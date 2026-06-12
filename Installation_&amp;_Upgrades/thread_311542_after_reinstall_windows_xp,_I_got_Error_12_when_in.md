---
title: "after reinstall windows xp, I got Error 12 when installing grub into MBR"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by vincent_wang on 2006-12-03
Currently I use Ubuntu 6.04. After I reinstall windows xp, I can not install grub to MBR, it gave me Error 12(more details later) all the time, what's going wrong? Please give me your help! Thanks in advance!

DETAILS: 
```

15:12 root@sysresccd /root % fdisk -l 
omitting empty partition (5)

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+   c  W95 FAT32 (LBA)
/dev/hda2            1217        9729    68380672+   f  W95 Ext'd (LBA)
/dev/hda3            3649        5472    14651248+   b  W95 FAT32
/dev/hda5            1217        1313      779089+  82  Linux swap / Solaris
/dev/hda6   *        1314        3555    18008833+  83  Linux
/dev/hda7            3556        3648      746991   82  Linux swap / Solaris
/dev/hda8            5473        9729    34194321    b  W95 FAT32

15:13 root@sysresccd /root % grub 
grub> root (hd0,6)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,6)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

grub> 


```

---

### Post by ciscosurfer on 2006-12-03
This link should help you out: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by vincent_wang on 2006-12-03
After I  tried the method in the above link, the error is still the same. :(
  Any ideas?

---

### Post by glyph on 2006-12-03
> **vincent_wang said:**
> Currently I use Ubuntu 6.04. After I reinstall windows xp, I can not install grub to MBR, it gave me Error 12(more details later) all the time, what's going wrong? Please give me your help! Thanks in advance!


Your problem seems to be a numbering issue.  Grub and Linux (and fdisk) do not use the same numbering scheme for disks or partitions: Grub starts at 0 and 0, linux starts at "a" and 1, respectively.

However, your debug output does not seem consistent, so I might be mis-interpreting.  Are you sure you pasted correctly?

> DETAILS: ```

/dev/hda6   *        1314        3555    18008833+  83  Linux
```
This is your actual root partition, I assume.
> ```
/dev/hda7            3556        3648      746991   82  Linux swap / Solaris
```
and that is what grub is seeing as "(hd0,6)".  Which is why I'm surprised to see this:

> ```
grub> root (hd0,6)
 Filesystem type is ext2fs, partition type 0x83
```
I *think* what you should be doing here instead is
```
grub> root (hd0,5)
```
But when I do what you did (specify a swap partition), I see
```
 Filesystem type unknown, partition type 0x82
```
which is why I ask if I'm sure you copied your rescue-CD session correctly.

Most likely changing (hd0,6) to (hd0,5) will fix your problem, though.

---

### Post by ciscosurfer on 2006-12-03
> **glyph said:**
> Your problem seems to be a numbering issue.  Grub and Linux (and fdisk) do not use the same numbering scheme for disks or partitions: Grub starts at 0 and 0, linux starts at "a" and 1, respectively.

However, your debug output does not seem consistent, so I might be mis-interpreting.  Are you sure you pasted correctly?


This is your actual root partition, I assume.

and that is what grub is seeing as "(hd0,6)".  Which is why I'm surprised to see this:


I *think* what you should be doing here instead is
```
grub> root (hd0,5)
```But when I do what you did (specify a swap partition), I see
```
 Filesystem type unknown, partition type 0x82
```which is why I ask if I'm sure you copied your rescue-CD session correctly.

Most likely changing (hd0,6) to (hd0,5) will fix your problem, though.Agreed.

---

### Post by vincent_wang on 2006-12-04
Thanks for your answer! 

I am pretty sure all the output, from both fdisk and grub is real. 
I just tried to use (hd0,5), but it does not work, grub sayes it can not mount the partition. 

I found one thing that is very strange in the output of fdisk: 
```

  /dev/hda2            1217        9729    68380672+   f  W95 Ext'd (LBA)
  /dev/hda3            3649        5472    14651248+   b  W95 FAT32

```
From the above output, hda2 is extended partition, as far as I know, all logical partition should start from number 5, but hda3 seems is a logical partition! That is very strange and I can not remember what I have done that makes it looks like this. This is related to the problem. But I don't know what I should do with hda3. Any hints are appreciated.  
I really don't want to reinstall Ubuntu :)

---

