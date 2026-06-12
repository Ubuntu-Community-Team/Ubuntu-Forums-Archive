---
title: "Wireless broadband modem [Huawei E122]"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by cpgos on 2010-09-19
I would appreciate some help in getting a Huawei E122 modem to work with Ubuntu 10.04.

I have tried the suggestions at [http://ubuntuforums.org/showthread.p...highlight=e620](http://ubuntuforums.org/showthread.p...highlight=e620) but have not been successful.

usb-modeswitch was installed with : sudo dpkg -i usb-modeswitch_1.1.4-1_i386.deb

and

usb-modeswitch-data was installed with : sudo dpkg -i usb-modeswitch-data_20100826-1_all.deb

When I enter lsusb the list below is displayed:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:0912 Hewlett-Packard Printing Support
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 059b:007a Iomega Corp.
Bus 001 Device 003: ID 12d1:1446 Huawei Technologies Co., Ltd.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The modem is visible only as a drive containing the required Windows software. There is a signal in the area but this is not detected by Network Manager and as a result it is not possible to make a connection with Ubuntu.

Any suggestions appreciated.

Best regards,
cpgos

---

### Post by stbcomp on 2010-09-24
> **cpgos said:**
> I would appreciate some help in getting a Huawei E122 modem to work with Ubuntu 10.04.

I have tried the suggestions at [http://ubuntuforums.org/showthread.p...highlight=e620](http://ubuntuforums.org/showthread.p...highlight=e620) but have not been successful.

usb-modeswitch was installed with : sudo dpkg -i usb-modeswitch_1.1.4-1_i386.deb

and

usb-modeswitch-data was installed with : sudo dpkg -i usb-modeswitch-data_20100826-1_all.deb

When I enter lsusb the list below is displayed:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:0912 Hewlett-Packard Printing Support
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 059b:007a Iomega Corp.
Bus 001 Device 003: ID 12d1:1446 Huawei Technologies Co., Ltd.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The modem is visible only as a drive containing the required Windows software. There is a signal in the area but this is not detected by Network Manager and as a result it is not possible to make a connection with Ubuntu.

Any suggestions appreciated.

Best regards,
cpgos

Hi
I battled with this as well, and I found that setting it up on my wifes XP machine and making a connection initializes the sim card. Don't know if that's right or not, but when I then connected it to my Ubuntu laptop, I had only to insert *99***# as the phone number and username for username and password for password, and it worked perfectly.
I had previously installed the usb-modeswitch utilities mentioned, and this may also have helped.
Sometimes damned fool luck can work nicely.

---

### Post by cpgos on 2010-09-27
Thank you for your response, I was starting to think that I may not get any. The situation is not resolved as yet but there has been some progress. 

I am using a dual boot PC, ie XP and Ubuntu 10.4; and I find that by first starting in XP and making an internet connection with the modem seems to cause it to be recognised when I restart into Ubuntu. If I start directly into Ubuntu the modem is not listed as a modem in response to lsusb. Unfortunately I am still not able to make a connection or find a way of making Ubuntu recognise the modem independently.

Best regards,
cpgos

---

### Post by cpgos on 2010-09-28
I have finally managed to make a connection, with the Huawei E122 modem from 3 Ireland, using the following settings:

phone number = *99#
username & password = both left blank
APN = 3internet
security settings = PAP, CHAP & MSCHAP

At present, it neccessary to firstly connect with Windows XP and then reboot into Ubuntu. Also, the files needed for use under Windows are still present on the Ubuntu desktop in a folder called 3Connect.

cpgos

---

### Post by cpgos on 2010-09-30
This problem has finally been solved by initially making an internet connection via XP, rebooting into Ubuntu and then downloading usb-modeswitch along with usb-modeswitch-data with Synaptic Package Manager.
The versions being 1.1.0-2 and 20100127-1 respectively.

A connection set up with Network Manager now works reliably.

cpgos

---

