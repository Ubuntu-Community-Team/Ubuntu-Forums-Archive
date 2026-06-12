---
title: "triple boot: xp, 7, ubuntu 11.04"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by love_linux1 on 2011-07-24
**[SIZE="2"][FONT="Arial Black"]how to triple boot ubuntu with xp and 7?[/FONT][/SIZE]**

 I have installed 'WIN XP' 1st on HD1, then installed 'WIN 7' on HD2.. Now i want to install ubuntu 11.04  on HD3, means fresh install (not windows alongside). I want to know whether there will be any BOOT problem for XP and 7? Will it show all 3 os?

Please help.

---

### Post by oldfred on 2011-07-24
Depends on how you installed windows. Windows can only boot from one primary partition, so standard installs literally move all boot files from the second install to the first. With two drives you can force the install to only be on that drive, but that is not the standard install.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

You have to use manual install (Something else in Natty) to get where to install grub2's boot loader. You will want to install grub's boot loader to the Ubuntu drive probably sdc.
Then in BIOS boot using sdc.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Split dual boot win7 & XP - Instructions meierfra. post #3
[http://ubuntuforums.org/showthread.php?t=1421737](http://ubuntuforums.org/showthread.php?t=1421737)


Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

---

### Post by love_linux1 on 2011-07-24
Thanks everyone to reply.

Which installer should I use? 

Ubuntu-11.04-desktop-i386.iso or Ubuntu-11.04-desktop-amd64? I have a 32-bit intel pc. 

Which one is called natty narwhal?

thank you.

---

### Post by oldfred on 2011-07-25
If your computer is so old to only have a 32bit processor you may not want the full Ubuntu. Almost all new Intel chips are 64bit and follow the AMD standard which just was backwards compatibility with 32bit Intel code.

Natty is 11.04.
Versions and release & support until dates:
[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases)
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by oldfred on 2011-07-25
Please do not double post. You have others helping you in this thread. We are all volunteers and do not appreciate having to do double work.

[http://ubuntuforums.org/showthread.php?t=1811242](http://ubuntuforums.org/showthread.php?t=1811242)

And you necromancied this thread from 2009 with the same question.

[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

