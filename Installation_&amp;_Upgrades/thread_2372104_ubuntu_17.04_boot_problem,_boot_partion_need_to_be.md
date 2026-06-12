---
title: "ubuntu 17.04 boot problem, boot partion need to be recovered on every boot"
date: 2017-09-21
forum: Installation &amp; Upgrades
---

### Post by avi99 on 2017-09-21
The normal boot waiting for boot partition check to be finished, and hangs.
Only going to recovery mode and run fsck on all file system solves the issue till the system is restarted next time.

on running fsck some error displayed "/lib/recovery-mode/recovery-menu line 75 /etc/default/rdS no such file or directory"

The on resume, the system boots normally

Again

$ sudo fdisk -l
```
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x621c7d4c

Device     Boot     Start        End    Sectors   Size Id Type
/dev/sda1  *         2048     206847     204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848  419637247  419430400   200G  7 HPFS/NTFS/exFAT
/dev/sda3       419637248  461580287   41943040    20G  7 HPFS/NTFS/exFAT
/dev/sda4       461582334 1953523711 1491941378 711.4G  5 Extended
/dev/sda5       461582336  462557183     974848   476M 83 Linux
/dev/sda6       462559232  478181375   15622144   7.5G 82 Linux swap / Solaris
/dev/sda7       478183424 1953523711 1475340288 703.5G 83 Linux

Partition 4 does not start on physical sector boundary.
```

--> sda5 is boot partition

--> any pointers

Thanks a lot

Avi

---

### Post by ajgreeny on 2017-09-21
Start a live Ubuntu system using the DVD or USB you used for installation of the OS then run command ```
sudo e2fsck /dev/sda7
``` this assumes sda7 is your root partition which it appears to be according to the fdisk output; it may do a more complete filesystem check and offer you the option to repair.

If that still does not solve the problem and you still get errors shown at boot run it again on sda5 which I think must probably be a separate /boot partition of 476Mb.

There is, incidentally, little point in having a separate /boot partition in a standard desktop Ubuntu OS unless you are using encryption or LVM partitioning which you do not seem to be using, so next time you install I suggest you avoid using separate /boot partition.

---

### Post by avi99 on 2017-09-22
Thanks a lot for the reply.

the e2fsck output for both sda5 and sda7 are clean ..

Still the problem persists.

One more issue, /boot partition if full with old kernel images .. 

About not having separate /bot partition  -- > if boot partition isn't separate, we have to deal with 100 gb / partition instead of 500 mb /boot partition

Thanks again

---

### Post by avi99 on 2017-09-22
[IMG]https://www.imageupload.co.uk/images/2017/09/22/IMG_20170922_104229.jpg[/IMG]
This is howthe system is stuck after normal boot. I have to manually restart after this.
[https://www.imageupload.co.uk/image/DSxE](https://www.imageupload.co.uk/image/DSxE)

---

### Post by ajgreeny on 2017-09-22
> **avi99 said:**
> Thanks a lot for the reply.

the e2fsck output for both sda5 and sda7 are clean ..

Still the problem persists.

One more issue, /boot partition if full with old kernel images .. 

About not having separate /bot partition  -- > [COLOR="#FF0000"]if boot partition isn't separate, we have to deal with 100 gb / partition instead of 500 mb /boot partition[/COLOR]

Thanks again
Normally when /boot is simply a folder in the root partition we do not have to "deal with" it at all as there is nothing to do, and it is not likely to fill up causing the problems that may be at the root of your difficulty booting.

Let's see what your current situation is from command ```
dpkg -l linux-image* linux-headers*
``` then we can try to remove the unneeded versions.  Have you attempted command ```
sudo apt autoremove
``` which might work, though if your /boot partition is full is likely not to do what is should, ie remove all but the last two kernel versions.

---

### Post by avi99 on 2017-09-27
Some additional Info.

I tried installing Manjaro linux, and its booting normally . Only a warning about "Superblock last write time is in the future. (by less than a day, probably due to the hardware clock being incorrectly set) " 

But tried both ubuntu 17.04 and 16.04.3. Not going beyond that point like in that picture

[IMG]https://www.imageupload.co.uk/image/DNam[/IMG]

[https://www.imageupload.co.uk/image/DNam](https://www.imageupload.co.uk/image/DNam)

Thanks

---

