---
title: "Adding Ubuntu on another hard drive to grub?"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by hxczach on 2008-08-13
Hello

So a few days ago, i installed Fedora F9 onto my first hard drive, which has 2 partitions. Windows XP had been installed on it previously and everything went well. So last night i decided to install Ubuntu on my second hard drive (1 partition) and i would like to add it to the grub menu that was already installed with Fedora. I'm not sure what to put in terms of hdx's and root=/dev/...blah

And i installed Gutsy BTW

---

### Post by logos34 on 2008-08-13
If ubuntu root is on the first partition of the other drive, then try this entry in Fedora menu.lst:

> title Ubuntu 7.10
configfile (hd1,0)/boot/grub/menu.lst

---

### Post by hxczach on 2008-08-13
Well...
I can add&edit the menulist for grub within Fedora(because its bootable from the menu)
The problem im having is directing grub to the right disk and partiton of my ubuntu kernels.

---

### Post by logos34 on 2008-08-13
run this and post the output:

# [B]fdisk -l


[/B]

---

### Post by hxczach on 2008-08-14
Yeah, fdisk commands don't work in fedora for some reason?

---

### Post by Too Late on 2008-08-14
Did you try fdisk as root? First you need to type 'su' or something like that (don't know about Fedora).

---

### Post by logos34 on 2008-08-14
> **hxczach said:**
> Yeah, fdisk commands don't work in fedora for some reason?

login as administrator--the '#' is the universal symbol for 'run as root/with admin privileges'

---

### Post by hxczach on 2008-08-14
Here you are.
I had to boot with my old kernel for some reason.(weird)
lol





```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd355d355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8904    71521348+   7  HPFS/NTFS
/dev/sda2            8905        9729     6626812+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000216b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS

```

---

### Post by logos34 on 2008-08-15
uh, I don't see any linux/ubuntu partition on the other drive--or else the partition table is wrong and sdb1 is really an ext3 ubuntu /.  It says ntfs.  

Can you mount it in Fedora and see your ubuntu files?  And what does Gparted show?

If sdb1 realy is ubuntu, the entry I gave you above should work '(hd1,0)'.

You might run [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to fix the partition table.

---

### Post by hxczach on 2008-08-15
Yeah something went wrong when i formated for an install i think. Anyways, i decided to just dump fedora and install ubuntu on that partition (sda2). Thanks for your help though. 
And yes, i could mount that disk and view it in fedora. But grub didnt recognize the messed up file system format.

---

