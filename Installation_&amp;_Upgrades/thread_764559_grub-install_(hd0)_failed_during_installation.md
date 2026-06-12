---
title: "grub-install (hd0) failed during installation"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by sanjeevan on 2008-04-24
i know many threads exists but none helped. i came across that error during installation. i tried fixing using livecd but the find /boot/grub/stage1 says file not found and its not there too.

i have a 1.3 gb partition that i dont know that is used for, i cant get rid  of it or ubuntu doesn't work. then i have 130gb for xp, 30gb free ntsf, and 30gb for ubuntu ext3. i have no swap partion since i dont one.

output for fdisk -l is 

```
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> quit
quit
root@ubuntu:/boot# fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc9d9739

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       17281   137270272    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           17281       20800    28262400    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4           20800       24322    28290048    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           17281       20800    28261376    7  HPFS/NTFS

Disk /dev/sdb: 4103 MB, 4103937024 bytes
255 heads, 63 sectors/track, 498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46784677

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         497     3992135+   b  W95 FAT32
root@ubuntu:/boot# 


```

---

### Post by Creptic on 2008-04-24
Had same problem. Disconnect from the internet during install, Then update after installed.

---

### Post by BoredSilly on 2008-04-24
Had the same problem to. In the install right at the end when it gives a summary of whats going to happen there's an advanced button on the bottom right of the window. Click that and you can manually configure the grub boot options. By default it's trying to install on hd0 and your fdisk output tells me you're using sata drives so set it to sda1 and you might be in business. Then again it may just wipe everything ... who knows!

---

### Post by dstew on 2008-04-24
I don't see any ext3 filesystem on your fdisk output. I don't think you have an installed Ubuntu system, so installing grub failed. You have to install Ubuntu before you install grub.

---

### Post by Hub-1 on 2008-04-24
Same here with ubuntu 8.04 Hardy Heron. Grub installation failed. How embarrassing to start an LTS release with a bug like this.

---

### Post by sanjeevan on 2008-04-24
> **Creptic said:**
> Had same problem. Disconnect from the internet during install, Then update after installed.

i have internet connection.

> **BoredSilly said:**
> Had the same problem to. In the install right at the end when it gives a summary of whats going to happen there's an advanced button on the bottom right of the window. Click that and you can manually configure the grub boot options. By default it's trying to install on hd0 and your fdisk output tells me you're using sata drives so set it to sda1 and you might be in business. Then again it may just wipe everything ... who knows!

but i have done this tons of time before. i mean installing in this laptop.


> **dstew said:**
> I don't see any ext3 filesystem on your fdisk output. I don't think you have an installed Ubuntu system, so installing grub failed. You have to install Ubuntu before you install grub.
but i chose to partition it as an ext3 with / as the mountpoint.

---

### Post by amartz on 2008-05-07
I just had a similar problem. I have 4 partitions on the second drive of an HP Pavilion dv9740, /, swap, /usr and /home, all ext3 (not swap, of course).  I was running the gnome partition manager from the 8.04 Ubuntu dvd, and telling it to format / and /usr, not /home, and do the install. This disk had 7.10 on it. I'd get the grub-install failed near the end of the install.  Following a tip from another thread, I ran fdisk -l.  The /usr and /home partition types IDed as type 83 (ext3), but the / partition as something else.  Even though I was telling the partition manager it was ext3 (type 83) and to format it, it didn't change the type to ext3, so grub-install failed (even though the mbr was on the other drive).  Since I was formatting the / partition anyhow, I deleted the partition, and then re-created it as ext3, told it to format and install, and the grub-install worked fine.
Art

---

