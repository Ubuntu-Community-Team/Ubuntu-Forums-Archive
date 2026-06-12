---
title: "Invalid boot.ini file"
date: 2016-07-07
forum: Installation &amp; Upgrades
---

### Post by abhi1996 on 2016-07-07
whenever i try to install lubuntu os from the USB drive I am always encountering a problem as shown below....
[COLOR=#ff0000]**Invalid-boot.ini-file**[/COLOR].
[COLOR=#ff0000]**C:\WINDOWS**[/COLOR]
please some one help. currently I use windows xp of sp3 ram-1gb and processor is Intel core duo

---

### Post by grahammechanical on 2016-07-07
Here you can see the installation instructions.

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

We do not run the Ubuntu installer from inside a loaded Windows operating system. Windows uses ini files to run a program on a CD from within Windows. The Ubuntu installer image (ISO) does not have an ini file because that is not the way we install Ubuntu.

Regards

---

### Post by DuckHook on 2016-07-08
grahammechanical is entirely correct. Only change I would make is to point you to Lubuntu's installation instructions instead of Ubuntu's:

[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)

*Thread moved to **Installation & Upgrades** as the more appropriate forum.*

---

### Post by abhi1996 on 2016-07-09
hello, i have tried to install from the usb stick but when i try to boot the lubuntu as from the methods of link given by you , Im getting the same error as i qouted above(I've tried to enter into bios and choose the boot up file ,i.e; usb stick but still facing the problem)

---

### Post by yancek on 2016-07-09
You need to first enter the BIOS setup when booting the computer so that you do not boot into windows.  You need to set the usb you are using to try to install to the first boot priority in the BIOS setup.  Accessing setup varies from computer to computer.  On initially booting you should see at the bottom of the screen a brief (3-5 seconds) message telling which key to hit to enter setup.   So what happens when you enter the BIOS, what options do you see?

---

### Post by grahammechanical on 2016-07-09
On my motherboard (BIOS boot system) a USB memory stick with an OS on it, such as a Lubuntu installer, is seen as an external USB drive and I have to go to the section for hard drives and select which drive to load from. Setting the boot order of priority is not enough.

Regards.

---

### Post by abhi1996 on 2016-07-14
okok, can u eloborate me how to do that ???????
grahammechanical..

and also i like to point out that in the instructions (the link in which you provided, see the second image) there the bios is showing correct name of USB but in mine it is showing as USB-ZIP
please help me here

---

### Post by oldfred on 2016-07-14
BIOS vary, but something like this:

How old is your system?
 XP was around for years. Old XP only booted from CD/DVD, newer systems then started to boot with USB ports.

---

### Post by abhi1996 on 2016-07-16
Thanks grahammechanical . But I just want to know that is it  safe to boot from boot-loaders

---

### Post by abhi1996 on 2016-07-29
when i did that procedure as asked by [COLOR=#DD4814][COLOR=#000000][yancek]("https://ubuntuforums.org/member.php?u=1928724") ,[/COLOR][/COLOR]i was always ending up on a blue screen showing the choices to load the os ,where i choose USB but problem is it is always showing as "USB-ZIP" but not as"USB-2.0....."(once i have entered but now im unable to able to boot from live USB)
and one more thing i found suspicious is that my usb drive has been dectecting as a disk drive but not as flash drive....

---

### Post by oldfred on 2016-07-29
My old BIOS system would not boot any USB entries.
The USB flash drive boot was seen as another hard drive under hard drives.

---

