---
title: "Uninstallation help"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by Treubaria on 2011-05-17
Hi,
I've used Ubuntu for a number of years now, and have enjoyed it.  I'm in the process of selling my laptop, and the guy that is buying it wants nothing to do with Linux.  

Is there an easy way to uninstall Ubuntu?  I've been looking for hours and all I can find is people using a Windows Recovery CD, which I don't have.  A few years ago, I remember running across a program that made uninstallation a breeze.  Does anybody know what it was or where I could find it?

Cheers

---

### Post by shantanu18 on 2011-05-18
IS Your laptop running on dual-boot or only linux?

ONLY_LINUX: Then install a new os (you want to) on the same partition of linux. Linux partition is ext3/ext4 so windows will format it with ntfs or fat32. If all other disk are also in ext3/etx4 then just format them after install windows(normal format [from disk management ].

DUAL-BOOT: one, just reinstall windows it will remove linux from dual boot list. Format the linux drive to ntfs or fat32.

I think these methods are easy one. Best of Luck!

---

### Post by Quackers on 2011-05-18
Or, if you are running Vista or Windows 7 you can make a repair disk, which will repair the Windows bootloader.
Control Panel > Backup & Restore Centre then in the left pane click on "make a recovery cd".

---

### Post by Hedgehog1 on 2011-05-18
Fix MBR

First, get your PC to boot directly into Windows again:

To make a Windows 7 / Vista emergency repair disk (in case you don't already have one made):
[IMG]http://img641.imageshack.us/img641/9550/small50createrepairdisk.png[/IMG]

If you are unable to make a recovery disk, you can download the ISO for [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

---

### Post by Hedgehog1 on 2011-05-18
To remove Ubuntu:
[IMG]http://img718.imageshack.us/img718/7687/small55diskmanagement.png[/IMG]
Remove Swap Partiton
[IMG]http://img97.imageshack.us/img97/4905/small56deleteswap.png[/IMG]
[IMG]http://img231.imageshack.us/img231/2992/small57freespace.png[/IMG]
Remove Ubuntu Partition
[IMG]http://img96.imageshack.us/img96/5986/small58deleteubuntu.png[/IMG]
Remove extended Partition
[IMG]http://img848.imageshack.us/img848/8053/small59deleteextended.png[/IMG]
Expand windows partition to use all the space
[IMG]http://img3.imageshack.us/img3/7880/small61extendwin7volume.png[/IMG]


***The Hedge***

:KS

---

