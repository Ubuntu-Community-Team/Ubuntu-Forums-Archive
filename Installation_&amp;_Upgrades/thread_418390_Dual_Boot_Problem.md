---
title: "Dual Boot Problem"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Arepo on 2007-04-22
Well I thought I would give Solaris a try, so I planned on dual booting it with Ubuntu because I have been using Ubuntu for awhile. First, I installed Ubuntu on the first partition and then for the 2nd partition, made a swap. Then after the installation, I copied the info from /boot/grub/menu.lst so I could put it into Solaris' GRUB menu.lst and boot into Ubuntu. Next I put in the Solaris DVD and installed it on partition 3, everything went ok. I logged into it just fine and I had Solaris working. Then I added the info into the GRUB menu.lst of Solaris, restarted and it noticed Ubuntu and I could boot into both of them and everything was good.

I went out of house for a few hours and I came back, turned on the computer and was greeted by a screen with "GRUB_" and the computer was beeping repeatedly.

I'm at a loss of what happened and if anyone can shed some light on the problem that would be great and even better if you could guide me through it. Well thanks for the help

I'm using Solaris 10 11/06 and Ubuntu Edgy.  And I'm rather new to Ubuntu so try not to make it too complicated ^_^

---

### Post by davidgarcin on 2007-04-22
I have no idea what might cause it to do that... however, it sounds like re-installing GRUB might solve your problem.

Unless you have a specific reason for doing otherwise, I suggest installing the Ubuntu GRUB, and configure your menu choices from Ubuntu's menu.lst.

Here's a link to reinstall GRUB using the Ubuntu Live CD: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Once you've reinstalled GRUB, boot into Ubuntu and edit /boot/grub/menu.lst.  You may have to google a bit to find the correct options for booting into Solaris, but if you add the following to your menu.lst, it should work:

```

title           Solaris
rootnoverify    (hd0,2)
chainloader +1
makeactive
```

This is a general form for booting just about any OS from GRUB, but there is probably a Solaris-specific way to do this (I've never used Solaris).  (hd0,2) stands for your first hard disk, third partition.

-Dave

---

