---
title: "Visual Glitching, can't install Ubuntu"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by larrysellers on 2013-01-06
Hello everyone.  This is my first thread.  Although I've installed and used Ubuntu successfully on systems before, I'm still a noob.  Here's the deal...

I recently built a laptop by combining two identical HP laptops which had various problems.  These laptops were purchased in 2007 and wasting away in a closet and had not been used in about 2 years.  One hard drive was virus ridden and got wiped to use as an external storage device.  The other has Vista installed, which works but it's very slow.  

We're planning to give this laptop to my grandfather to use solely to check his stocks online at the local public library.  I thought Linux would be perfect for this primarily because of the speedy boot times and security it provides.

Unfortunately, I am unable to install Linux on this computer.  Whenever I try, the screen glitches horribly and freezes.  It looks like one of those Magic Eye pictures where you relax your eyes and a 3D image pops out.  This visual glitching always happens when I'm asked to choose the time zone or the username and password for the system.  I've tried to install at least six times now and it happens every time.

This has happened with Ubuntu 12.10 using both a DVD and USB to try to install, as well as 12.04 LTS via USB.  
Here are the specs for the computer:

HP dv2415nr (purchased appx 2007)
AMD Turion 64 x2 processor
nVidia Geforce 6150 video card
1G RAM (2 512 RAM sticks)
Currently (slowly) running Vista Service Pack 2 (takes a couple minutes to boot up and freezes up occasionally.  I've recently defragged and run Ccleaner but it's still slow and it's still Vista).

I would like to know if it's a problem with my particular hardware or the particular versions of Ubuntu I'm trying to install.  I've read online that it may be both.

I'm considering trying to install a previous version of Ubuntu, (11.10 perhaps) because I had this problem on a different HP laptop when I tried to install 12.10 on it. I was able to install 12.04 on that laptop.  I don't know how I got that one to work.

Thanks in advance for any suggestions.

---

### Post by darkod on 2013-01-06
I would keep trying with 12.04 because it's LTS and supported longer.

With nvidia usually you need to boot with nomodeset to live mode. As soon as you see the first purple screen, hit Esc to get the old style main menu. Hit F6 for Advanced options and select nomodeset. Then Try Ubuntu from the main menu.

If that loads the live mode successfully, it should be OK after you install but you will still have to add nomodeset to the boot line first time you reboot so that it can boot the newly installed ubuntu and allow you to activate the video driver.

More details here, note that you don't always need to do all of it:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by larrysellers on 2013-01-06
> **darkod said:**
>  As soon as you see the first purple screen, hit Esc to get the old style main menu. Hit F6 for Advanced options and select nomodeset. Then Try Ubuntu from the main menu.



Thanks. I'll give it a try.  When you say the first purple screen, do you mean the one with the word "ubuntu" and the little progress dots underneath it?

---

### Post by darkod on 2013-01-06
No, when booting from the cd/usb I think there is one even before that one. It has like a little person and keyboard icons at the bottom part. As soon as you see purple, hit Esc if you want to get the old style main menu with advanced options.

---

### Post by larrysellers on 2013-01-06
Thanks!

---

