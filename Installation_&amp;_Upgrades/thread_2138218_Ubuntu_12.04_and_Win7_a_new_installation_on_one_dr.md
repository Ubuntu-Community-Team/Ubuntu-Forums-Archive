---
title: "Ubuntu 12.04 and Win7 a new installation on one drive - how many partitions?"
date: 2013-04-23
forum: Installation &amp; Upgrades
---

### Post by Malmberg on 2013-04-23
I, "The Newbie", is so happy with my "new" Ubuntu 12.04 laptop, this is a fairly new HP NX-9420 (plus 10 years, I guess :-)), that got a new life after I left WinXP/7.

So now I'm going for the next level.
I have a Shuttle Xpc that I would like to use as my desktop, with Ubuntu 12.04 and Win7 - I have some applications that only comes in Windows versions.

I have found several good instructions on how to do this - there is just one point (at the moment) where I'm a bit confused:

Should I partition my empty HD in 4 partitions:
1: Win7 OS
2: Win7 apps/docs
3:Ubuntu /
4:Ubuntu /home

- or have I (again) misunderstood something?

Cheers, and thanks in advance
Malmberg

---

### Post by dino99 on 2013-04-23
you are right, but also need a swap partition

[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by oldfred on 2013-04-23
Since with swap that will be more than the allowed 4 primary partitions, you have to convert one primary to an extended and then can have many logicals inside the extended.

Windows default install uses two primary partitions. One is a 100MB boot/repair (hidden in Windows) and the main install. You can have the NTFS data partition as a logical and all the Linux partitions as logicals. I suggest 10 to 25GB for Ubuntu / (root) and whatever you want for /home. Swap can be equal to Ram in GiB not GB only if you want to hibernate which I do not suggest when dual booting. Otherwise some swap of 2GB is fine if you have 4GB of RAM or more.

---

### Post by Malmberg on 2013-04-25
Hi dino99 & oldfred,

Found another solution!
I had a new spare drive - so Ill go for 2 drives in the Shuttle instead - that seems much easier :-)

Thanks 
Malmberg

---

### Post by oldfred on 2013-04-25
Either disconnect Windows drive or be sure to use manual install and install grub2's boot loader to the Ubuntu drive.
You want to make sure each drive can boot without the other drive.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

