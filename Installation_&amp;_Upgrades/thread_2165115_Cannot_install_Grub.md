---
title: "Cannot install Grub"
date: 2013-08-03
forum: Installation &amp; Upgrades
---

### Post by GirlFromMars on 2013-08-03
[h=1][B]Totally new to linux and trying to install on an old dell laptop which I believe has RAID 0.  When I get to the following error:

Cannot install GRUB to /dev/sda[/B][/h]
I then chose the first option from the drop down list of alternatives /dev/mapper/pdc_bdffj then it said ok and rebooted but will not actually boot up, presumably I chose the wrong one and the laptop now and stuck at the "Fast build utility" menu.  So now I'm trying to re-install again and it now says I have two operating systems of 12.04 and 12.04 so I'm not sure what to do next.  I am at the erase disk and install ubuntu or do something else option.

I see in searches that other people have fixed this but I don't know what they did.

Help!

---

### Post by Bashing-om on 2013-08-03
GirlFromMars; Hi ! Welcome to the forum.

Let's get the raid question out of the way ... if you think Raid0 has been used in the past... that meta data must be removed in order to install a desk top system.
Try this... Boot up the liveDVD(USB) and from terminal install the dmraid tools to cope with this situation.
This is presupposing that 'buntu is the sole operating system to be installed.. else would entail a lot of hassle to get Windows back up.
```
sudo apt-get install dmraid
```
To remove that old raid meta data do terminal code:
```

sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

``` where "sda" is the linux nomenclature for the first hard disk, "sdb" is the second hard disk (if applicable).

Now-a-days installing any alternate software may have gotten complex ... what with UEFI,  SSRT,   Intel Smart Response Technology and others precluding loading a boot loader. Let us hope that in your case all that needs to be dealt with is the meta data from Raid.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by GirlFromMars on 2013-08-03
Ok, I've done that and now when it gets to the installation rather than the one 320gb I get sda or sdb each with 160gb.  Fair enough but no matter which I chose I get :No root file system is defined.

---

### Post by Bashing-om on 2013-08-03
GirlFromMars; Hey ...

As this is a fresh install and ubuntu is the sole operating system ... 
If It were me ... I would fire up GParted (ubuntu's partition editor) from the liveDVD and delete all partitions present on my hard disk(s), make a new partition table (as msdos - msdos !=  Micrsosoft disk operating system) and then try and install ubuntu from scratch.
Initially in my beginning years I found the help files for using GParted though accurate somewhat confusing. Take the time to read the help files and we will help you over the rough spots.. in the event you require additional guidance.

Edit: Are you using the "something else" install option, rather than the 1st option to install "use the entire disk" -> lets the install wizard make all the decisions. ????
I have encountered that above error "manually" installing to afore created partitions. If you are doing the "something else" install, at the partition set up screen -> select the partition that holds your kernel and boot code (sda1 in all likely hood) -> select change ->in the next screen make sure "/" -with no quotes- is set in the "use as" field. 

[INDENT][INDENT]GParted works ![/INDENT][/INDENT]

---

### Post by GirlFromMars on 2013-08-03
I got an error cannot create swap when using the use entire disk then it sent me to the partion menu, picking anything there gave the no root file system defined.

I've ran the gparted and it got past both messages now, though it only formated sda with 160gb and didn't pick up the other 160gb in sdb, maybe I can do something else with that?  Anyhoo, it's still installing so fingers crossed...

---

### Post by Bashing-om on 2013-08-03
GirlFromMars;
 I am having a bit of difficulty relating as to where you are from the info provided...
GParted seeing 2 -as in two hard drives- of 160 GB on a 320 GB drives ... makes me question if there is not but one hard drive (physically) with 2 partitions and you are miss representing the nomenclature of Windows disk description onto ubuntu.

Let me back up a bit so I am clear on ubuntu disk nomenclature:
The first physical hard drive  will be noted as device sda ... partitions on that sda device are noted as sda1 = 1st partition, sda2 = 2nd partition
thus:
the second physical hard drive is noted as sdb ; and partitioning -> sdb1 sdb2 sdb3 and so on.

Now in the partition editor "GParted" the editor will show exactly what is on the selected hard disk. It is possible that the display does show 2 partitions on device (hard drive) sda ... maybe like unto sda1 and sda2 ... and I would expect other partitions ... like maybe "extended" (sda5 ?) or "swap" (sda6 ?).
It is also possible that a "swap" partition has been created .. and is in use .. and as it may be in use ... must be unmounted before any action can be taken on that hard disk by GParted ... do you see any key icons in the display setup area ?

A picture is worth a thousand words is never truer than now ... how about providing a screenshot of GParted ? So we all know we are all on the same page.

[INDENT][INDENT]said: longest journey starts with but one step -> we are getting there[/INDENT][/INDENT]

---

### Post by GirlFromMars on 2013-08-03
I'm missing a hard drive but it did install and boots fine now. Thanks very much.

In gparted only one 160gb drive named sda was showing that i could partition. sdb could not be found though it can be seen in my bios and I had it before I removed the raid.  I'm not hugely bothered as it's an old laptop and this was just an experiment but if anyone knows how to get it back or how I can use it for storage or something that would be awesome.

---

### Post by Bashing-om on 2013-08-03
GirlFromMars; Hey ...

Yer stepping out big now ... congrats on geting it installed ...
To see what all hard drives are installed and how they are partitioned ...terminal code:
```

sudo fdisk -l

```
example from my system:
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000945e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   968384511   484191232   83  Linux
/dev/sdc2       968386558   976771071     4192257    5  Extended
sysop@1304mini:~$ 


showing three 500 GB drives and all the partitions and related info.

[INDENT][INDENT]Welcome to ubuntu
[/INDENT][/INDENT]

---

