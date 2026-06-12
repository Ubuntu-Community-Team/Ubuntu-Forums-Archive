---
title: "RAID 1 Bootloader Problem"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by root45 on 2011-05-15
Hi,

I'm attempting to install Ubuntu 11.04 on a two-disk RAID 1 setup. I've started with two independent, blank disks.

I basically followed the instructions here

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

which have worked pretty well, but I'm having an issue when it comes to installing GRUB. The installer asks me if I want to install it on the first disk. If I say yes, it returns a "Fatal Error" saying that it couldn't be installed.

I've tried entering things like /dev/md0 and /dev/md1, but it gives the same error.

I've looked at this thread

[http://ubuntuforums.org/showthread.php?t=1559762](http://ubuntuforums.org/showthread.php?t=1559762)

and tried doing

```
ls /dev/mapper
```to see which partition I should install the bootloader to, but nothing comes up except "control". I also tried booting from the Live CD to try and install GRUB that way, but I can't mount any of the partitions. There's an error about them being RAID partitions.

So basically, I have two drives sdb and sdc each with three partitions, sdb2 and sdc2 are RAIDed as the root filesystem, sdb3 and sdc3 are RAIDed as swap. This means there are three RAID devices, md0, md1 and md2 where md0 corresponds to sdb1 and sdc1 and so on.

And I just need to know how to install GRUB 2 onto this setup. I should also note that Windows 7 is installed on sda, so I'd like to have access to that at boot time as well.

Thanks for any help.

---

### Post by quaeritate on 2011-05-21
You need to point it to one of the physical drives such as /dev/sda

---

### Post by root45 on 2011-05-21
Oh, I should reply to say that I actually solved this problem eventually. I was using out of date information, sort of. My drives were 2 TB, which means they used GPT instead of the regular partition table. What this means is that I needed to create a BIOS boot partition on each device and mark it for GRUB boot, and NOT raid those partition together. Then just install GRUB on /dev/sda /dev/sdb (it should automatically do this).

---

