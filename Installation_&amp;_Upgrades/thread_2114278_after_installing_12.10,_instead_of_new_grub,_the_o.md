---
title: "after installing 12.10, instead of new grub, the old grub loads"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by finalni on 2013-02-09
I have ubuntu 10.04 and Win7 on one hard drive. I installed ubuntu 12.10 on second hard drive, everything seemed fine (it asked me to install alongside old OSs), installation completed and asked me to restart.
Even though 12.10 got installed, when booting, the old grub (with options only for old OSs) appears, so I can't boot to new ubuntu. I've tried changing the boot device to the second hard drive, but then only a message "not bootable drive" or sth like that appears, no grub.

Any ideas where did new grub go to? :D
Can grub load from different hard drives?



Just in case, here's the output of fdisk-l (just to see the mess there is:)
sudo fdisk -l

Disk /dev/sda: 82.0 GB, 81964302336 bytes
252 heads, 39 sectors/track, 16288 cylinders
Units = cylinders of 9828 * 512 = 5031936 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce0d07d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1224     6008832   83  Linux
/dev/sda2            1224        1290      326656   82  Linux swap / Solaris
/dev/sda3   *        2412        6552    20346322+   7  HPFS/NTFS
/dev/sda4            6553       16288    47842704    f  W95 Ext'd (LBA)
/dev/sda5            6553       16288    47842684+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00032ddc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       76525   614680538    b  W95 FAT32
/dev/sdb2           76525      121602   362080257    5  Extended
/dev/sdb5           76525      100535   192862423   83  Linux
/dev/sdb6          121133      121602     3761152   82  Linux swap / Solaris
/dev/sdb7          100535      121132   165447680   83  Linux

Partition table entries are not in disk order

---

### Post by darkod on 2013-02-09
I have noticed that sometimes the 12.10 installer doesn't seem to install grub2 to the MBR as it should.

Do you know which one of those partitions is the 12.10 root?

---

### Post by dabl on 2013-02-09
Disclaimer: Fiddling with grub always includes the risk of creating a (temporarily) unbootable computer.  Fair warning.

Assuming you have the 12.10 repos set in /etc/apt/:

```
sudo apt-get update && sudo apt-get install --reinstall grub-pc
```

There may be a debconf screen inviting you to "x" the applicable drive or partition where you want it.  Be careful on that one -- use the Tab key and spacebar to place the "x" where you need it, then tab to "OK".

---

### Post by finalni on 2013-02-09
> **darkod said:**
> I have noticed that sometimes the 12.10 installer doesn't seem to install grub2 to the MBR as it should.

Do you know which one of those partitions is the 12.10 root?

It seems that /dev/sdb7 got a label/"mount point" 641a0d79-9d9f-4eb8-afeb-0fb3085682ac, which contains bin, boot and other folders of 12.10, so I guess that should be the root partition..?

@dabl, 12.10 sources.list and co. are in /media/641a0d79-9d9f-4eb8-afeb-0fb3085682ac/etc/apt.. perhaps I should run ubuntu 12.10 from DVD ("try ubuntu") and then run this (or some similar) commands?

---

### Post by darkod on 2013-02-09
OK, if sdb7 is the root, from live mode do:
```
sudo mount /dev/sdb7 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

That should put grub on the MBR of sdb. Try to boot from it as first option and see how it goes.

---

### Post by dabl on 2013-02-09
Yes, try darkod's suggestion.  If it doesn't work, then you'll need to boot a Live CD and chroot into the 12.10 installation, and once your are in, run:

```
sudo apt-get update && sudo apt-get install --reinstall grub-pc
```.

Here are chroot instructions:

[http://basictheprogram.blogspot.com/2011/02/how-to-chroot-simple-and-fast-archive.html](http://basictheprogram.blogspot.com/2011/02/how-to-chroot-simple-and-fast-archive.html)

---

### Post by darkod on 2013-02-09
> **dabl said:**
> Yes, try darkod's suggestion.  If it doesn't work, then you'll need to boot a Live CD and chroot into the 12.10 installation, and once your are in, run:

```
sudo apt-get update && sudo apt-get install --reinstall grub-pc
```.

Here are chroot instructions:

[http://basictheprogram.blogspot.com/2011/02/how-to-chroot-simple-and-fast-archive.html](http://basictheprogram.blogspot.com/2011/02/how-to-chroot-simple-and-fast-archive.html)

Slight correction, you don't need sudo in front when inside chroot. It will report an error I think.

---

### Post by finalni on 2013-02-09
> **darkod said:**
> OK, if sdb7 is the root, from live mode do:
```
sudo mount /dev/sdb7 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

That should put grub on the MBR of sdb. Try to boot from it as first option and see how it goes.

Thanks, this worked :)

Now I just need to find some drivers for 10 years old graphic card to get passed the blank desktop :S
Really should buy new computer instead of constantly upgrading this one :S

---

