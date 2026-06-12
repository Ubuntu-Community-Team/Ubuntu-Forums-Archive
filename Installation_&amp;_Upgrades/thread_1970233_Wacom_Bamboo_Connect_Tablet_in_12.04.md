---
title: "Wacom Bamboo Connect Tablet in 12.04"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by MoonLitOwl on 2012-04-30
So, I've no idea how to go about getting my Wacom Bamboo Connect Tablet to work in 12.04. I was told that it should work (did not bother with it in 11.10, was still using Windows 7) , but even after putting in the cd, I get an error when the Archieve tries to read it, and it also doesn't work without the cd either.

Is there something I'm supposed to do/download first? I've been having a hard time finding any info on it. I can't seem to find anything on it on this forum either. =(

And if it makes any difference, my laptop is a HP Pavilion dm1, running on just Ubuntu 12.04.

---

### Post by Favux on 2012-05-01
Hi MoonLitOwl,

I doubt the Bamboo Connect install CD has linux drivers.

Wacom usb tablets need two Wacom drivers.  The Wacom usb kernel driver/module.  And the Wacom X driver.  The kernel driver sends usb info. to the X driver which then draws the stuff on your monitor.

The default Wacom X driver that comes with Precise (12.04) works fine with the Connect.  So you are good there.  The problem is the kernel driver which is called wacom.ko.  The wacom.ko that supports the Connect was accepted into the 3.3 kernel and Precise has the 3.2 kernel.  So Precise's kernel is too old to support your tablet.

However one of the Linux Wacom Project developers (Chris) has backported that 3.3 kernel support to input-wacom.  Input-wacom is how you get Wacom tablets working on older kernels that do not support them.  It is a package that will give you an updated wacom.ko that will work with your Connect.

I don't think anyone has made an input-wacom PPA for Precise you could use yet so you will need to compile it.  Step by step instructions are on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Just follow part I. for input-wacom-0.13.0 and you should be good to go.

---

### Post by MoonLitOwl on 2012-05-01
> **Favux said:**
> Hi MoonLitOwl,

I doubt the Bamboo Connect install CD has linux drivers.

Wacom usb tablets need two Wacom drivers.  The Wacom usb kernel driver/module.  And the Wacom X driver.  The kernel driver sends usb info. to the X driver which then draws the stuff on your monitor.

The default Wacom X driver that comes with Precise (12.04) works fine with the Connect.  So you are good there.  The problem is the kernel driver which is called wacom.ko.  The wacom.ko that supports the Connect was accepted into the 3.3 kernel and Precise has the 3.2 kernel.  So Precise's kernel is too old to support your tablet.

However one of the Linux Wacom Project developers (Chris) has backported that 3.3 kernel support to input-wacom.  Input-wacom is how you get Wacom tablets working on older kernels that do not support them.  It is a package that will give you an updated wacom.ko that will work with your Connect.

I don't think anyone has made an input-wacom PPA for Precise you could use yet so you will need to compile it.  Step by step instructions are on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Just follow part I. for input-wacom-0.13.0 and you should be good to go.

Hello and thanks for the reply!

I instead followed the instructions found here: [http://ubuntuforums.org/showthread.php?t=1951073](http://ubuntuforums.org/showthread.php?t=1951073)

And they it worked! My bamboo connect works now. ^^

---

### Post by Favux on 2012-05-01
Good.  I'm glad you got your Wacom tablet working.  I forgot Lekensteyn added Precise to his input-wacom-0.12.1 PPA.

---

