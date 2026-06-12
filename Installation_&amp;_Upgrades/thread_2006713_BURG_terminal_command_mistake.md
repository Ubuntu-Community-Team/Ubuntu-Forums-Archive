---
title: "BURG terminal command mistake"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by sks24 on 2012-06-19
I, uh, copied the command "sudo burg-install "(hd0)" from [here]("http://www.unixmen.com/how-to-install-burg-in-ubuntu/") but forgot to substitute the correct disk for the MBR before I hit "Enter."  "sudo fdisk -l" result below:

```
ronald@ronald-OptiPlex-GX620:~$ sudo burg-install "(hd0)"
Installation finished. No error reported.
ronald@ronald-OptiPlex-GX620:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7a994666

   Device Boot  	Start     	End  	Blocks   Id  System
/dev/sda1   *    	2048  	411647  	204800	7  HPFS/NTFS/exFAT
/dev/sda2      	411648   132632639	66110496	7  HPFS/NTFS/exFAT
/dev/sda3   	132634622   156248063	11806721	5  Extended
/dev/sda5   	132634624   152076287 	9720832   83  Linux
/dev/sda6   	152078336   156248063 	2084864   82  Linux swap / Solaris
ronald@ronald-OptiPlex-GX620:~$
```

Can I continue safely with "sudo update-burg"?  Should I re-issue:
```
sudo burg-install "(hd0)"
```

If so, what should I say instead of "(hd0)">?

This is a 12.04 32 bit installation alongside Win7

Thanks in advance, 
Scott

---

### Post by wilee-nilee on 2012-06-19
The command is
```
sudo burg-install /dev/sda
```
Then
```
sudo update-burg
```

---

### Post by sks24 on 2012-06-19
Workidid lika charm, wilee-nilee!  Thanks!

---

### Post by wilee-nilee on 2012-06-19
> **sks24 said:**
> Workidid lika charm, wilee-nilee!  Thanks!

No problem, notice with grub 2 partitions are sdX and sdXX, and some times is preceded by a /dev.

Burg is actually grub 2 with added visual stuff, or at least one of the grub 2 releases.

---

### Post by sks24 on 2012-06-19
Noted, & thanks again,
S

---

