---
title: "RAID 5 (Intel) not recognized in OS but was in install"
date: 2015-09-18
forum: Installation &amp; Upgrades
---

### Post by tylerdavidharris on 2015-09-18
I am attempting to build my own Linux server with:
[LIST]
[*]1 SSD "boot" drive where I have installed Ubuntu 
[*]3 3TB WD-Red HDSs in RAID 5 
[/LIST]
  I created my RAID 5 set in BIOS:
[LIST]
[*]Gigabyte H97N-WIFI motherboard/Intel Software RAID 
[*]During the Ubuntu install, it recognized the SSD and a 6TB "Software RAID"
*Note: I installed Ubuntu 14.04.3 LTS on the SSD using pendrivelinux.com, according to [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)* 
[/LIST]
**THE PROBLEM**:
[LIST]
[*]Ubuntu doesn't appear to recognize my RAID 5 array.. Disk Utility shows all 3 drives separately as /dev/sdb, /dev/sdc, /dev/sdd; however, as noted above, during the install it recognized a single 6TB drive. 
[*]Selecting each drive will show on the right panel: "Volumes" as "3.0 TB IMSM RAID Member (1.3.00)" and at the bottom, "Contents" as "Intel Matrix RAID Member (version 1.3.00)" 
[/LIST]
The closest appearing issue I could find is this, but I could not resolve it similarly:
[http://ubuntuforums.org/showthread.php?t=1514575](http://ubuntuforums.org/showthread.php?t=1514575)

 Any ideas would be very much appreciated!! The following information may be helpful:[I]
```

tharris@tdh-ubu:/dev/mapper$ dmraid -l
asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1,5,01)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs
tharris@tdh-ubu:/dev/mapper$ sudo dmraid -r
[sudo] password for tharris: 
/dev/sdd: isw, "isw_bcbdehieih", GROUP, ok, 5860533166 sectors, data@ 0
/dev/sdc: isw, "isw_bcbdehieih", GROUP, ok, 5860533166 sectors, data@ 0
/dev/sdb: isw, "isw_bcbdehieih", GROUP, ok, 5860533166 sectors, data@ 0
tharris@tdh-ubu:/dev/mapper$ sudo dmraid -b
/dev/dm-0:   3131122176 total, "N/A"
/dev/sdd:   5860533168 total, "WD-WCC4N4CVR63Z"
/dev/sdc:   5860533168 total, "WD-WCC4N2DN6DUR"
/dev/sdb:   5860533168 total, "WD-WCC4N0FHAF4T"
/dev/sda:    117231408 total, "OCZ-N0EW247FJY5PZ5ZT"
tharris@tdh-ubu:/dev/mapper$ ls /dev/mapper/
control  isw_bcbdehieih_WD-RED
tharris@tdh-ubu:/dev/mapper$ sudo fdisk -l

Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   117231407    58615703+  ee  GPT

Disk /dev/mapper/isw_bcbdehieih_WD-RED: 1603.1 GB, 1603134554112 bytes
255 heads, 63 sectors/track, 194903 cylinders, total 3131122176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_bcbdehieih_WD-RED doesn't contain a valid partition table
tharris@tdh-ubu:/dev/mapper$ sudo dmraid -r
/dev/sdd: isw, "isw_bcbdehieih", GROUP, ok, 5860533166 sectors, data@ 0
/dev/sdc: isw, "isw_bcbdehieih", GROUP, ok, 5860533166 sectors, data@ 0
/dev/sdb: isw, "isw_bcbdehieih", GROUP, ok, 5860533166 sectors, data@ 0
tharris@tdh-ubu:/dev/mapper$ sudo dmraid -ay
RAID set "isw_bcbdehieih_WD-RED" already active

```
[/I]

---

### Post by TheFu on 2015-09-19
I think this is "FakeRAID" - personally, I don't have much use for it because it has all the issues of HW-RAID, but not the performance.  Since the performance is similar to SW-RAID, why not use that and gain the added flexibility of not being tied to HW?  [https://superuser.com/questions/245928/does-fake-raid-offer-any-advantage-over-software-raid](https://superuser.com/questions/245928/does-fake-raid-offer-any-advantage-over-software-raid) has more.

I've moved SW-RAID arrays between Linux systems without any issues multiple times. Couldn't do that with FakeRAID. Just sayin'.

Don't use fdisk on GPT disks. Use **parted** or **gparted**.

SW-RAID is created/controlled/managed with the **mdadm** tool.  You may want to "scrub" the RAID data weekly to catch issues ASAP.

---

### Post by tylerdavidharris on 2015-09-19
Thanks for your advice! I didn't realize that about onboard motherboard raid controllers, but it definitely makes sense. I have things going and am waiting on the parity to finish. I used mdadm. Do you have any helpful links or docs that might help clarify what to do to "scrub" the RAID data weekly? Any recommendations for maintenance would be very much appreciated as this is my first experience with RAID-5. Thanks for your help!!

Here are the steps I have taken to configure my SW-RAID array using mdadm on Ubuntu Server after disabling my onboard raid and switching back to AHCI mode in BIOS:
[I]Note: I am currently waiting for my array to finish it's initialization, but I expect the following will work unless anyone has any suggestions. I used the following as my guide: [https://www.flynsarmy.com/2012/12/create-and-manage-a-raid-array-in-ubuntu/](https://www.flynsarmy.com/2012/12/create-and-manage-a-raid-array-in-ubuntu/)

(removed the steps as they were incorrect. I used fdisk when I should have used parted as was suggested since my drives are >2TB and use GPT)
[/I]

---

### Post by TheFu on 2015-09-19
For GPT disks, don't use fdisk. Use gparted or parted. Said this above already. Let me know now if my advice isn't wanted. It will be easier for me going forward.

The mkfs stuff wasn't useful. That doesn't happen until **after** the array is created.

Do not add those commands to the bottom of the conf file. Don't know what it does, but it won't be good if it does anything. That isn't how conf files work.

Be careful getting how-to guides from blogs. Try to stay with reputable sites - *.ubuntu.com  askubuntu and here.  Often, blog articles are written by someone who does'nt know as much as you and just because they got something working on their system, doesn't mean it applies to yours.  Lots of things change every release - so things that work on 12.04 no longer apply with 14.04 and there will be major changes when 16.04 is released.

BTW, if you are running a "server", stick with LTS releases (as you have). Avoid all the others unless you can handle a fresh OS install every 6 months. I can't.

Of course, I have a blog where I've written lots of articles, mostly about Ubuntu and Virtualization. SW-RAID sorta "just works" for me. 

Scrubbing RAID - [https://serverfault.com/questions/369132/maintain-raid-to-keep-it-healthy-data-scrub](https://serverfault.com/questions/369132/maintain-raid-to-keep-it-healthy-data-scrub) - use the **checkarray** tool. I do it from cron, weekly, when idle.

And of course, RAID is not a backup.  RAID addresses 1 issue.  Backups address 1000 issues. Backups are 100x more important than RAID.

---

### Post by tylerdavidharris on 2015-09-19
Thanks for your help! I used parted now instead and didn't do mkfs until after the array like you suggested. Thanks for the scrubbing link as well. I found the following helpful when using parted: [http://askubuntu.com/questions/350266/how-can-i-create-a-raid-array-with-2tb-disks](http://askubuntu.com/questions/350266/how-can-i-create-a-raid-array-with-2tb-disks). What do you think?:
```

**tharris@tdh-ubu:~$ [COLOR=#ff0000]cat /proc/mdstat[/COLOR]**
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdd1[3] sdc1[1] sdb1[0]
      5860267008 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]


unused devices: <none>


**tharris@tdh-ubu:~$ [COLOR=#ff0000]sudo mdadm --detail /dev/md0[/COLOR]**
/dev/md0:
        Version : 1.2
  Creation Time : Sat Sep 19 14:53:34 2015
     Raid Level : raid5
     Array Size : 5860267008 (5588.79 GiB 6000.91 GB)
  Used Dev Size : 2930133504 (2794.39 GiB 3000.46 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent


    Update Time : Sun Sep 20 12:33:16 2015
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : tdh-ubu:0  (local to host tdh-ubu)
           UUID : a3de6872:83734185:1959ae34:0f874ad7
         Events : 85680


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      active sync   /dev/sdd1

```

At first, I was concerned that the initialization-sync was going to take too long, but I let it go overnight and it somehow finished way ahead of schedule, so I was happy about that for sure. Of note, I've been reading that it's normal for mdadm to create the array initially in degraded mode as it marks the spare disk for rebuilding and then calculates parity, etc: [https://raid.wiki.kernel.org/index.php/Initial_Array_Creation](https://raid.wiki.kernel.org/index.php/Initial_Array_Creation).

I saved my raid configuration in the mdadm.conf file as suggested here:
[https://raid.wiki.kernel.org/index.php/RAID_setup#Saving_your_RAID_configuration](https://raid.wiki.kernel.org/index.php/RAID_setup#Saving_your_RAID_configuration) 

Thanks again for your help! Things appear to be working quite well actually.

---

