---
title: "NTFS Drives disappeared"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by Auzern on 2010-06-13
After upgrading from Ubuntu 9.10 to Ubuntu 10.04, my NTFS drives have disappeared. Even the Disk Utility doesn't seem to work.
What do I do? All my important files are in my NTFS Drives.:confused:

---

### Post by darkod on 2010-06-13
Just the auto mounting has disappeared? If you run in terminal:

sudo fdisk -l

does it show all disks?

---

### Post by Auzern on 2010-06-13
Thanks for your reply, darkod.
I guess this is what it shows:
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0e7b0e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9728    62782020    f  W95 Ext'd (LBA)
/dev/sda5            1913        4462    20482843+   7  HPFS/NTFS
/dev/sda6            4463        7012    20482843+   7  HPFS/NTFS
/dev/sda7            7013        8924    15358108+  83  Linux
/dev/sda8            8925        9728     6458098+  82  Linux swap / Solaris

I think sda1,2,5,6 are my NTFS Drives.
How do I get them back?

---

### Post by darkod on 2010-06-13
If you look in Places, will they be shown? It would say like 10GB filesystem, or similar.

If they do show, try clicking on one and it should mount it. Then you can look inside.

If that works, most probably all is fine, it just depends how you were used to access them, maybe the mount command is broken.

---

### Post by Auzern on 2010-06-13
Whoa! I can access them now. Thanks a lot!! It seems to work. I just hope it doesn't disappear again.

---

### Post by darkod on 2010-06-13
When you restart they don't stay mounted. :)

You can do the same if you need to access them. In fact I don't auto mount ntfs partitions except if you really need to access them all the time. It keeps them safe from deleting anything by mistake.

---

### Post by Auzern on 2010-06-13
I agree. Like this its more secure.
Thanks again :D

---

