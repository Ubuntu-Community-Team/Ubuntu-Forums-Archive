---
title: "Installation Causes Windows not to be found"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by scastle on 2007-09-14
Using Gutsy Tribe 5
Dell Inspiron 600m Laptop
40GB hard drive

Was running Windows XP Pro
Set up the partition manager to dual boot, giving ubuntu 22GB and Windows the rest.

Windows was using 9GB at the time.

When I run:
fdisk -l
I get:
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa287a287

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2               5        2748    22041180    7  HPFS/NTFS
/dev/sda3   *        2749        4770    16241715   83  Linux
/dev/sda4            4771        4864      755055    5  Extended
/dev/sda5            4771        4864      755023+  82  Linux swap / Solaris

```

The Windows partition should still be there, and I am thinking that it is the HPFS/NTFS partition (sda2), but it is not showing up in GRUB.

Is there something that I am missing?

Help would be greatly appreciated.

EDIT:
When I go into gparted and look at the partitions, I get a popup that says:
```
"Cannot Mount Volume"
Unable to mount the volume

Details:
Volume is scheduled for check.  PLease boot into WIndows TWICE, or use the 'force' mount option.  For example, type on the command line:
mount -t ntfs-3g /dev/sda2 /media/disk -o force
Or add the option to the relevant row in the /etc/fstab file:
/dev/sda2 /media/disk ntfs-3g defaults,force 0 0
```

I see that it is giving me instructions, but I don't want to screw anything up.  I have backed up my data that was on the Windows partition, but I'd like to keep the installation there if possible.

It'd be great if someone that knows what this is about and can give step by step instructions. :)

---

### Post by ddrichardson on 2007-09-15
This is quite common and is the reason a defrag is recommended before resizing. There are ntfs tools for Linux that may help - [ntfsfix]("http://packages.ubuntu.com/feisty/otherosfs/ntfsprogs").

If grub hasn't picked it up you'll need to manually add the entry to grub.lst

---

