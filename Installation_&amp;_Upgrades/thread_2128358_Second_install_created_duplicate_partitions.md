---
title: "Second install created duplicate partitions"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by hawkhock on 2013-03-22
Dual boot with Win7 installation. First install of 12.05LTS failed. Burned ISO at lower speed and second install completed successfully. I now have duplicate partitions for each install. Two Window loaders, etc. How do I fix this?

---

### Post by ahallubuntu on 2013-03-23
~

---

### Post by hawkhock on 2013-03-23
No - am not sure I have a problem. After I posted, I installed GPart to check out the partitions and sizes. SDA1 is a Windows boot loader flagged as boot & diag. SDA2 Windows boot loader allows me to boot into Windows. SDA4 & 7 are both Ext4 with SDA 7 as Mount Point. SDA3 is the HHDRecovery partition.

If all is okay, the only other question would be should I change any of the partition sizes.

Thanks for taking a look at this.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x900b3d5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2         3074048   349142825   173034389    7  HPFS/NTFS/exFAT
/dev/sda3       954755072   976773119    11009024   17  Hidden HPFS/NTFS
/dev/sda4       349143038   954755071   302806017    5  Extended
/dev/sda5       557099008   938246143   190573568   83  Linux
/dev/sda6       938248192   954755071     8253440   82  Linux swap / Solaris
/dev/sda7       349143040   557099007   103977984   83  Linux

Partition table entries are not in disk order
ghock@ghock-Satellite-P500:~$

---

### Post by ahallubuntu on 2013-03-23
~

---

### Post by darkod on 2013-03-23
For future reference, linux will never automatically try to use existing partitions unless you tell it to. What if you wanted a second install without overwriting the first? That's why it will never overwrite partitions.

If there are partitions from previous failed install that you don't want to keep you have to:
- Delete them first if you want to use the automatic method in the second install, or
- Use the manual install (Something Else) and manually set the existing root partition to be used with mount point / and the existing swap to be used as swap.

---

### Post by hawkhock on 2013-03-23
**[COLOR=#FF0000]Or, you could just blow away sda4, sda5, sda6, and sda7 with Gparted and just re-install one more time from scratch and let it use the new free space.[/COLOR]**

Am elementary Ubuntu student and in over my head at this point. It appears that the easiest would be "blowing away" sda4,5,6,7 and reinstalling BUT

? What happens if do nothing?
? Or am I compromising the install by not having it partitioned correctly?

If I proceed --
? What does "blow away" mean?
? Will using Live CD boot me into my current install of Ubuntu?
? How to access GPart on LiveCD?
? How to erase sda 4-7?
? After erasing sda 4-7 do I reboot to the Live CD to reinstall?

---

### Post by hawkhock on 2013-03-23
I did the research and learned how to use GParted to delete the partitions using the LiveCD. 

Question remains -- what if I do nothing and leave install and partitions as is?

---

### Post by ahallubuntu on 2013-03-23
~

---

### Post by hawkhock on 2013-03-23
thanks for the info. I am a minimal computer user - no fancy bells and whistles - and probably have enough disk space to either leave as is or delete the one partition. Appreciate your timely reply and help.

---

### Post by darkod on 2013-03-23
Correct, there is no drawback if you leave it as it is. Only the wasted space.

Apart from that, ubuntu will keep working for years without any issues.

---

