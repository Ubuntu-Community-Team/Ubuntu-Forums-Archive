---
title: "GRUB not showing ubuntu install after upgrade."
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by Dyamalos on 2010-12-06
At first I thought it was a fluke, but it happed on another computer I was a bit late in updating.

I'm running 10.04 lucid 32 bit on both computers.

After running the update, everything ran fine. The script ran update-grub and everything seemed ok. However when I rebooted, my laptop booted into GRUB and only showed windows and the recovory partition. Desktop would boot strait into windows with no selection (I knew how to fix it for the desktop since it happed a few days later)

When it first happend on my laptop, I scrounged around trying to repair the OS list, but nothing worked. Eventualy running "grub-install" with the  "--root-directory" option on a live CD fixed it.

I'm not sure what is causing the problem, but I think I remember there being an update to GRUB when I ran the updater. The fix works, just a bit of a hassle, but I thought I would bring it to someone's attention in case it happens to them.

Hopefully it won't happen again.

---

### Post by Quackers on 2010-12-06
Welcome to UF :-)
Thanks for the info.
Can you confirm whether you have a wubi install or a true dual boot system (2 or more operating systems on separate partitions)?
Thanks.

---

### Post by Dyamalos on 2010-12-07
It's dual boot. Both computers came pre-installed with vista and a recovery partition. I assume something was changed in grub with the last update and it needed to be reinstalled to work.


Here is the fdisk list output of my laptop:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f989a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10158    81594103+   7  HPFS/NTFS
/dev/sda2           17930       19457    12266496    7  HPFS/NTFS
/dev/sda3           10159       10289     1052257+  82  Linux swap / Solaris
/dev/sda4           10290       17929    61368269+   5  Extended
/dev/sda5           10290       10313      192748+  83  Linux
/dev/sda6           10314       13960    29294496   83  Linux
/dev/sda7           13961       17929    31880961   83  Linux

Partition table entries are not in disk order

```

I have a remote computer with some family that doesn't have windows, only Ubuntu 10.04. I updated it though SSH and it seems to be working. I think this problem only effects dual boots, but I can't remember if I reinstalled grub before restarting that PC as a precaution.

---

