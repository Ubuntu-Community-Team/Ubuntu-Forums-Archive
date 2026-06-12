---
title: "Ubuntu 10.04 &amp; Vista Home basic dual boot"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by rj98942 on 2010-08-23
I was wondering who would be comfortable walking me through some stuff dealing with both operating systems. i already have both dual booted on an acer aspire laptop (i know, really cheap) one thing is how do i remove all the options for when i have to pick the operating system? how do i change the user controls for different logins. i can not make one admin and another desktop users. let me know when you can. thanks.
ryan

---

### Post by ajgreeny on 2010-08-23
I don't totally understand your question.

You ask:-
   "how do i remove all the options for when i have to pick the operating system?".
This is normally a simple grub menu choice between ubuntu and windows, if you let ubuntu put grub on the first disk's MBR, and there is no need to do anything more.  What are all these options you are asking about?  If it is just new kernels, see below.

As new kernels appear in the update notifications, they will be added to the grub menu, and if you wish you can remove the oldest of the kernels, but for safety, I recommend you keep the newest kernel and the one previous version, just in case something goes wrong with one of them.

Your second comment:-
  "i can not make one admin and another desktop users."
does not mean much to me either.  You can make as many users as you wish; the first user is setup at installation and is the admin user by default, but you can later add others and give them whatever permissions, including admin rights you want.  All users can have admin rights if that suits you, or you can limit admin to yourself, and give all others only desktop rights.

I hope that helps a bit

---

### Post by rj98942 on 2010-08-25
The options i have are as follows: 
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
ubuntu, with linux 2.6.32-21-generic
ubuntu, with linux 2.6.32-21-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Vista (loader) (on /dev/sda1)
Windows Recovery Environment (loader) (on /dev/sda2)

i would like to remove Windows Vista (loader) (on /dev/sda1), the memory tests and all the ubuntus except for the top one Ubuntu, with Linux 2.6.32-24-generic. those are the only 2 options that i use as of right now. 

i am thinking that i should have put my post in the absolute beginners section. you talk about getting to the grub menu. i'm not sure how to access that.

---

### Post by oldfred on 2010-08-25
Some info on custom menus:

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

How to: Create a Customized GRUB2 Screen that is Maintenance Free. 
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

