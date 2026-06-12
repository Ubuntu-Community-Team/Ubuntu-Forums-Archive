---
title: "How to expand disk using LVM"
date: 2014-02-24
forum: Installation &amp; Upgrades
---

### Post by giambolo on 2014-02-24
Hi there, I've a Ubuntu mounted on a 20 GB disk, it's under Vmware. I have to expand it of an additional 10 GB. Under VmWare I expanded the disk to 30GB and now I see, under gparted, an additional space of 10 GB. I'm not familiar with LVM, this is why I'm posting this question.
Provided that I have /boot on sda1, I now have sda2 as extended, which contains two partitions, respectively sda5 lvm2pv in group ubuntuvg and sda6, same characteristics but with 10 GB.
 
Do I understand well that I can see one single file system under ubuntuvg? If I'm correct, how could I merge the two spaces?
 
P.S. I'm a bit confused when using df which shows /dev/mapper/ubuntu--vg-root 100% 

Thanks everybody for every contribution.
 
Elio

---

### Post by giambolo on 2014-02-24
OK, I understood the LVM system and I'm posting how I fix it. Maybe someone else will, like me, get confused at first by LVM. Just my humble contribution to the community.

First of all, we only have to use the lvm(xx) commands. Using df to check available space will confuse it. With the session  log I'm posting, I believe that every one should be able to span a logical disk over more physical disks.

 Long live Linux ...

elio@ubu1310:~$ lvmdiskscan
  /dev/ram0             [      64,00 MiB] 
  /dev/ubuntu-vg/root   [      18,27 GiB] 
  /dev/ram1             [      64,00 MiB] 
  /dev/sda1             [     243,00 MiB] 
  /dev/ubuntu-vg/swap_1 [       1,47 GiB] 
  /dev/ram2             [      64,00 MiB] 
  /dev/ram3             [      64,00 MiB] 
  /dev/ram4             [      64,00 MiB] 
  /dev/ram5             [      64,00 MiB] 
  /dev/sda5             [      19,76 GiB] LVM physical volume
  /dev/ram6             [      64,00 MiB] 
  /dev/sda6             [      10,00 GiB] LVM physical volume
  /dev/ram7             [      64,00 MiB] 
  /dev/ram8             [      64,00 MiB] 
  /dev/ram9             [      64,00 MiB] 
  /dev/ram10            [      64,00 MiB] 
  /dev/ram11            [      64,00 MiB] 
  /dev/ram12            [      64,00 MiB] 
  /dev/ram13            [      64,00 MiB] 
  /dev/ram14            [      64,00 MiB] 
  /dev/ram15            [      64,00 MiB] 
  1 disk
  18 partitions
  0 LVM physical volume whole disks
  2 LVM physical volumes
elio@ubu1310:~$ sudo vgs
  VG        #PV #LV #SN Attr   VSize  VFree 
  ubuntu-vg   2   2   0 wz--n- 29,75g 10,02g
elio@ubu1310:~$ sudo pvscan
  PV /dev/sda5   VG ubuntu-vg   lvm2 [19,76 GiB / 20,00 MiB free]
  PV /dev/sda6   VG ubuntu-vg   lvm2 [10,00 GiB / 10,00 GiB free]
  Total: 2 [29,75 GiB] / in use: 2 [29,75 GiB] / in no VG: 0 [0   ]

### Extends by 9 GB, out of 10
elio@ubu1310:~$ sudo lvextend -L+9G /dev/ubuntu-vg/root /dev/sda6 
  Extending logical volume root to 27,27 GiB
  Logical volume root successfully resized
elio@ubu1310:~$ 

### Extends using all the free space left
elio@ubu1310:~$ sudo lvextend  /dev/ubuntu-vg/root /dev/sda6 
  Extending logical volume root to 28,26 GiB
  Logical volume root successfully resized

### To check the space, forget tthe df command, now using lvdisplay
elio@ubu1310:~$ sudo lvdisplay 
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                lA1cK3-gGBt-w93S-RW8l-5dwB-dOhD-R2FAcG
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-01-16 19:10:15 +0100
  LV Status              available
  # open                 1
  LV Size                28,26 GiB
  Current LE             7235
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                OXPl60-b4l6-wvio-zQH5-vpBe-QySJ-dohWjt
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-01-16 19:10:15 +0100
  LV Status              available
  # open                 2
  LV Size                1,47 GiB
  Current LE             377
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

---

