---
title: "Grub not installed properly"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by snakep on 2007-11-12
Hello,

I just installed Ubuntu 7.10 for the first time.  I replaced an installation of Suse 10.1, and I also have Windows XP.  Now Grub isn't working.  When I reboot, I get "Grub loading ..." and then "Error 22".

Right now I am working from the live disc.  I tried following other instructions I found here, so I mounted the Ubuntu partition with "sudo mount -t ext3 /dev/sda2 /root/" and then navigated to /root/boot/.  However, the file "menu.lst" was not there.  Does this mean that grub wasn't properly installed?

FYI, the results of "sudo fdisk -lu" are :

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x54f954f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sda2        81915435    85819229     1951897+  83  Linux
/dev/sda3        85819230    86799194      489982+  82  Linux swap / Solaris
/dev/sda4        86799195   156296384    34748595   83  Linux

```

/dev/sda2 is where / is mounted, /dev/sda3 is swap, and /dev/sda4 is /home.

Thanks in advanced for any help you can give.

---

### Post by confused57 on 2007-11-13
This might be a better way to mount your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Here's an explanation for grub error 22:
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

You really need at least 5 Gb for a root partition, probably not your problem, but thought I'd mention it.

---

### Post by snakep on 2007-11-14
Well, the problem no longer exists.  I reinstalled Ubuntu, and this time I set up the partitions differently.  I made sure that I had 5 GB for /, and I created a partition for /boot.  It wouldn't let me create all four (swap, /, /boot, and /home) as primary partitions for some reason, so I made /boot and swap logical partitions.  

Overall, I felt that the installer was a little weak.  I didn't know what settings I should apply for the partitioning and there was no information or help.  The Suse installer at least gives a little bit of information about what different things do, and it has more options as well.  In the end, though, I'm up and running, so I guess that's all that matters.

---

