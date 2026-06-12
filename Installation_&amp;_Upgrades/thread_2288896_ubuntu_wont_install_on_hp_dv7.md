---
title: "ubuntu wont install on hp dv7"
date: 2015-07-30
forum: Installation &amp; Upgrades
---

### Post by charlie32 on 2015-07-30
hey i have a hp dv7, originally came with vista then upgraded to windows 7, 7 crashed so tried to factory reset to vista, and that crashed, so said screw it and am trying to install ubuntu on it, problem is no mater what version i use i get the same screen, says SYSLINUX 4.04 EDD 2011-04-18 COPYRIGHT (C) 1994-2011 H. Peter Anvin et al, with a blinking cursor beneath it and then nothing happens. does the same thing if i try using gparted or dban (recovery partition is still on there for windows and cant get it off thought that might be the problem) iv tried creating the usb install with unetbootin, pendrive, lili, and nothing all comes to down to same screen no matter how i dice it. anu suggestions here on what im doing wrong? i havent used ubuntu in around 6 years but dont remember it ever causing me this kinda headache.

---

### Post by ubfan1 on 2015-07-31
How much memory does it have?  Seems you can't even get to the grub menu screen.  Did you hashcheck the downloaded ISO?  If you get to the grub menu screen, try the media check and memory check before trying the "try" or "install".

---

### Post by grahammechanical on 2015-07-31
You are trying to solve a hardware problem with software. May be.

Windows 7 crashed. The factory reset crashed. Why? Syslinux is the Linux used to run Ubuntu on the live session DVD disc or USB stick. And Syslinux is not getting very far in the loading process. Why?

Faulty memory problems? Using a 64 bit ISO image of Ubuntu on a 32 bit CPU? Problem getting the right screen resolutions from the monitor? When you load the Ubuntu ISO image do you get a purple screen? If you do not, then the problem is happening very early in the loading of Syslinux.

Regards.

---

### Post by charlie32 on 2015-07-31
So I finally just decided to go with dvd install and got a little farther got to the purple screen with the icons on the bottom middle, then the ubuntu name with loading dots, then nothing, still can't get any further, used dban to wipe the hard drive and tried again still nothing, when windows and it'd recovery crashed it said I was missing several .dll files and couldn't finish the recovery install, it's a 64 bit with 4gb memory, but have tried both 64 and 32 bit same problem on either, I got the iso from ubuntu's website

---

### Post by leunam12 on 2015-07-31
Bad RAM maybe? Pull the RAM out and the battery; start the computer without RAM, it will beep probably of just do nothing (blinking lights). Unplug it and put the RAM back in and press the power button and hold it for 45 seconds; then plug it in and start. If that doesn't work try with only one stick of RAM. If that doesn't work, try the other one.

One thing that has work for me in the past with USB drives that don't want to boot is to invoke the temporary boot menu (usually F9 on HP's) and pick USB FDD from the menu as my booting device (that is if you are booting from USB stick).

---

### Post by charlie32 on 2015-07-31
So I got the grub menu started to the install but it keeps saying it could not get the info from the cd please check if the cd is in the tray? That was on a disk burned at x4 on a n other cd burned at x2 using the same iso I get a error saying: edd: error aaaa reading sector 374878

---

### Post by oldfred on 2015-07-31
In Disks click on icon in upper right corner and Smart Status. That will confirm if drive is ok or failing. 

It also can run tests on drive, but I do not know how to review results. Pass or fail at least says is drive is issue.

---

