---
title: "Ubuntu 12.10 installer is not seeing my partitons."
date: 2012-12-03
forum: Installation &amp; Upgrades
---

### Post by cetacea on 2012-12-03
In preparation of installing ubuntu 12.10 for dualboot along with pre-installed win7, I encountered a problem: that the intaller, upon reaching the point where I have to choose a partition for intallation does not see any thing at all, and freezes. After some google-fu, I figured out that I can learn something by the following command.

=======================================================================

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa4c01ee8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   323702783   161646592    7  HPFS/NTFS/exFAT
/dev/sda3       940214272   976543743    18164736    7  HPFS/NTFS/exFAT
/dev/sda4       323702784   940214271   308255744    5  Extended
/dev/sda5       323704832   429744127    53019648   83  Linux
/dev/sda6       429746176   647206911   108730368   83  Linux
/dev/sda7       647208960   940214271   146502656   82  Linux swap / Solaris
Partition table entries are not in disk order

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0b6f1346

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    16775167     8386560   84  OS/2 hidden C: drive

Disk /dev/sdc: 4016 MB, 4016045056 bytes
90 heads, 23 sectors/track, 3789 cylinders, total 7843838 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcca776ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8192     7843837     3917823    b  W95 FAT32

=====================================================================
Trouble is, I cannot really tell what I need to do to make the installer see the partitions that I created for it. 

Thanks. 


Ps. I use a HP laptop with an hdd and a small ssd.

---

### Post by darkod on 2012-12-03
In this kind of setup, I think the hdd and the ssd are joined together in some sort of raid0 setup, called Intel Smart Response Technology or similar.

Google around for installing dual boot with ISRT. I think it was only possible if you break up the hdd+ssd connection and they can be seen as separate disks. But I don't know if windows will work slower after that since it uses the ssd as some sort of cache I think.

---

### Post by cetacea on 2012-12-03
Thank you. Will do that. But in the mean time, I just realised that, when I log into win7 (pre-installed), it still thinks the whole hdd is its to use, when in fact I just chopped quite a bit out for ubuntu. I mean, win7 does not see the partitions that I made using Gparted. Is that normal? And might it be related?

---

### Post by darkod on 2012-12-03
It might be. And you should shrink windows partition with windows Disk Management, otherwise it can complain about Gparted touching it. After the shrink reboot few times to do its disk checks.

---

### Post by cetacea on 2012-12-03
Disaster... I successfully installed Ubuntu by "dmraid" command, but... when I tried to boot from win7 it tried to 'recover' presumably what it considers lost. And it did.. by blowing everything away.. including itself. Now I have grub rescue command in place of booting screen... well. you live and learn. But what am I supposed to do now?

Oh.. the recovery tool that win7 used? It was HP provided kind of a thing. Nowadays the physical dvd containing windows is a sort of a rarity. And since my machine doesn't even have an odd, it makes sense as well. But now I really have a serious problem. I probably can install ubuntu first this time, and windows second, but I am not entirely sure if the same thing would not happen, namely the stupid windows trying to overtake everything. I'll just have to fumble onwards....

---

### Post by darkod on 2012-12-03
You should have undone the linux partitions first, especially since win7 wasn't even seeing the change.

And when you said you installed with dmraid command, did you break up the hdd+ssd connection of you simply installed on top of the IRST as it was? I don't think you can successfully install dual boot on top of it. And if you broke them up, they should be separate disks now.

The grub rescue is not a problem, it only means the ubuntu partition is gone. But win7 is more important now, with all your data inside.

Do you want to try and recover it? Post the parted results from live session again, lets see what is there.

---

### Post by oldfred on 2012-12-03
Some others have threads with Intel SRT. Do not think it really matters if a different vendor as the Intel part is the same.

Some have just turned off the SRT and installed Ubuntu to SSD. Others turned it off, installed Ubuntu and turned it back on. I do not know RAID but it seems a strange way to implement the caching of data for Windows.

       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
 > You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

