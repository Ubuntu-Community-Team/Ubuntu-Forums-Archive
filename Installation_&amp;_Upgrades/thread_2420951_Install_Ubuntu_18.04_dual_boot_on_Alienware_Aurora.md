---
title: "Install Ubuntu 18.04 dual boot on Alienware Aurora r8"
date: 2019-06-13
forum: Installation &amp; Upgrades
---

### Post by larry90 on 2019-06-13
Hello everyone,


I’m trying to install Ubuntu 18.04 next to Windows (dual boot), but I’m having some problems.
First  of all, I changed the bios settings from raid to ahci and all was   working great; than I created the bootable stick, with secure boot   disabled, and it worked great on another computer (I opened the live   session and the installation), but here the problems started!


More  specifically, the problem is that in my Aurora R8 the usb is not   working correctly, I can get to the options to try or to install ubuntu,   but after I pick “try” the computer “freeze” while trying to load: I   can see many times  [Failed] to start user manager for uid 121 and than   it gets stuck at “started session c(number) of user gdm.or details.
I  tried another approach, installing ubuntu instead of using the live   session, all seemed fine until the end of the installation when I needed   to reboot the computer, after that the problem presented itself again!   Still the same error and stuck with a never-ending loop.


Can anyone help me with my problem?


Sorry if some parts are not understandable enough, but English is not my first language and I m a novice with computer tech :grin:
Thanks for your help, have a great day

---

### Post by oldfred on 2019-06-13
Are Alienware still based on Dell, so similar issues.
Did you update UEFI and if SSD update firmware to latest versions?

These may now be older.
        Alienware Area 51 R4 16.04 UEFI update
[https://ubuntuforums.org/showthread.php?t=2397456](https://ubuntuforums.org/showthread.php?t=2397456)
[https://askubuntu.com/questions/1085884/install-ubuntu-on-alienware-15-r4](https://askubuntu.com/questions/1085884/install-ubuntu-on-alienware-15-r4)
Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr](http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr)

---

### Post by larry90 on 2019-06-14
Yes, both UEFI and SSD are updated. I try to post exactely what I get while booting:
[FAILED] Failed to start User Manager for UID 121.
See 'systemctl status [EMAIL="user@121.servic"]user@121.servic[/EMAIL]e' for details.
[ok] removed slice User Slive of gdm.
[ok] createdd slice User Slive of gdm.
This message is on loop and it usually adds a line with [ok] Started Session C(incresing number) of user gdm.
but than suddenly it gets stuck

Edit: Update: I managed to boot it correctely in ubuntu safe mode and there I noticed i coudn't change the resolution and that GPU was unclaimed.
Edit 2: I think i managed to solve my problem! The only annoying part now is that i don't have the alien logo while booting but the windows one... but it's ok :D

---

### Post by jonathan-laurent on 2019-07-17
> **larry90 said:**
> 
Edit 2: I think i managed to solve my problem! The only annoying part now is that i don't have the alien logo while booting but the windows one... but it's ok :D

**@larry90:** I am running into the exact same problem that you described. Would you mind sharing your solution? Thanks! :D

---

