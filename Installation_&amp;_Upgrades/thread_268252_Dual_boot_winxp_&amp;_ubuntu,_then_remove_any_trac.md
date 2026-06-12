---
title: "Dual boot winxp &amp; ubuntu, then remove any traces of ubuntu"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by nyxynyx on 2006-09-29
Hello. I'm planning to use ubuntu on my friend's laptop for a while then remove it. How do i go about doing that? Like removing ubuntu, removing the bootloader, and change the partition back to ntfs and combine with the existing ntfs partition containing winxp installation, or any other things i need to do. thnx!

---

### Post by morphodone on 2006-09-29
When you are done with ubuntu you would need to boot into windows.

Then open the disk management utility and delete the ubuntu partition(s).

You would then have to resize the windows partition with a third party 
utility.  I think the gparted live cd will do that for you.

Then you can restore windows to the mbr by booting a windows 98 floppy.
```
fdisk /mbr
```

Of course you'll want to back up any important data...

---

### Post by kristiankarlson on 2007-11-07
Hi,

I have the same problem. I have installed Ubuntu and XP with dual boot. However, I want to install Ubuntu on a different computer and keep XP on this one. My problem is that, for instance, Partition Magic  does not recognize the ubuntu-drives. This means I can not format the ubuntu-drives and merge them with the other drives. I have four drives:
 - WinXP
 - Ubuntu
 - Ubuntu Swap
 - MyFiles

I want to merge the Ubuntu-drives into the MyFiles. That is, remove Ubuntu completely and then expand the MyFiles-drive. I find it very tricky - so please, spell it out for me ;)

All the best, Kristian

---

### Post by stevie_velvet on 2007-11-07
Partition Magic v 8 recognises EXt3 File system

---

### Post by kristiankarlson on 2007-11-07
Thanks!

---

### Post by kristiankarlson on 2007-11-09
Hmmm.

Partition Magic 8 (PM8) seems to have the same problem. Opening PM8 the following message pops up:

"Disk 1 appears to have partitions created using a different drive geometry (75h 63s). This serious problem can lead to data loss..." and it continues saying 'do not use PM8'!

This puzzles me. Ubuntu seems impossible to de-install.

Any other suggestions?

---

### Post by kristiankarlson on 2007-11-09
By the way. I am gonna try 'GPARTED' to see if it works. Is this a good idea?

---

### Post by Fire_Chief on 2007-11-09
As Morphodone suggested earlier, use the GParted LiveCD. It can be downloaded from [here]("http://gparted-livecd.tuxfamily.org/")

---

### Post by sundance2007 on 2008-01-27
> **morphodone said:**
> 

Then you can restore windows to the mbr by booting a windows 98 floppy.



Any other way to restore the mbr? I don't have a floppy on the system I need to remove Ubuntu from.

---

