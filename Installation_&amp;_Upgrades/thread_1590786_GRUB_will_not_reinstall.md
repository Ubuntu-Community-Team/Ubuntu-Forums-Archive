---
title: "GRUB will not reinstall"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by lightford on 2010-10-08
Hello all,

First time poster here!

I have been working through the process of installing XP after installing Ubuntu 10.04 on a clean slate.  XP is now installed and, of course, I can only boot to it since the MBR was overwritten.  SO, I am now following the GRUB 2 restore method found here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Everything works well until I reach the grub-install portion of the instructions, at which point I receive this error:

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/*yada yada for my main Ubuntu partition */dev/sda1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea..
~
~*More errors and warnings referring to blocklists*
~

So, am I getting this error because I am trying to install to /dev/sda1 instead of just /dev/sda?  I chose /dev/sda1 since that is the reference I received during the **mount | tail -1 **command.

Looking at my hard drive in Disk Utility while booted in the 10.04 Live CD I see that Ubuntu is installed to /dev/sda1, XP is on /dev/sda2 and the Extended and Swap partitions are on /dev/sda3 and sda5 respectively.

I appreciate your help on this!
Jake

---

### Post by andrewthomas on 2010-10-08
Use the instructions here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

and yes, you do want to install grub to sda and not sda1

From the information you provided 
```

sudo mount /dev/sda1 /mnt
```
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by Rubi1200 on 2010-10-08
If the method suggested by andrewthomas does not work, then try this:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by lightford on 2010-10-08
Well that was easy enough.  Now I am just working on getting GRUB to recognize XP.  And it appears a simple update of GRUB allowed it to recognize XP.  Awesome!  Thank you for the quick help.

---

