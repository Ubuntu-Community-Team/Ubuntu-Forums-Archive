---
title: "Tripple Boot"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by merlin051 on 2008-10-07
Ok, here's the story, I'm trying to make my laptop triple boot.

I've got a successful double boot working Ubuntu + Windows, But I'm wanting to boot a third distro.(Backtrack 3 Specifically - SLAX based)

I've tried creating an extra 2 partitions (one for root and one for =/changes)

However no matter what I try I'm having problems getting the grub to boot the new distro.

Here is an output of fdisk -lu
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc701c701

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   104711669    52355803+   7  HPFS/NTFS
/dev/sda2       104711670   312576704   103932517+   5  Extended
/dev/sda5       104711733   308078504   101683386   83  Linux
/dev/sda6       308078568   312576704     2249068+  82  Linux swap / Solaris

```

at the moment I dont have my extra 2 partitions on there, but I'm not sure why currently its showing 1/2/5/6 as far as i know there is only 3 active partitions. they are NTFS - Windows, Linux Swap and Linux for ubuntu.

Also, when stopping on teh grub menu and trying to use the geometry command, i get the following error ```
Error 21: Selected disk does not exist

```

I only have 1 HD so I'm assuming its HD0 ?

Please advise, I'm using a Dell Inspiron 1300 with a 160gb Drive.

---

### Post by Malac on 2008-10-08
```
/dev/sda1   *          63   104711669    52355803+   7  HPFS/NTFS
/dev/sda2       104711670   312576704   103932517+   5  Extended
/dev/sda5       104711733   308078504   101683386   83  Linux
/dev/sda6       308078568   312576704     2249068+  82  Linux swap / Solaris
```
sda1 (hd0,0) is first disk first partition ( a primary )
sda2 (hd0,1) is extended partition which contains the other two.
sda5 (hd0,4) is first logical partition within extended (these start at 5 to allow for 4 primary partitions)
sda6 (hd0,5) is second logical partition within extended

This is probably best visually represented if you look at the drive in gparted(Partition Editor).

New logical partitions would be /dev/sda7(hd0,6) and /dev/sda8(hd0,7) unless you have unallocated space on the drive in which case you could create them as /dev/sda3(hd0,2) and /dev/sda4(hd0,3)

Hope this helps.

EDIT: post or attach your /boot/grub/menu.lst file as well as fdisk -l output with the new partitions.

---

