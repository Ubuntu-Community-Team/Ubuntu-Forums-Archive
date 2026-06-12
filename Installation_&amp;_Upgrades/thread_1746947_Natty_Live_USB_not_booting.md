---
title: "Natty Live USB not booting"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by vikrang on 2011-05-02
I have downloaded i386 32 Bit ISO for Natty NArwhal..
 
Strangely , I am not able to use any tool to boot it thro USB..
 
I am getting the error below 
 
"initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs"
 
I have used 
 
1.Unetbootin 471
2.Multisystem USB (the french utility)
 
I already have Ubuntu 10.10 in my partition ...Can I create thro the startup Disk Creator?

---

### Post by An Sanct on 2011-05-02
The software might not be ready yet for this brand new release ...

PS. Natty has had problems with wubi also as far as I know... it might have problems with Live USB versions too. The CD version should work tho (I did not check...)

---

### Post by alexanda on 2011-05-02
I booted from USB using the ubuntu-11.04-desktop-i386.iso image earlier today, so I can vouch that it does work.

It seems slower than any previous live usb's that I have used, but I suspect that may be partially due to Unity.

A few suggestions:

- make sure you check the md5 sums of the .iso file to ensure that it didn't get corrupted on download, here is a link showing how to check:   [HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") 


- if possible boot into your copy of 10.10 and use the 'Startup Disk Creator' to create the bootable usb drive.  Use the tool to format the usb drive first (will result in all data on the usb drive being lost), and then give it a few gig of persistent storage (mine was set to 4 gig)

Best of luck

---

### Post by eks on 2011-05-02
Make sure you don't have U3 on your USB stick, drives with that are not working with Natty installs:

[http://ubuntuforums.org/showthread.php?t=1743527](http://ubuntuforums.org/showthread.php?t=1743527)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by vikrang on 2011-05-03
Thanks to all.. Got it running..
 
I got this problem resolved by downloading the ISO afresh and also installing LiLi latest version for WIN. Then the USB was able to boot...
 
One small doubt though , I guess the current ver has both GNOME and unity...In my desktop, the live USB started off with Unity ...Wheras in my comparitively lesser powered laptops it booted GNOME by default....
 
Has it got anything to do with RAM /Processor and stuff? maybe since my Desktop got 2GB RAM , it was able to run unity , wheras my laptops have only 1 G and 512MB so it starts off with GNOME?? Just a guess,,,

---

### Post by An Sanct on 2011-05-03
Unity starts by default if GPU (video) is strong enough. If it isn't, then Natty "*falls back*" to gnome.

---

### Post by vikrang on 2011-05-03
Oh...Ok!! Thanks ...
 
I think I will go in for GNOME 3 ...I read that it would break unity but anyway if its not going to start might as well break it!
 
I am going to add the PPA as described in some website and update to GNOME 3...
 
So I figure Unity is more resource hungry than even KDE , bcoz KDE works well in all my machines, though speed varies!
 
Also compared to Natty Unity , I find Oz Unity to be extremely beautiful and it is based on Ubuntu 10.10 with Unity Desktop,...This runs well I should say!
 
Those who are interested can visit [www.ultimateeditionoz.com]("http://www.ultimateeditionoz.com") ...

---

