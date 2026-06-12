---
title: "help dual booting xp and ubuntu 10.10"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by conebone69jb on 2011-03-20
I am trying to dual boot xp and ubuntu 10.10 desktop.  Everything in 32 bit. I have xp installed now and created a bootable usb with ubuntu and am trying it out now.  i press install and then select my language.  I then select install updates and third party software.  I then get to a screen with 2 option erase disk and use that or specify partitions manually.  I want the option that says install side by side, but it is not there.  Can anyone help me?

---

### Post by Hedgehog1 on 2011-03-20
This usually happens because all four of your primary partitions are already taken.

Lets find out for sure.

Please boot off the LiveCD/Live USB, select TRY, and then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -lu
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by conebone69jb on 2011-03-20
> **Hedgehog1 said:**
> This usually happens because all four of your primary partitions are already taken.

Lets find out for sure.

Please boot off the live CD, select TRY, and then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -lu
```Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      128519       64228+  de  Dell Utility
/dev/sda2   *      128520    70669934    35270707+   7  HPFS/NTFS
/dev/sda3        70669935    78124094     3727080   db  CP/M / CTOS / ...

Disk /dev/sdb: 2038 MB, 2038431744 bytes
63 heads, 62 sectors/track, 1019 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3223366781  3470046704   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(825234, 44, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(888388, 51, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?   432871117  1208554935   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(110822, 6, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(309409, 54, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?  1869562563  3788792630   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(478638, 40, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(969992, 62, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?  2458386432  2466709559     4161564    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(629387, 13, 5)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(631518, 4, 4)
Partition 4 does not end on cylinder boundary.

---

### Post by Hedgehog1 on 2011-03-20
> Device Boot Start End Blocks Id System
/dev/sda1 63 128519 64228+ de Dell Utility
/dev/sda2 * 128520 70669934 35270707+ 7 HPFS/NTFS
/dev/sda3 70669935 78124094 3727080 db CP/M / CTOS / ...

Well that 3rd partition is unusual, and the install decided not to mess with it.

Do you know what data is on the third (sda3) partiton?  Are you still using it?

***The Hedge***

:KS

---

### Post by conebone69jb on 2011-03-20
> **Hedgehog1 said:**
> Well that 3rd partition is unusual, and the install decided not to mess with it.

Do you know what data is on the third (sda3) partiton?  Are you still using it?

***The Hedge***

:KS
no i only use 1 partition, i think windows might of made it but i have never used partitions

---

### Post by Hedgehog1 on 2011-03-20
OK, if you are sure you are not using it (and you can't call me names later if you discover you need it - Fair?) then you can delete /dev/sda3.

Then the install 'along side' will appear.  Please defrag your XP partition (C: drive from XP) before you install - it installs **much** faster that way.

For best results, may I suggest you do the partitioning manually?  

I can give you a nice guide with pictures.

***The Hedge***

:KS

---

### Post by conebone69jb on 2011-03-20
> **Hedgehog1 said:**
> OK, if you are sure you are not using it (and you can't call me names later if you discover you need it - Fair?) then you can delete /dev/sda3.

The the install 'along side' will appear.  Please defrag your XP partition (C: drive from XP) before you install - it installs **much** faster that way.

For best results, may I suggest you do the partitioning manually?  

I can give you a nice guide with pictures.

***The Hedge***

:KS
ok sounds fair i won't hold you responsible (i backed up my hard drive today) if you could send me the guide.

---

### Post by Hedgehog1 on 2011-03-20
This was for an HP with 4 partitions, so you can just ignore /dev/sda4, please:


[SIZE="4"][COLOR="DarkOrange"]First how it looks in Windows:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/9104/hp4partitions01.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]What it looks like in gparted off the LiveCD:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/8806/hp4partitions02.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right click on sda3 and select 'Delete':[/COLOR][/SIZE]
[IMG]http://img856.imageshack.us/img856/2164/hp4partitions03.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the 'check' mark button to really make the change:[/COLOR][/SIZE]
[IMG]http://img190.imageshack.us/img190/1732/hp4partitions04.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right Click, on empty area, select new and create extended sda3 (Press that check mark button again...):[/COLOR][/SIZE]
[IMG]http://img69.imageshack.us/img69/5967/hp4partitions05.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create you sda5 Ubuntu partition, leave a little room for swap later (Format this ext4 - and press that check mark button again.):[/COLOR][/SIZE]
[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create sda6 and make it swap space:[/COLOR][/SIZE]
[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the check mark button again[/COLOR][/SIZE]

---

### Post by Hedgehog1 on 2011-03-20
[SIZE="4"][COLOR="DarkOrange"]You are ready to install Ubuntu:[/COLOR][/SIZE]
[IMG]http://img864.imageshack.us/img864/2449/hp4partitions08d.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Select this during the install:[/COLOR][/SIZE]
[IMG]http://img705.imageshack.us/img705/2588/hp4partitions09.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]And you will get to here:[/COLOR][/SIZE]
[IMG]http://img849.imageshack.us/img849/9937/hp4partitions10.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]We will add some extra data to sda5 and sda6.  With sda5 highlighted, press the [CHANGE] button:[/COLOR][/SIZE]
[IMG]http://img861.imageshack.us/img861/5274/hp4partitions11.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]These settings prepare the partition to be exdt4, '/'.[/COLOR][/SIZE]
[SIZE="4"][COLOR="DarkOrange"]Repeat the steps for the swap area (This usually set itself up OK) :[/COLOR][/SIZE]
[IMG]http://img26.imageshack.us/img26/4934/hp4partitions12.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]You are ready to install.  Press [Install Now].[/COLOR][/SIZE]
[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG] 
[SIZE="4"][COLOR="DarkOrange"]This is what the drive looks like in the 'Disk Utility' in Ubuntu after the load is complete:[/COLOR][/SIZE]
[IMG]http://img852.imageshack.us/img852/3987/hp4partitions14.png[/IMG]  

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-20
>  Device Boot Start End Blocks Id System
/dev/sda1 63 128519 64228+ de Dell Utility
/dev/sda2 * 128520 70669934 35270707+ 7 HPFS/NTFS
/dev/sda3 70669935 78124094 3727080 db CP/M / CTOS / ...

In your PM, you asked how to avoid deleting a partition.

This requires that you reduce the size of your 'C:' drive (/dev/sda2).  Because XP does not offer the ability to shrink a partition with windows tool (Vista and Win7 do), Please do this:

In XP, defrag the C: drive (perhaps even 2 times), then shink it using gparted frm the LiveCD/LiveUSB.

After the XP partition is shrunk, reboot in xp and let the disk checker run.  Once XP is happy, create a new extended partition called /dev/sda4 (it is out of order, but that is OK) and make sda5 & sda6 as planned.

>  Device Boot Start End Blocks Id System
/dev/sda1 63 128519 64228+ de Dell Utility
/dev/sda2 * 128520 70669934 35270707+ 7 HPFS/NTFS
[B][COLOR="DarkRed"]/dev/sda4 extended
__/dev/sda5 ext4 '/'
__ dev/sda6 swap[/COLOR][/B]
/dev/sda3 70669935 78124094 3727080 db CP/M / CTOS / ...

***The Hedge***

:KS

---

