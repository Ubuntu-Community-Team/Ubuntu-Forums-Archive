---
title: "Problem With Partitions and Booting Vista with GRUB"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by faceoftheearth on 2007-05-11
I recently installed Feisty onto a partition formerly reserved for XP. When I installed I did a manual install that simply formatted the XP partition and installed Feisty in that location. GRUB was then placed in the default location, wherever that is.

My goal is to be able to dual boot my current Vista install with Feisty. However, GRUB can't seem to find the Vista bootloader. I've tried every partition on the drive. Vista is in /dev/sda5 so I have it in menu.lst as (hd0,4). However, GRUB gives me an Error 12, "invalid device requested." Furthermore, cfdisk tells me "Error 7, bad logical partition. Logical partitions overlap." I have a similar error, 105, in Partition Magic 8 which tells me the partitions are messed up. So my theory is that I've messed my partitions up somehow. I have a screenshot of gparted included that has my menu.lst as well. 

Is there any way to fix this short of a complete do over? I have my Vista install backed up so if necessary I can just do the complete PC recovery option and put the image back on my hard drive and start over from the beginning, but I'm rather attached to my Linux install as well (just got it comfortable) so if possible I just want to find a way to boot them both. 

If there's any more information you need, I'll be happy to post it. 

Thanks

EDIT- /dev/sda8 is a general storage partition.

---

### Post by davidgarcin on 2007-05-11
Vista does this weird thing where it sometimes installs its bootloader on the existing XP partition instead of its own  (this is what happened to me, and several others).  Maybe this is the case for you as well, and the Vista bootloader got erased when you formatted the XP partition for Ubuntu.

If you look at your Vista partition in Ubuntu, you should see c:\bootmgr and c:\Boot (which contains a whole bunch of locales, as well as some BCD stuff).  If you don't see them, that's definitely your problem.  Let me know what you've got, and we'll take it from there.

---

