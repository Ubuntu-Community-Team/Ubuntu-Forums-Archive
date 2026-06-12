---
title: "howto install Kubuntu on LVM partition ?"
date: 2019-03-09
forum: Installation &amp; Upgrades
---

### Post by anderbuntu on 2019-03-09
[COLOR=#000000][FONT=sans-serif]Hi[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]How can I install new Kubuntu [/FONT][/COLOR]18.04 [COLOR=#000000][FONT=sans-serif]to LVM partition ?[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]There is only option to - use entire disk and setup LVM...[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]I have dual boot with WIn10, so I dont want this option.[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]In manualy option >> there is no option to create LVM partition > when I created manualy with fdisk and then I go back to install screen > this LVM partition is not recognized...[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Any idea ?[/FONT][/COLOR]

---

### Post by Dennis N on 2019-03-09
The installer can't create a partition for LVM use. But gparted can*. Running it from the live media, format the partition as "lvm2 pv" (lvm2 physical volume). Then there is a bit more to do:

After the partition is made, you need to use the terminal from the live media session to create a volume group from the partition, and then create a logical volume in that volume group to use for root of the OS installation (and optionally one for a separate home). Are you familiar with LVM-related commands? The installer will display the logical volume you create in the partitioning screen, where you can designate it for root of the OS being installed.

*you can also use a simple terminal command to prepare a partition for LVM use: **sudo pvcreate /dev/sda3** for example.

---

### Post by anderbuntu on 2019-03-10
Hi

Yes, I created lvm2 partition via KDE Partition Manager then I  created PV, VG, LV and ext4 FS on it, also tried to mount and touch a  file, all OK,
Also I checked via Gparted app > and shows LVM  partition....hwever when I try to install  Kubuntu >  partiotn sda8  is still no recognized...

Any idea ?

Attaching screenshots..


vgdisplay >
vgdisplay -v
  --- Volume group ---                                                                                                                                                                                                                
  VG Name               vg00                                                                                                                                                                                                          
  System ID                                                                                                                                                                                                                           
  Format                lvm2                                                                                                                                                                                                          
  Metadata Areas        1                                                                                                                                                                                                             
  Metadata Sequence No  2
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               <30.04 GiB
  PE Size               4.00 MiB
  Total PE              7690
  Alloc PE / Size       7680 / 30.00 GiB
  Free  PE / Size       10 / 40.00 MiB
  VG UUID               glqebe-Fm5T-g9n6-fHXY-Ez1r-csp2-Iisrao
   
  --- Logical volume ---
  LV Path                /dev/vg00/lv00
  LV Name                lv00
  VG Name                vg00
  LV UUID                t5It8v-0UNQ-5e5d-9Ys1-00J0-I2uZ-umAcRo
  LV Write Access        read/write
  LV Creation host, time kubuntu, 2019-03-10 11:56:39 +0000
  LV Status              available
  # open                 0
  LV Size                30.00 GiB
  Current LE             7680
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
  --- Physical volumes ---
  PV Name               /dev/sda8     
  PV UUID               KGcg1A-xY20-Szh5-VoxP-6nva-mC04-OF89cJ
  PV Status             allocatable
  Total PE / Free PE    7690 / 10

---

### Post by Dennis N on 2019-03-10
>  I checked via Gparted app > and shows LVM partition....hwever when I try to install Kubuntu > partiotn sda8 is still no recognized...

The "Prepare Partitions" screen shown in your 2nd screenshot should show the logical volumes above all the partitions. Use those to make your selection for install location. See the attached screenshot.

---

### Post by anderbuntu on 2019-03-10
> **Dennis N said:**
> The "Prepare Partitions" screen shown in your 2nd screenshot should show the logical volumes above all the partitions. 

Yes, ..should show... but  not showing.... I don't know why 

There is only showing **sda8** as **unknown** partition

---

### Post by anderbuntu on 2019-03-10
Aaah, I checked again, and you have right, is there on the top.  :)
Thanks for help

A.

---

