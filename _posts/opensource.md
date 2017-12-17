---
layout: post
cover: 'assets/images/tree.jpg'
title: 2017년 1학년 2학기 오픈소스 실습: 뮤직 플레이어 떼고 "DDEGO"
date: 2017-12-17 12:00:00
tags: ddego, opensource, hanyang
author: Jason Koo
---

# 개요
대학교에 들어와서 처음 접한 PBL이라는 수업이 있었습니다. 이는 Problem-Based Learning의 줄임말로, 어떤 주제에 대해 학생이 직접 문제를 해결해가면서 배우는 방식의 수업이었습니다. 일정한 과정만을 따라가며 그대로 따라하는 방식에 익숙해져 있는 저는 이러한 수업 방식이 생소하게 느껴졌습니다.

# 첫 번째 목표: 중간 시연
1학년 2학기에 수강하게 된 오픈소스라는 PBL 강의에서는, 매장에서 음원을 재생할 때 사용하는 최소기능제품 개발 프로젝트를 맡게 되었습니다.
먼저 처음 프로젝트에서 주어진 목표는 다음과 같았습니다.

> 당신은 대형 음악서비스 포털인 ㈜KT 뮤직의 전략기획실 신기술개발팀장이다. 최근 대법원 판결(2013 다 219616)에 따라 디지털 음원을 매장에서 재생할 때, 공연보상금을 징수하는 기준이 3,000m2 이상에서 모든 면적으로 확대되었다. 이에 따라 본사는 기존 매장음원서비스인 “샵엔지니” 서비스를 확장하여 보다 다양한 시장을 확보하고자 2017 년 9 월 6 일 전략기획회의를 진행하였다. 회의 결과 별도의 음악 재생용 PC 마련이 곤란한 소형 점포를 위해 저렴한 독립형 뮤직 셋톱박스(standalone music set-top box)를 제공하는 “플러그엔 지니” 서비스를 새롭게 기획하기로 하였다. 이에 신규 서비스의 가능성 타진을 위해 신기술개발팀에서는 오픈소스 SW 와 Raspberry Pi 나 비글본 같은 간단한 오픈소스개발보드를 활용하여 최소기능제품(MVP, Minimum Viable Product)을 개발하기로 하였다. 당신의 팀은 9 월 27 일까지 독립형 뮤직 셋톱박스에 대한 MVP 를 개발하여 시연해야 한다.
> MVP 는 오픈소스에 기반한 간단한 네트워크 스토리지 서버와 뮤직 플레이어 클라이언트로 구성된다. 클라이언트는 마지막 재생채널을 기억하고 있다가 전원 연결(플러그인) 시 자동으로 유/무선의 네트워크상에서 서버의 해당채널 음원을 스트리밍하여 3.5mm 오디오 단자로 출력하는 기본 기능을 지원해야 한다. 또한, 현재 재생 중인 채널 및 곡에 대한 간단한 정보를 LED 혹은 LCD 디스플레이 상에 표시하여야 하며, 채널전환 버튼을 통해 손쉽게 음악채널들을 전환할 수 있어야 한다.

따라서 저희 팀은 라즈베리파이에 운영체제를 설치한 뒤, 기본적인 LCD 디스플레이와 브레드보드를 연결하고
파이 안에 설치되어 있는 파이썬 언어로 필요로 하는 기능들을 구현하고자 했습니다.

그리고 중간 시연까지 위에 설명되어 있는 기능들 중 아주 기본적인 기능이 수행 가능한 Minimal Viable Product를 제작하였습니다.

