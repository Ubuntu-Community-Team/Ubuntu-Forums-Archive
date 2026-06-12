---
title: "Can bootup after install"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by bonehead01 on 2008-07-23
I am receiving the following error after reboot after install. 

GRUB Loading stage1.5

GRUB loading, please wait...
Error 17

I have researched other error messages but they all appear to be related to a dual boot install and mine is not.   I tried a download of Super Grub but it could not correct the problem.  The following is my output from sudo fdisk -l:

Disk/dev/sda 30.0 GB  30005821440 bytes
(extra disk info)

Device Boot    Start    End      Blocks     ID   System
/dev/sda1      1        3492     28049458+  83   Linux
/dev/sda2      3493     3648     1253070     5   Extended
/dev/sda5      3493     3648     1253038+   82   Linux swap / Solaris

I seem to be able to run the Live disk just fine.  I have a Tecra 8200 with an IDE hd.


Thanks for any help with this issue.

---

### Post by logos34 on 2008-07-23
check bios settings
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

error 17
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by bonehead01 on 2008-07-24
I reviewed the 2 links and I noticed that I don't appear to have any stuff setup for Grub such as menu.lst.  I am not sure if my install cd is bad or what.  Live runs fine but installs don't seem to be doing a complete install.  I was doing the install over Freespire.  I am not sure if the std install does a complete format of the disk or not.  I was able to reinstall Freespire without issue.

---

