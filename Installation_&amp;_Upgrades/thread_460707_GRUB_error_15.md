---
title: "GRUB error 15"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by davidgq on 2007-05-31
Ive been trying all day to get ubuntu installed but every time i came across new problems. the latest is the Grub error 15. from what ive read i could be just a few terminal commands away from having a bootable installation.

But, i cant make sense of any of the explanations ive seen. if someone could walk me through the process it would greatly appreciated. Thanks in advance

---

### Post by benner on 2007-06-01
are you dual booting?  do you have more than one hard disk?

---

### Post by davidgq on 2007-06-01
i am dual booting and on 2 hard drives. im trying to do it without getting into the MBR

---

### Post by benner on 2007-06-01
i'm pretty sure you will need to edit your grub.  if you can't get into your system at all, put in the live cd, then locate the drive where it is installed and go to the folder called 'boot' and in there is the grub file.  sorry, i'm not in front of a ubuntu machine right now but if you di around you will find it.  edit the grub as root and make sure that it is looking on the right drive to find your linux kernel.  (i have a million partitions so if i can't remember what they are called--sda1, hdb1 etc... i usually open the partition editor to check, there is probably a much smarter way)

a few times when i downloaded updates, i got the same error and had to re-edit grub.  good luck

---

### Post by davidgq on 2007-06-01
maybe i don't know what i'm doing. As far as I can tell everything is pointing in the right direction.

---

### Post by merlinus on 2007-06-01
Can you post the contents of /boot/grub/menu.lst

Also

sudo fdisk -l

and

blkid

This may give some helpful info.

-merlin

---

### Post by davidgq on 2007-06-01
menu.lst
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=12c19f12-80b0-4d05-b6c0-47779341c943 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=12c19f12-80b0-4d05-b6c0-47779341c943 ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/memtest86+.bin
quiet

```

fdisk

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2089    16779861    c  W95 FAT32 (LBA)
/dev/sda2            2090        9729    61368300    f  W95 Ext'd (LBA)
/dev/sda5            2090        9729    61368268+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391   83  Linux
/dev/sdb2              14          14        8032+  82  Linux swap / Solaris
/dev/sdb3              15        7663    61440592+  83  Linux
/dev/sdb4            7664       60801   426830985    b  W95 FAT32
ubuntu@ubuntu:~$ 

```

blkid

```
/dev/sda1: UUID="1052-B046" TYPE="vfat" 
/dev/sda5: TYPE="ntfs" 
/dev/sdb1: UUID="941918c9-1f45-4e9b-bf92-2120cbe2b3a8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="ff229114-8520-42bf-9069-92447e9ca0d7" TYPE="swap" 
/dev/sdb3: UUID="12c19f12-80b0-4d05-b6c0-47779341c943" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: UUID="4660-2C44" TYPE="vfat" 
ubuntu@ubuntu:~$ 

```

---

### Post by confused57 on 2007-06-01
If you're booting first to your Ubuntu drive, your root needs to be (hd0,0)...if this is the case & you have grub installed to the Ubuntu drive mbr, highlight your Ubuntu entry, press "e", then change root to (hd0,0), then press "b" to boot...if it works, this is temporary, but can be made permanent in /boot/grub/menu.lst.

---

