---
title: "Partition does not end on cylinder boundary"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by MadEgg on 2010-06-14
I recently installed a new hard disk and reinstalled Ubunut (well, Kubuntu, but anway), and afterwards Windows 7.

My partition table was supposed to be:

```

/dev/sda1   ext2      /boot
/dev/sda2   extended partition for Linux install
/dev/sda3   NTFS      Windows Boot partition
/dev/sda4   NTFS      Windows Partition
/dev/sda5   ext4      /
/dev/sda6   ext4      /home
/dev/sda7   swapfs    swap

```

Most of this worked fine; I even created the partitions for Windows using the installer partition manager.

Here comes the problem: the Windows installer does not want to change the partition type, so the only way to install was to remove the partitions for Windows from the Windows installer and have the installer recreate them.

Somehow this messed things up. 

fdisk -l /dev/sda shows:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         122      975872   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             122       61640   494139393    5  Extended
/dev/sda3   *       61640       61653      102400    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           61653      182402   969917440    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5             122       24437   195311616   83  Linux
/dev/sda6           24438       60910   292967424   83  Linux
/dev/sda7           60910       61640     5858304   82  Linux swap / Solaris

```

The problem is the 'does not end on cylinder boundary'. This problem also makes it impossible to start cfdisk to change the partition table.

Right now I don't have any incentive to change the partitions as both Kubuntu and Windows run fine. Still it bothers me that something apparently is wrong. Is there any way to fix the partition table without reinstalling both OS'es?

---

### Post by garvinrick4 on 2010-06-14
If you notice one starts at same # other ends at, no big deal. Does all your OS's boot fine?

---

### Post by MadEgg on 2010-06-14
After some searching that seems to be the problem instead of the cylinder boundaries. The error I get when I run cfdisk is:

Bad primary partition 3: Partition ends in the final partial cylinder

Everything currently runs fine, but there is loads of space available so maybe the overlapping blocks are not currently used yet so no conflict can occur.

---

### Post by garvinrick4 on 2010-06-14
> **MadEgg said:**
> After some searching that seems to be the problem instead of the cylinder boundaries. The error I get when I run cfdisk is:

Bad primary partition 3: Partition ends in the final partial cylinder

Everything currently runs fine, but there is loads of space available so maybe the overlapping blocks are not currently used yet so no conflict can occur.

When I make my partitions i give them 1 meg between each partition. Have one install

that has partition ending on same as next partition has not seemed to bother anything for 
a long time.

---

### Post by srs5694 on 2010-06-14
In terms of the legality of the disk structures, there is no problem, as far as I can tell from the description. If cfdisk is complaining about this, then that's a cfdisk bug. You might try a more recent version. It's part of the [util-linux-ng](http://userweb.kernel.org/~kzak/util-linux-ng/) package, so check there for source code.

The problem with cfdisk probably derives from the fact that the standard for how partitions are aligned is changing. In Windows XP and previous versions of Windows, as well as most Linux partitioning tools until a matter of a few weeks or months ago, the standard was to align partitions on cylinder boundaries. This made sense a few decades ago when such alignment could improve performance for technical reasons that have long been moot; but today cylinder alignment is meaningless. Aligning partitions on cylinder boundaries has no performance benefit and is rather arbitrary anyhow, since the "cylinders" described by hard disks in their cylinder/head/sector (CHS) geometry values, as reported to the computer, are fictions. (Disks do have real cylinders, but the CHS values reported to the computer no longer correctly describe the disk's real geometry.)

Since Windows Vista, Microsoft has switched to a new partition alignment standard, and Linux partitioning tools are beginning to support this new method, too. In the new system, partitions are aligned on multiples of 1 mebibyte (1 MiB; 2048 sectors, given the usual 512-byte sector size). This alignment prevents performance degradation on the new "Advanced Format" disks that use 4096-byte physical sectors with 512-byte logical sectors, and to a lesser extent also with some types of RAID array.

Most core Linux utilities, such as the kernel, GRUB, etc., don't care about partition alignment; partitions can be aligned to the cylinder, to 1 MiB blocks, or not at all, and everything works. If cfdisk is refusing to work because of a particular alignment, it's probably trying to enforce long-obsolete partition alignment recommendations. In other words, it's broken. You should use something else, if at all possible. If that's not possible (say, if some utility is launching cfdisk and refuses to let you use something else), then you've got a problem. Upgrading cfdisk might help; or you might be able to temporarily rename cfdisk and substitute something else, such as fdisk or parted.

---

### Post by MadEgg on 2010-06-15
Thanks for the clear explanation. But your explanation only treats the cylinder boundaries. There's still the other problem of maybe overlapping partitions. Is it OK of the next partitions starts at the same block that the first partition ends? 

I see in my fdisk -l output posted above that sda2 starts where sda1 ends, and sda3 starts where sda2 ends and sda4 starts where sda3 ends. But sda5, sda6 and sda7 show no such overlap. Or is this some fundamental difference between primary and extended partitions?

---

### Post by srs5694 on 2010-06-15
The "fdisk -l" command only shows partition boundaries in cylinder terms. Chances are the partitions aren't actually overlapping, but you'll need to check with greater precision to be sure. Try "fdisk -lu" instead; that will show the start and end points in units of sectors rather than cylinders.

---

### Post by MadEgg on 2010-06-15
Allright, that gives me this:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     1953791      975872   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2         1955838   990234623   494139393    5  Extended
/dev/sda3   *   990234624   990439423      102400    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4       990439424  2930274303   969917440    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5         1955840   392579071   195311616   83  Linux
/dev/sda6       392581120   978515967   292967424   83  Linux                                                                                                                      
/dev/sda7       978518016   990234623     5858304   82  Linux swap / Solaris

```

Seems better indeed. Now there appear to be some gaps between some of the partitions but that shouldn't be a problem I suppose.

Thanks a lot. Now I just need to update cfdisk :)

---

### Post by dino99 on 2010-06-15
you may need to boot with a good tool like partedmagic to check partitions errors and repair them

[http://partedmagic.com/](http://partedmagic.com/)

---

