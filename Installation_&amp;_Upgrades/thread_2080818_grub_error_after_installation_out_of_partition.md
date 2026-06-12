---
title: "grub error after installation: out of partition"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by SkaarjZR on 2012-11-05
Hello.
I've installed Ubuntu on external hard drive, but after reboot I got error: level loop.
I reinstalled Ubuntu, but after that I get error: out of partition.

To boot from external HD, I enter to boot menu in BIOS and select boot from ext. HD. I'm trying to boot on my notebook Asus K50IE. Ubuntu successfully starts from this HD on my another PC, so it looks like HW related problem. I updated BIOS but it didn't help.
[Screenshot of error](http://savepic.su/2852297.jpg)
```

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000563cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   984432639   492215296   83  Linux
/dev/sdb2       984432640   992624639     4096000   82  Linux swap
/dev/sdb3       992624640  1953519615   480447488    7  HPFS/NTFS/exFAT

```
NTFS partition was added after installation. There is lilo installed on /dev/sda

I haven't found any helpful information :(

Do you have any clues? Do I need to post additional info?

---

### Post by darkod on 2012-11-05
If the same ext hdd boots OK on another PC, it seems the installation is good. Sometimes it might not be detecting the ext hdd fast enough to boot from it.

Or the grub2 and kernel files might have ended up too far into the disk. Some older boards have a limitation that they can't reach boot files beyond 137GB on the disk. I am not sure whether you might be affected by this.

If this is the problem, the solution would be to make a new installation this time with a small 500MB or 1GB /boot partition at the start of the disk. That way you are sure that the boot files will always be at the start.

You can view all details including the position of the boot files in the bootinfo that boot-repair can create for you.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by SkaarjZR on 2012-11-07
Thank you, darkod!
Boot Repair told me the same about /boot partition
So I created it using gparted. Although Ubuntu booted from CD didn't wake up during moving partition. Thank god no changes were applied. I used gparted livecd.
And now I can boot into Ubuntu from external drive on my notebook!

---

