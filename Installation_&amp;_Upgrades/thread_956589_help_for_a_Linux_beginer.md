---
title: "help for a Linux beginer"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by md08 on 2008-10-23
Hello everyone,
I'm new with Linux so please be patient with me.
Here is my first problem: i have no idea how to install AIM on my UBUNTU 8.04.
Second problem: my web cam dosen't work - i have a Acer TravelMate 5510
Third problem: can anyone tell me if it's possible to have an instant messeging client on Ubuntu that suports web cam and voice?

 I really need HELP!!!!

---

### Post by sethvath on 2008-10-23
Hi and welcome to ubuntu. Pidgin replaces aim on ubuntu, you can find it under Applications > Internet > Pidgin Internet Messenger. 

Web cam and voice does not work out of the box unfortunately, are you able to verify what are the system specs for your laptop?

In terminal type the following:
lspci

---

### Post by micdhack on 2008-10-23
About the first thing you can go to add remove programs from application menu(that is on your top left) and install pidgin which is a multi-chat program. I personally use it for icq, and msn but also has aim support. Now if you want aim and only aim then you can install first wine
```
sudo apt-get install wine
```
And then download a version of aim that is working with wine.
You can see this from here:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=109](http://appdb.winehq.org/objectManager.php?sClass=application&iId=109)

About your second problem. Im not sure what happens with on board cameras(but i will soon find out cause i order an Acer aspire with camera). First thing that i believe you should do is
```
lspci
``` and find your camera specifics.
After this you should go to [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) and see if the camera is supported.
if its supported then theoritically its a piece of cake:
[https://help.ubuntu.com/community/Spca5xx#Ubuntu%207.10%20(Gutsy),%20and%208.04%20(Hardy](https://help.ubuntu.com/community/Spca5xx#Ubuntu%207.10%20(Gutsy),%20and%208.04%20(Hardy))
The first thing searches the list of the loaded modules for the specific module which is the driver for the camera. The second loads the module for the camera.
Now if all goes well with camorama you can test it.
Btw modprobe temporarily loads modules into memory...you will need to use insmod to install it permenatly but i suggest you first check if its working and then continue.

Last about your third question i dont know about aim but i manages to use my usb trust webcamera with amsn which is an msn client for linux

---

### Post by md08 on 2008-10-23
Thanks both of you guys,

This is what i've got after i typed lspci in the terminal:


00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

I dont see any info about my web cam, wich is integrated, but i can tell u that in Windows i've found it as ACER ORBICAM.

---

### Post by micdhack on 2008-10-24
well the only orbicam i see is from logitech there but you can try to 

```
sudo modprobe gspca
```

and then use camorama...in case you dont have it installed

```
sudo apt-get install camorama
```

Its better to run it through console so you can see what kind of errors your getting.
I read on one site that acer's orbicam is rebranded logitech model so maybe they use same chipset thus same drivers could work.

---

### Post by Ayuthia on 2008-10-24
> **md08 said:**
> Thanks both of you guys,

This is what i've got after i typed lspci in the terminal:


00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

I dont see any info about my web cam, wich is integrated, but i can tell u that in Windows i've found it as ACER ORBICAM.

There is a good chance that it is being recognized as a USB device.  Can you post your lsusb results?

---

### Post by micdhack on 2008-10-25
well since know i have also a laptop with acer onboard webcam i can support too in order to find a solution.
Since on my system i already had a usb web camera and move my files to the new computer with remastersys im not sure what came out of the box and what is working because of my tweaking.

I think we forgot to check the most important thing first:
```
ls /dev/video0 -la
```
If this device file exists then this means that linux recognises the web camera.
This happened to me.
By using xawtv my camera worked perfectly. Camorama on the other hand returned could not connect to /dev/video0. Its certainly no permissions thing cause i also runned it with sudo.
So it makes me wonder which device file the xawtv uses..

Here is my lsusb. pawnest is my usb mouse..the rest is intergrated parts.
> Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 064e:a103 Suyin Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ac7:0130 Panwest Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

064e:a103 Suyin Corp. This is the device..

---

