---
title: "Kernel won't load with out separate usb device mounted"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by Shway on 2011-01-03
Hello all, I'm fairly new to linux I've come across a problem I can't quite trouble shoot on my own. 

I have windows installed on my pc and Ubuntu 10.04 installed on an external hard drive which is connected to my PC via usb. When I start up my PC I select my Ubuntu OS system then get to GRUB where I can select which kernal I want to boot. If I have another USB device mounted (as well as the external hard drive) before I select a version it'll boot up fine. However, if I don't; once I select my most recent version I am given a black screen for a while and presented with a message that reads "Gave up waiting for device...." followed by some common problems and then "ALERT! /dev/sdc1 does not exist dropping to built in shell." and I'm in the busy box.

Seeing as how the usb device doesn't really matter (booting worked with a pen drive or my phone mounted), and once ubuntu has started I can remove the device with out causing errors, I don't see how it could possibly be that the header is installed on a different device. 

I don't have any real idea on what the problem could be and searches have yielded no solutions. If there's any more information that would be useful let me know and how to get it.

if it helps at all:
-using kernel 2.6.32-27-generic
-kernel root is set to hd2,1
-devices I have plugged in to usb when it doesn't work are: keyboard, mouse, wifi adapter, HD w/Linux.

thanks for any help in advance!

---

