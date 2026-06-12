---
title: "Issues with Usb ModeSwitch"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by Balvinder25 on 2011-07-10
I have ubuntu lucid 10.04 and im facing issues with a USB Modem that i have.The problem is that it takes awful lot of time for ubuntu to recognize the usb device as a modem, and i have to play around by enable/disabling the network connection, or removing and plugging the device back on again and then it eventually works.

The version of usb mode switch that i have is usb-modeswitch_1.0.2-1_i386.deb. 

Now my question is are there any later versions to this and is there any sort of PPA available for the same.

lsusb shows the below :

balvinder@balvinder-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 19d2:fff1 ONDA Communication S.p.A. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0b38:0003 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


any help would be much appreciated.

Thanks all.
__________________
Thanks 
Balvinder

---

### Post by foresthill on 2011-07-10
What's your definition of "an awful lot of time"?

I have used USB modeswitch on several computers, and it might take 30 seconds, and sometimes as long as a minute to recognize the modem, especially on slower systems. 

So if that's how long it's taking, I would say that's normal. Even in Windows, with the modem software installed, it still takes about this same amount of time for the modem to "flip" and be recognized,

---

### Post by Balvinder25 on 2011-07-11
hmmm , by awful lot of time i meant atleast 3 to 4 mins at times, but dont worry about i got the issue sorted, there was a deb package in the USB modem that gave me the same interface that i got in windows so its all fine now.

Thanks for the response btw.

Tc...

---

