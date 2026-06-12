---
title: "Dual Booting - shaken, not stirred"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by saggio on 2007-07-20
I've been using Ubuntu for awhile exclusively now, but there are some programs that I need to use once in a while for work and various other things. Now, I've been putting off reinstalling XP on a separate partition for awhile now, but the time has come for me to actually go through with it and install XP again. But the caveat to all of this is I don't want to install it over top of Ubuntu.

I've read various things, and I have gotten the instructions for reinstalling/making GRUB work after you install XP, and I've used gparted from the LiveCD to resize and create new partitions (specficially a FAT32 partition for XP) so that I can install Windows without too much hassle. The problem comes when I use my XP CD and I get to the part when I must install Windows on a specific partition - all it identifies is an unknown file system on C: - which I presume the XP installer reads as my /dev/hda. 

I don't know how to get it to read /dev/hda4 (which is my FAT32 partition) as the only partition available (so that I don't accidentally wipe out my Ubuntu installation). Is there anyway to do this? 

Is it possible (or advisable) to use VMWare to install XP on a specific partition of my root harddisk, so that it doesn't mess up the other partitions and still allows me to fix and use GRUB to boot into Ubuntu? 

Thanks in advice.

---

### Post by Pumalite on 2007-07-20
I don't know about VMWare, but I know this: XP demands a primary partition, and I think it demands to be in sda (not sure). What I'm sure of is that you can do the partitioning with Gparted (the best partitioner). Hope it helps. You can install XP, take the MBR and then reinstall Grub with the live CD.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

