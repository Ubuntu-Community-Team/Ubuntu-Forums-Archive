---
title: "Brand new ubuntu user - problems installing 'Wine'"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by wogboy711 on 2011-04-10
Hey,
I just switched to Ubuntu today and am trying to install my wireless internet adapter (Netgear WNDA 3100v2). I have just managed to install the Windows Wireless Driver Ndiswrapper, after much trouble. And now I need to install Wine so that I can install my Netgear's driver from its driver cd (after reading this thread [http://ubuntuforums.org/showthread.php?t=1383708](http://ubuntuforums.org/showthread.php?t=1383708))
When I try to install wine from the software center it tells me "Sorry, wine is not available for this type of computer (i386).
After reading numerous other threads about similar problems, I have come to this endless loop where I am told that I need to have an internet connection to update/install/download the wine software from the internet. But my whole problem is that I am trying to get my wireless internet adapter to work in the first place.

I am a brand new linux user as of today, so any help would be greatly appreciated.

---

### Post by linuxuser12345 on 2011-04-10
Try installing PlayonLinux from the software center. It uses Wine as a backend and might possibly bypass what your computer originally told you. But, you don't need Wine to look through the driver CD. All you do is open it, and search for the .inf file in the Drivers section.

---

### Post by lkraemer on 2011-04-10
wogboy711,
Before you jump through all those hoops........

1.  What version of Ubuntu?
2.  32 Bit or 64 Bit?
3.  Wifi Card USB/PCI/???
4.  Laptop or Desktop?
5.  Windows Drivers 32 Bit or 64 Bit? --They need to match Ubuntu's 32 Bit or 64 Bit.

Typically, one tries all the functionality with the LiveCD, and most times
everything works, with the exception of some Wifi, off brand Scanners & Printers.  

May I suggest you do the following?

Open a Terminal Window (Console) and do:  (Copy & Paste to prevent errors)
```

lspci > junk.txt
echo ------------------------------------- >> junk.txt
lsusb >> junk.txt
echo ------------------------------------- >> junk.txt
dmesg | tail
echo ------------------------------------- >> junk.txt

```
Your device should be detected.......................

This will return a Manufactuer & Product Number, so use it to get more information.... example.....0a5c:2101...)
```

Bus 008 Device 003: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Then do:
```

lsusb -v -d 0a5c:2101 >> junk.txt
echo ------------------------------------- >> junk.txt

```
You may also want to include:
```

lshw -C network >> junk.txt
echo ------------------------------------- >> junk.txt
lsmod >> junk.txt
echo ------------------------------------- >> junk.txt
ndiswrapper -l >> junk.txt
echo ------------------------------------- >> junk.txt
cat /etc/modprobe.d/blacklist.conf >>junk.txt
echo ------------------------------------- >> junk.txt
iwconfig >> junk.txt

```
Then post junk.txt along with answers to the questions.


lk

---

