---
title: "Executing 'grub-install (hd0)' failed"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by jerry_teps on 2008-03-04
Everytime I try to install Ubuntu I get this error when I get up to installing GRUB.

"Executing 'grub-install (hd0)' failed.

This is a fatal error."

I tried manually install GRUB by using root (hd0,0) | setup (hd0), but it doesn't work it gives an error saying it's not mounted or something, can someone please help?

---

### Post by zxscooby on 2008-03-04
check your bios to see if your HD is being detected properly , could be a loose cable , bad drive , etc.

---

### Post by DaV|d on 2008-03-04
Also check you have enough size in /boot (min. 40-50 MB)

---

### Post by jerry_teps on 2008-03-04
The install wont even start for GRUB, it's a laptop so I can't check for loose cables, how do I check /boot's size?

---

### Post by DaV|d on 2008-03-04
Actually, the size is only relevant if you set up /boot on a separate partition. If that's the case, just change the partition size while in the ubuntu installer. 

what do you mean:
> The install wont even start for GRUB?

---

### Post by Pumalite on 2008-03-04
Let's check your partitions. Boot your Ubuntu Live CD and from the Terminal, post:
sudo fdisk -lu

---

### Post by jerry_teps on 2008-03-04
> **DaV|d said:**
> Actually, the size is only relevant if you set up /boot on a separate partition. If that's the case, just change the partition size while in the ubuntu installer. 

what do you mean:
?

When it says installing GRUB in the Ubuntu installer it says it can't start or soemthing.


I'll check the partitions when I get home (at school)

---

### Post by Lord Grover on 2008-03-07
Same issue for me.
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS
/dev/sda2       102398310   312480314   105041002+   f  W95 Ext'd (LBA)
/dev/sda5       102398373   204796619    51199123+   7  HPFS/NTFS
/dev/sda6       204796683   205005464      104391   82  Linux swap / Solaris
/dev/sda7       205005528   312480314    53737393+  8e  Linux LVM

```

ETA: formatting as EXT2 made no difference.

---

### Post by Lord Grover on 2008-03-07
Exact error(s):
[B]Unable to install GRUB in (hd0)
Executing 'grub-install (hd0)' failed.
This is a fatal error.[/B]

---

### Post by falkaholic on 2008-03-11
I just got around the same problem.

Long story short, it doesn't matter about ext2 or ext3 etc.

I got mine to work by making a separate /boot partition.

---