* [중간시연까지 구현한 기능의 동영상](https://youtu.be/gOvtueTeT9M)은 여기서 확인 가능합니다.

<amp-youtube width="1280"
  height="720"
  layout="responsive"
  data-videoid="gOvtueTeT9M">
</amp-youtube>

# 두 번째 목표: 최종 시연

중간 시연까지는 시간이 부족한 관계로 미흡한 부분이 많았으며 최종 시연까지 이 점들을 보완하기 위해 많은 시간을 투자했습니다.
최종 시연의 목표는 다음과 같았습니다.

> 성공적인 시연 결과, 당신의 팀이 만든 솔루션을 활용하여 본격적인 신규 매장음원서비스를 기획하기로 결정되었으며, 당신을 본부장급 권한을 가진 “플러그엔 지니” 태스크 포스 리더로 임명하여, 신규 사 업 승인을 위한 최종 데모를 11월 15일 임원회의에서 진행하기로 하였다. 이에 기획팀, 설계팀 및 디자인팀을 이끌고, 나선형 모델 (spiral model)에 입각하여 요구사항 명세서, 설계 명세서 등의 적절 한 산출물과 함께 구체적인 서비스 기획 및 설계를 진행한 후, 이 시 스템에 사용될 케이스와 주변기기에 대한 적절한 디자인을 개발, 3D 프린터로 rapid prototype를 제작하여 성공적인 신제품 데모를 수행하라.

이에 저희 팀은 중간 시연까지 구현하지 못했던 기능적인 부분을 코드로 보완하기로 했고,
본격적으로 외관에 신경쓰기 위해 Rhino 및 3D 프린터를 이용하는 법을 배웠습니다.

## 외관 부분

### 제품 프로토타입 디자인

저희 팀은 "레고"를 컨셉으로 제품을 디자인하기로 하였습니다. 하지만 단순히 모양만 레고일 뿐만 아니라, 떼었다 붙였다 할 수 있는 레고의 특징을 최대한 이용하는 방식으로 디자인을 하고자 하였습니다.
따라서 사용자에 입맛에 따라 "모듈"을 추가할 수 있도록 하여 원하는 대로 기기를 배치 및 조립할 수 있도록 했고, 매장에서 사용할 수 있는 "모듈"에는 어떤 것들이 있는지 고민하다 명함꽂이, 펜꽂이 등을 모듈로 만들고자 하였습니다.
제품의 이름은 "레고" + "떼었다 붙였다 할 수 있다는 점"을 결합해서 떼고(ddego)라고 결정하였습니다.

![프로토3](https://github.com/retrowavve/retrowavve.github.io/blob/master/assets/images/ddegoproto3.jpeg)
![프로토1](https://github.com/retrowavve/retrowavve.github.io/blob/master/assets/images/ddegoproto1.jpeg)

소규모 매장에서 카운터 옆에 두고 사용할 수 있고, 조작이 편리하도록 초기 프로토타입을 디자인 하는 모습입니다.

![프로토2](https://github.com/retrowavve/retrowavve.github.io/blob/master/assets/images/ddegoproto2.jpeg)
![프로토4](https://github.com/retrowavve/retrowavve.github.io/blob/master/assets/images/ddegoproto4.jpeg)

PCB 보드에 연결할 선을 회로도로 나타낸 모습입니다.
저희 팀은 기본으로 주어진 부피를 많이 차지하는 브레드보드 대신 "PCB 보드"를 사용하여 부피와 무게를 획기적으로 줄였습니다.

### 라이노 및 3D 프린팅

사용자가 서서 조작하기 편리하도록 화면과 조작부가 위를 향해 있는 수평형 설계를 했습니다.
ABS와 PLA 재질을 사용하여 인쇄했으며, 밀도를 증가시켜서 견고하게 인쇄하였습니다.

### 사용된 라이노 및 3D 프린팅 자료


### 제품 최종 완성본

![떼고프로토타입1](https://github.com/retrowavve/retrowavve.github.io/blob/master/assets/images/ddegoreal.jpeg)
3D 프린팅을 마친 뒤, 케이스 부분과 라즈베리파이 본체를 결합한 직후의 모습입니다. 순간접착제로 붙인 뒤, 내부는 전기가 통하지 않은 고무찰흙과 지점토를 이용해서 고정하였습니다.

![떼고프로토타입2](https://github.com/retrowavve/retrowavve.github.io/blob/master/assets/images/ddegoreal2.jpeg)
최종적으로 완성된 떼고와 떼고의 구성품입니다. 레고 모양의 판, 본체, 그리고 "모듈"인 명함꽂이, 펜꽂이 등이 있습니다.
좀더 직관적인 버튼 작동을 위해 버튼에 화살표 모양의 스티커를 부착했습니다.

![떼고프로토타입3](https://github.com/retrowavve/retrowavve.github.io/blob/master/assets/images/ddegoreal3.jpeg)
사진과 같이 떼고 본체 밑부분에는 결합부가 달려 있어서 레고 모양의 판과 결합이 가능합니다.

![떼고프로토타입4](https://github.com/retrowavve/retrowavve.github.io/blob/master/assets/images/ddegoreal4.jpeg)
몇 가지 모듈과 결합한 후의 떼고의 모습입니다.

![떼고로고프로토타입](https://github.com/retrowavve/retrowavve.github.io/blob/master/assets/images/ddegoreal5.jpeg)
이 부분은 떼고가 카운터에 놓여졌을 때 점장의 시점입니다. 조작이 편리하도록 떼고 본체를 가깝게 배치하였습니다.

![떼고로고프로토타입](https://github.com/retrowavve/retrowavve.github.io/blob/master/assets/images/ddegoreal6.jpeg)
이 부분은 고객 입장에서 떼고를 볼 때의 시점입니다. 명함을 가져갈 수 있도록 명함꽂이를 맨 앞에 끼워넣은 모습입니다.



### 로고 디자인

#### 로고 초기 디자인

![떼고로고프로토타입](https://github.com/retrowavve/retrowavve.github.io/blob/master/assets/images/ddegologoproto.jpeg)

#### 로고 최종 완성본

![떼고로고](https://github.com/retrowavve/retrowavve.github.io/blob/master/assets/images/ddegologo.png)

떼었다 붙였다 할 수 있는 제품의 특징을 반영하여 알파벳 밑에는 레고 판을 넣었으며, 첫 알파벳 d가 떼어져 있는 모습을 디자인하였습니다.



## 기능 부분

중간 시연까지 구현한 기능은 이전곡, 다음곡, 재생, 정지 기능이 있었습니다.
요구사항에서 구현하지 못한 기능들은 채널 구현, 서버 구축을 통한 음악 재생, 마지막 재생채널 기억 등이 있었습니다.
이 부분은 모두 최종 시연까지 구현하는 데에 성공하였습니다.
서버 구축은 OpenMediaVault를 사용하였습니다.

### * 최종 시연에 사용된 Python 코드 자료 및 설명

```python

#!/usr/bin/python
#--------------------------------------
#    ___  ___  _ ____
#   / _ \/ _ \(_) __/__  __ __
#  / , _/ ___/ /\ \/ _ \/ // /
# /_/|_/_/  /_/___/ .__/\_, /
#                /_/   /___/
#
#  lcd_i2c.py
#  LCD test script using I2C backpack.
#  Supports 16x2 and 20x4 screens.
#
# Author : Matt Hawkins
# Date   : 20/09/2015
#
# http://www.raspberrypi-spy.co.uk/
#
# Copyright 2015 Matt Hawkins
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
#--------------------------------------
#!/usr/bin/env python

import ftplib
import smbus
import time
import vlc
import RPi.GPIO as GPIO
import os

#button settings
GPIO.setmode(GPIO.BCM)
GPIO.setup(17, GPIO.IN) #stop
GPIO.setup(18, GPIO.IN) #play, pause
GPIO.setup(19, GPIO.IN) #previous song
GPIO.setup(20, GPIO.IN) #next song
GPIO.setup(21, GPIO.IN) #channel down
GPIO.setup(22, GPIO.IN) #channel up
// 기기 작동에 사용될 버튼을 설정해주는 곳 입니다.



# Define some device parameters
I2C_ADDR  = 0x27 # I2C device address
LCD_WIDTH = 16   # Maximum characters per line

# Define some device constants
LCD_CHR = 1 # Mode - Sending data
LCD_CMD = 0 # Mode - Sending command

LCD_LINE_1 = 0x80 # LCD RAM address for the 1st line
LCD_LINE_2 = 0xC0 # LCD RAM address for the 2nd line
LCD_LINE_3 = 0x94 # LCD RAM address for the 3rd line
LCD_LINE_4 = 0xD4 # LCD RAM address for the 4th line

LCD_BACKLIGHT  = 0x08  # On
#LCD_BACKLIGHT = 0x00  # Off

ENABLE = 0b00000100 # Enable bit

# Timing constants
E_PULSE = 0.0005
E_DELAY = 0.0005

#Open I2C interface
#bus = smbus.SMBus(0)  # Rev 1 Pi uses 0
bus = smbus.SMBus(1) # Rev 2 Pi uses 1

def lcd_init():
  # Initialise display
  lcd_byte(0x33,LCD_CMD) # 110011 Initialise
  lcd_byte(0x32,LCD_CMD) # 110010 Initialise
  lcd_byte(0x06,LCD_CMD) # 000110 Cursor move direction
  lcd_byte(0x0C,LCD_CMD) # 001100 Display On,Cursor Off, Blink Off 
  lcd_byte(0x28,LCD_CMD) # 101000 Data length, number of lines, font size
  lcd_byte(0x01,LCD_CMD) # 000001 Clear display
  time.sleep(E_DELAY)

def lcd_byte(bits, mode):
  # Send byte to data pins
  # bits = the data
  # mode = 1 for data
  #        0 for command

  bits_high = mode | (bits & 0xF0) | LCD_BACKLIGHT
  bits_low = mode | ((bits<<4) & 0xF0) | LCD_BACKLIGHT

  # High bits
  bus.write_byte(I2C_ADDR, bits_high)
  lcd_toggle_enable(bits_high)

  # Low bits
  bus.write_byte(I2C_ADDR, bits_low)
  lcd_toggle_enable(bits_low)

def lcd_toggle_enable(bits):
  # Toggle enable
  time.sleep(E_DELAY)
  bus.write_byte(I2C_ADDR, (bits | ENABLE))
  time.sleep(E_PULSE)
  bus.write_byte(I2C_ADDR,(bits & ~ENABLE))
  time.sleep(E_DELAY)

def lcd_string(message,line):
  # Send string to display

  message = message.ljust(LCD_WIDTH," ")

  lcd_byte(line, LCD_CMD)

  for i in range(LCD_WIDTH):
    lcd_byte(ord(message[i]),LCD_CHR)

// LCD 출력 관련 부분 코드입니다.
  

def main():

  path = ["/home/pi/Music/classic/", "/home/pi/Music/kpop/", "/home/pi/Music/pop/"]
   
  j = 0
  root = ftplib.FTP('192.168.0.77','root','openmediavault')
  
  root.cwd('/number1/classics/')  
  list1 = root.nlst()
  while j<len(list1):
    if not os.path.isfile("/home/pi/Music/classic/"+list1[j]):
      fd = open("/home/pi/Music/classic/"+list1[j], 'wb')
      root.retrbinary("RETR /number1/classics/"+list1[j], fd.write)
      fd.close()
    j+=1
  j=0
  
  root.cwd('/number1/korean/')
  list2 = root.nlst()
  while j<len(list2):
    if not os.path.isfile("/home/pi/Music/kpop/"+list2[j]):
      fd = open("/home/pi/Music/kpop/"+list2[j], 'wb')
      root.retrbinary("RETR /number1/korean/"+list2[j], fd.write)
      fd.close()
    j+=1
  j=0
  
  root.cwd('/number1/pop/')
  list3 = root.nlst()
  while j<len(list3):
    if not os.path.isfile("/home/pi/Music/pop/"+list3[j]):
      fd = open("/home/pi/Music/pop/"+list3[j], 'wb')
      root.retrbinary("RETR /number1/pop/"+list3[j], fd.write)
      fd.close()
    j+=1
  j=0

  lcd_init()
  
  path = ["/home/pi/Music/classic/", "/home/pi/Music/kpop/", "/home/pi/Music/pop/"]
  #path = ["ftp://192.168.0.77/number1/classics/", "ftp://192.168.0.77/number1/korean/", "ftp://192.168.0.77/number1/pop/"]
  #a = os.listdir(path)
  
  
// 서버에서 스트리밍 하는 방식으로 코드 작성시 인터넷 연결이 불안정할 경우 음악이 자주 끊기는 현상이 발생했습니다.
// 따라서 저희 팀은 전원 실행시 서버에서 음원을 다운로드를 받아 로컬에 저장한 뒤 재생하는 방식을 채택했습니다.
// 이 때 이미 받아져 있는 음원은 파일명으로 구분하여 받지 않는 방식으로 다운로드 시간을 줄였습니다.


  loader1 = open("/home/pi/channel.txt", 'r')
  i = str(loader1.readline())
  loader1.close()
  print(i)
  i = int((float(i)))
  
  loader2 = open("/home/pi/channel2.txt", 'r')
  channel = str(loader2.readline())
  loader2.close()
  print(channel)
  channel = int((float(channel)))
  
// 마지막 재생채널 / 재생곡을 기억하기 위해 종료시 정보를 텍스트 파일에 기록하도록 하였습니다.
// 재부팅시 텍스트 파일에 저장된 채널 및 곡 정보를 불러오도록 하였습니다.

  
  
  file = (path[i]+os.listdir(path[i])[channel])
  instance = vlc.Instance()
  player=instance.media_player_new()
  media=instance.media_new(file)
  player.set_media(media)
  player.play()
  time.sleep(1)
  count = player.get_state()
  
// 처음 실행이 되고 경로를 받아와서 제품에서 노래가 재생되는 부분입니다.

  while True:
    count = player.get_state()
    if count == 6:
      channel += 1                                                   
      file = (path[i]+os.listdir(path[i])[channel])
      instance = vlc.Instance()
      player= instance.media_player_new()
      media = instance.media_new(file)
      player.set_media(media)
      
      player.play()
      time.sleep(1)

    if GPIO.input(17)==0:
        count=player.get_state()

        f1 = open("/home/pi/channel.txt", 'w')
        data1 = i
        hhh = str(data1)
        print(data1)
        f1.write(hhh)
        print(data1)
        f1.close()


        f2 = open("/home/pi/channel2.txt", 'w')
        data2 = channel
        hhh2 = str(channel)
        f2.write(hhh2)
        f2.close()
        
        player.stop()
        count=player.get_state()
        time.sleep(1)

    elif GPIO.input(18)==0:
        player.pause()
        count=player.get_state()
        time.sleep(1)
        
    if GPIO.input(19)==0: #track before
      if channel == 0:
        channel = len(os.listdir(path[i]))
      player.stop()
      channel -= 1
      file = (path[i]+os.listdir(path[i])[channel])
      instance = vlc.Instance()
      player= instance.media_player_new()
      media = instance.media_new(file)
      player.set_media(media)
      player.play()
      time.sleep(1)
      
      
    if GPIO.input(20)==0: #track after
      if channel == len(os.listdir(path[i]))-1:
        channel = -1
      player.stop()
      channel += 1
      file = (path[i]+os.listdir(path[i])[channel])
      instance = vlc.Instance()
      player= instance.media_player_new()
      media = instance.media_new(file)
      player.set_media(media)
      player.play()
      time.sleep(1)
      
          
      player.get_state()

    if GPIO.input(21)==0: #channel down
      if i == 0:
        i = 3
      player.stop()
      i -= 1
      channel = 0
      file = (path[i]+os.listdir(path[i])[channel])
      instance = vlc.Instance()
      player= instance.media_player_new()
      media = instance.media_new(file)
      player.set_media(media)
      player.play()
      time.sleep(1)

    if GPIO.input(22)==0: #channel up
      if i == 2:
        i = -1
      player.stop()
      i += 1
      channel = 0
      file = (path[i]+os.listdir(path[i])[channel])
      instance = vlc.Instance()
      player= instance.media_player_new()
      media = instance.media_new(file)
      player.set_media(media)
      player.play()
      time.sleep(1)
      
// 재생 및 일시정지, 종료, 이전/다음곡, 이전/다음 채널 버튼을 구현한 부분입니다.


    if i == 0 or i == -3:
      if channel == 0 or channel == -4:
        lcd_string("Prokofiev      ",LCD_LINE_1)
        lcd_string("Romeo & Juliet ", LCD_LINE_2)
      if channel == 1 or channel == -3:
        lcd_string("Khachaturian   ",LCD_LINE_1)
        lcd_string("Masquerade     ", LCD_LINE_2)
      if channel == 2 or channel == -2:
        lcd_string("Khachaturian   ",LCD_LINE_1)
        lcd_string("Spartacus      ", LCD_LINE_2)
      if channel == 3 or channel == -1:
        lcd_string("Rachmaninoff   ",LCD_LINE_1)
        lcd_string("Rhapsody       ", LCD_LINE_2)
        
    if i == 1 or i == -2:
      if channel == 0 or channel == -4:
        lcd_string("Psy            ",LCD_LINE_1)
        lcd_string("New Face       ", LCD_LINE_2)
      if channel == 1 or channel == -3:
        lcd_string("Zico           ",LCD_LINE_1)
        lcd_string("She's a Baby   ", LCD_LINE_2)
        
      if channel == 2 or channel == -2:
        lcd_string("Sunmi          ",LCD_LINE_1)
        lcd_string("Gasina         ", LCD_LINE_2)
      if channel == 3 or channel == -1:
        lcd_string("Zico           ",LCD_LINE_1)
        lcd_string("Boys and Girls ", LCD_LINE_2)
        
    if i == 2 or i == -1:
      if channel == 0 or channel == -4:
        lcd_string("Little Mix     ",LCD_LINE_1)
        lcd_string("Shoutout to My Ex", LCD_LINE_2)
      if channel == 1 or channel == -3:
        lcd_string("Bruno Mars     ",LCD_LINE_1)
        lcd_string("24K Magic      ", LCD_LINE_2)
      if channel == 2 or channel == -2:
        lcd_string("Maroon 5       ",LCD_LINE_1)
        lcd_string("Don't Wanna know", LCD_LINE_2)
      if channel == 3 or channel == -1:
        lcd_string("Zara Larsson   ",LCD_LINE_1)
        lcd_string("Not My Fault   ", LCD_LINE_2)

// LCD화면에 표시되는 곡 정보를 표시한 부분입니다.

if __name__ == '__main__':

  try:
    main()
  except KeyboardInterrupt:
    pass
  finally:
    lcd_byte(0x01, LCD_CMD)

```


### 최종 시연 동영상
https://youtu.be/sGXLG-uNgV4
<amp-youtube width="1280"
  height="720"
  layout="responsive"
  data-videoid="sGXLG-uNgV4">
</amp-youtube>

### 최종 시연에 사용된 PPT 발표 자료
