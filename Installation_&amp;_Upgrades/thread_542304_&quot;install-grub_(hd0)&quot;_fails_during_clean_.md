---
title: "&quot;install-grub (hd0)&quot; fails during clean Feisty install"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by merlin114 on 2007-09-03
I've tried twice now to do a clean install of Feisty to a 40GB partition, separate from my existing Dapper setup.  I did Manual partitioning, allocating 37GB for an ext3 partition mounted at "/", and 3GB for swap (sdb5 and 6 respectively).  Each time, the install went great until 94%, and then I get the error "Executing 'grub-install' (hd0) failed.  This is a fatal error."  I checked the live CD and it reported no errors.  I haven't seen this in the threads.  Anyone have an ideas?

---

### Post by Pumalite on 2007-09-03
If you have appropriate hardware, I would check the iso with an md5sum, burn at 4x, and check for corruption of CD before install. Why don't you post: sudo fdisk -lu ?

---

### Post by merlin114 on 2007-09-03
Thanks.  I just did md5sum on the iso and the hash is correct.  Now I'll reburn the CD at 4x and check it using the option at bootup.  Here's the results of fdisk.  That's kind of odd.  hda is my 2nd hard drive, with only Dapper on it.  hdb has half for WinXP (hdb2), and the other half was where I tried to install Feisty (hdb5), and was also formatted NTFS from before.  I did check the format box during partitioning, and allocated a 3GB partition for swap (hdb6).  So I wonder why hdb5 is still showing NTFS?  Any suggestions while I'm reburning the CD at 4x?

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    76662179    38331058+  83  Linux
/dev/hda2        76662180    78156224      747022+   5  Extended
/dev/hda5        76662243    78156224      746991   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    78156224    39078081    7  HPFS/NTFS
/dev/hdb2        78156225   156296384    39070080    f  W95 Ext'd (LBA)
/dev/hdb5        78156288   150432659    36138186    7  HPFS/NTFS
/dev/hdb6       150432723   156296384     2931831   82  Linux swap / Solaris

---

### Post by Pumalite on 2007-09-03
Something is very wrong. Whatever you tried to install in sdb didn't work and you ended up with only a swap partition. Is for you to decide now.

---

### Post by merlin114 on 2007-09-04
Thanks again.  I used 'gparted' to look at the partitions and found that, like you said, I only had extended partitions.  For us newbies, it isn't that clear exactly how the partitions need to be laid out for linux, so when I did it manually, I was kind of flying blind.  Although, I did try to mimic how the partitions were on my Dapper drive.  

Anyway, I was able to use gparted to deleted those partitions (leaving my WinXP NTFS one intact), and then create one 'ext3' partition 38GB, and a 3GB extended/swap partition. Tonight I'll try installing Feisty again and see how it goes. 

For any other newbies out there, if you have to re-parition manually during a clean install the notes aren't that clear on what you have to do.  But it seems that you need to make one main partition in 'ext3' format, and then a smaller 'swap' partition.  You can do this very easy using 'gparted' which you can get via the synaptic package manager.  Then in a terminal you just type 'sudo gparted', and a very user-friendly gui pops up.  It's very simple to right-click and make a main 'ext3' partition.  Then you make a smaller (1-3GB) 'extended' partition, and it will put a little triangle next to it.  Click the triangle and you can make a sub-partition, as a 'linux-swap'.  Clearly, messing with partitions should be done with GREAT CARE  so you don't wipe out good data.  

Any experts, please correct me if I said something incorrect.  Note that this is the level of detail us newbies generally need, since we don't know these basics.

---

