---
title: "Installation doesn't see windows and partitions"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by bznein on 2010-10-18
Hi all,

I have this strange problem I couldn't find anywhere. I'm trying to install Ubuntu 10.10 on my Ubuntu 10.04 (not upgrading, new installation).

I actually have a 320gb HDD with Windows 7 on one partition and Ubuntu 10.04 on another one (plus the Swap partition) but when I reach the point  in which I have to decide the device where to install it, it shows me only two options:

Erase and use entire disk
or
Specify partitions manually

If I choose the second one, I got a window where I can only see one partition (/dev/sda) of 320gb (which is my entire disk) and no sign of Windows 7 or the old Ubuntu version.

How can I make the installation see them? I add that I can see them while using the "live" Ubuntu from the CD. 

Sorry for my baaaaaad english :) and thanks in advance

---

### Post by Mark Phelps on 2010-10-18
Did your system come preinstalled with Win7?

Asking because OEMs, all to often, allocate several partitions to a drive with preinstalled Win7, leaving little flexibility for installing another OS.

So, if you have (1) Win7 Boot partition, (2) Win7 OS partition, (3) Linux root partition, and (4) Linux swap partition -- and they are all primary partitions -- then you have no way of creating any more of them because four is all you're allowed to have.

To see what you have, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  Post the results back here.

---

### Post by bznein on 2010-10-18
Sorry, maybe I explained bad.

I want to overwrite my old Ubuntu insallation (as I did before, so I know it's possible) replacin it with the new (but not doing the upgrade, that due to some reason you probably don't want to hear :D)

here's anyway the output:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   619898880   625139711     2620416    c  W95 FAT32 (LBA)
/dev/sda2          241664    21213183    10485760    7  HPFS/NTFS
/dev/sda3   *    21213184   342004199   160395508    7  HPFS/NTFS
/dev/sda4       342007846   625139711   141565933    f  W95 Ext'd (LBA)
/dev/sda5       619898880   625139711     2620416   dd  Unknown
/dev/sda6       342007848   608526134   133259143+  83  Linux
/dev/sda7       608526198   619884089     5678946   82  Linux swap / Solaris

Partition table entries are not in disk order
```


All I want is to install Ubuntu 10.10 over sda6 (the old installation) but the installer seems unable to see all this partitions

---

### Post by oldfred on 2010-10-18
You should be able to use manual install just as you have tried.

I have had issues with gparted not seeing a drive because the NTFS partition needed chkdsk. It would not even see my sda drive at all, I could boot XP on sda1 without obvious errors, but after running check disk it worked in gparted.

You also have two boot flags. Windows can only boot with one boot flag on one primary partition. I would remove the boot flag from sda1 with gparted from the liveCD. There is a slight possibility that that is what is causing the problem.

---

### Post by srs5694 on 2010-10-18
Your /dev/sda1 and /dev/sda5 overlap -- in fact, they describe the exact same space on the disk. This is a very bad problem with the partition table. Fortunately, it's easily corrected: Delete /dev/sda1 by using the "d" command in fdisk. The only question is whether it should really be type 0x0c (as /dev/sda1 is) or 0xdd (as /dev/sda5 is). My hunch is it should be 0x0c, since 0xdd is an obscure type code (reported as "Unknown" by fdisk). If you concur, you should change the type code using the "t" command in fdisk. Once you've finished with your changes, type "w" to save them to disk.

---

