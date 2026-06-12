---
title: "New Install 9.10, single boot, Can't get grub to load!"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by helix on 2009-12-30
Hey folks, clean install of 9.10, single boot, won't load grub.

Heres my fdisk output
```
root@ubuntu:/home/ubuntu# fdisk -ls

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x012625a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e6d254f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9324    74894998+  83  Linux
/dev/sdb2            9325        9726     3229065    5  Extended
/dev/sdb5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbdd9bdd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      182401  1465136001    7  HPFS/NTFS

```

Then I get this as I try to install grub2
```

root@ubuntu:/home/ubuntu# mount /dev/sdb1 /mnt
root@ubuntu:/home/ubuntu# grub-install --root-directory=/mnt/ /dev/sdb1
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

```


Please guide me in the right direction, I'm sure its something stupid I'm doing. Thanks!

---

### Post by yelvington on 2009-12-30
You're trying to install the bootloader to a partition, instead of a physical drive, and Grub is telling you not to do that.

You can install grub to /dev/sdb (not sdb1). To boot Linux you'll have to instruct your computer to boot from the second hard disk (probably by changing the preferred boot order in BIOS, or by hitting a function key at boot time).

Your reference to "single boot" is puzzling, though, as you clearly have two other disks formatted for Windows.

---

### Post by helix on 2009-12-30
> **yelvington said:**
> You're trying to install the bootloader to a partition, instead of a physical drive, and Grub is telling you not to do that.

You can install grub to /dev/sdb (not sdb1). To boot Linux you'll have to instruct your computer to boot from the second hard disk (probably by changing the preferred boot order in BIOS, or by hitting a function key at boot time).

Your reference to "single boot" is puzzling, though, as you clearly have two other disks formatted for Windows.

Thanks for the reply, I understand what I did wrong now.

Yes, those two drives are NTFS, however I don't have a Windows partition, nor am I planning on installing Windows at all. They are left over from my previous instillation.
```
root@ubuntu:/home/ubuntu# grub-install --root-directory=/mnt/ /dev/sdb
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
root@ubuntu:/home/ubuntu# 

```

---

