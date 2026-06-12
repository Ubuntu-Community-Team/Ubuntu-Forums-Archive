---
title: "Grub loading please wait....Error 18"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by mtime2457 on 2007-08-13
I recently installed Ubuntu 6.0.6 on my home PC.  This was suppose to be a dual boot system.  After I was done installing Ubuntu on my second hard drive, at the reboot I received a Grub error.  It says Grub loading please wait....Error 18

---

### Post by mtime2457 on 2007-08-13
Just to add to this topic...Windows XP was already installed, all I did was to add a second hard drive and install ubuntu onto the second hard drive.

---

### Post by confused57 on 2007-08-14
If grub installed to your Windows drive's mbr, you can restore your Window's IPL to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Once you're able to boot your Window's drive without grub, you might want to consider setting up your system this way:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Here's a description & possible solutions for grub error 18:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

Before you do anything else, you might want to go into your bios setup and try changing your IDE slave drive controller to "auto", which is one of the suggestions in the above link.

---

### Post by mtime2457 on 2007-08-14
Hello,

To post a follow up I took the advice from consfused57 and loaded the Windows XP recovery CD (a windows xp installation CD will work as well).  I loaded the recovery CD and and selected the Repair/Recover option.  Windows will ask which operation system to recover, if you are like me and only had Windows XP on the hard drive all you will need to do is to enter 1 and press enter.  You will then need to type fixmbr and press enter, eject Windows CD and reboot system.  This is how I fixed my Grub loading please wait....error 18.

For general information on fixing Master Boot Record (MBR) or recovering windows xp;

[http://www.windowsnetworking.com/articles_tutorials/wxprcons.html](http://www.windowsnetworking.com/articles_tutorials/wxprcons.html)

---

### Post by Balvinder25 on 2007-12-22
hi all,
         ive windows xp pro sp2 and ive installed ubuntu 7.04 as the other os..now whenever i start my pc i have this error 18 pls wait..and the system completely hangs..prior this i had ubuntu 6.10 installed n had upgraded to 7.10 but due to some problems i had to get rid of ubuntu and install 7.04 again..but have started getting this problem..could someone please guide me through this ...problem cause im fed up of windows xp now...any help would be highly appreciated..thanks..

---

