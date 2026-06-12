---
title: "Gparted refuses to assign mount points"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by jeeves on 2006-10-29
I'm installing Edgy on a computer that already has multiple partitions. Everything goes fine until I get to the screen where I tell the install program which partitions I want Ubuntu to own. Then it just keeps showing me the warning message below and does not let me proceed to the next step ](*,)  (see screengrab below):
> 
"FAT and NTSF filesystems may not be used by the system. It is usually best to mount them somewhere under /media"
[IMG]http://www.sonic.net/~artontap/mythtv/gparted.gif[/IMG]

**Any ideas how I can get unstuck?** This is a intended to ba a dual boot system that already has Windows installed on hda1. 

[LIST]
[*]hda5, hda7, hda8, hda10 are FAT32 and intended to be shared by both  Windows and Linux. 

[*]I plan on using hda6 for my SWAP partition, and hda9 for my "/" mount point.

[*]I did of course press "Forward"

[*]I did check the boxes to format hda6 & hda9 - However they install script has not done this yet.
[/LIST]

---

### Post by hajk on 2006-10-29
Working with prior partitions was a problem with the Dapper installer as well, but at least there were some work-arounds. The Edgy installer (GParted really) is a step back in this regard. 

I already had an earlier version of Edgy installed on /dev/sda1 (64MB Ext2 mounted on /boot), /dev/sda6 (JFS mounted on /) and a swap partition /dev/sda5 shared with an installation of Dapper and Gentoo. I tried to install Edgy to the same /dev/sda1, /dev/sda6 and /dev/sda5 setup, assigning the mount points /boot, / and swap respectively, but the installer would not proceed because I had not specified a root partition. Reformatting these partitions or not would not make a difference. I tried everything I could think of to get past this hurdle, but the installer wouldn't budge -- it just didn't see the root partition I had indicated.

In the end, I decided to let the installer wipe the whole disk and do a default install -- that went well. Luckily, I had a good backup of my personal stuff, and I was ready to get rid of Dapper and Gentoo.

So, you may have to create some unallocated space (or all of it) on your HD to get Edgy installed... and yes, it sucks!:rolleyes:

---

