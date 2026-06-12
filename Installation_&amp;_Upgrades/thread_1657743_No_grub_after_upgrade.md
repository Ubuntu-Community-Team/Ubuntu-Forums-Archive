---
title: "No grub after upgrade"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by Bryan55 on 2011-01-01
Hi.
I started off on 9.10 and upgraded to 10.4 without any problems.

However during the upgrade to 10.10 got asked about grub (see attachment 1& 2) and I think I should have ticked the other boxs but I didn't. I also got an error (see3) The 4th one I think is a different issue.

On the restart it would only get to the purple screen before the login field appears.
I presume I need to do something to the grub but have no idea what.
My system is 64bit and a raid 1. 
The attachment 5 shows the partition arrangement

I can boot into the the PC with a live (32bit 10.10) cd.

Your help would be very welcome.
Bryan

---

### Post by Bryan55 on 2011-01-01
Hi again.
I have read in other threads that boot info script is needed.

So hear is mine. Hope it helps.
 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/grub.

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     1,172,744     1,172,682  fd Linux raid autodetect
/dev/sda2           1,172,745    40,242,824    39,070,080  fd Linux raid autodetect
/dev/sda3          40,242,825   976,768,064   936,525,240   5 Extended
/dev/sda5          40,242,888   964,076,714   923,833,827  fd Linux raid autodetect
/dev/sda6         964,076,778   976,768,064    12,691,287  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,172,744     1,172,682  fd Linux raid autodetect
/dev/sdb2           1,172,745    40,242,824    39,070,080  fd Linux raid autodetect
/dev/sdb3          40,242,825   976,768,064   936,525,240   5 Extended
/dev/sdb5          40,242,888   964,076,714   923,833,827  fd Linux raid autodetect
/dev/sdb6         964,076,778   976,768,064    12,691,287  fd Linux raid autodetect


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e1ca07f2-9317-8237-28f9-9ea2dfd4c30a   linux_raid_member                               
/dev/sda2        c64025b6-bfe8-b49c-ac86-4255b0c1b559   linux_raid_member                               
/dev/sda3: PTTYPE="dos" 
/dev/sda5        0444353b-76e0-7fde-36a8-e3985bb804e6   linux_raid_member                               
/dev/sda6        4eeb94aa-f265-87e1-ae00-cf5db2d1cde4   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        e1ca07f2-9317-8237-28f9-9ea2dfd4c30a   linux_raid_member                               
/dev/sdb2        c64025b6-bfe8-b49c-ac86-4255b0c1b559   linux_raid_member                               
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        0444353b-76e0-7fde-36a8-e3985bb804e6   linux_raid_member                               
/dev/sdb6        4eeb94aa-f265-87e1-ae00-cf5db2d1cde4   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by Bryan55 on 2011-01-02
Hi.
I have been looking into the "fglrx" issue and found the this could be why it would not boot.

I tried holding "shift" when starting the computer to bring up grub menu which work( this is all new to me). Then selected Recovery mode and then Safe Graphic Mode and I got in. I was then going to install the proprietary drivers for my ati card but the PC , even with live CD,has not been able to connect to the internet (wired) I will start to do some searches on that and perhaps start a new topic.

So it looks like grub is not the problem though I can not get into the grub menu any more by holding Shift it just boots straight into Safe Graphic Mode.

Bryan

---

### Post by dino99 on 2011-01-02
the second sreenshot show you an issue (might says two) with /dev/md0 & /dev/md1.

[http://www.linuxquestions.org/questions/linux-software-2/raid5-using-mdadm-how-to-mount-dev-md0-387769/](http://www.linuxquestions.org/questions/linux-software-2/raid5-using-mdadm-how-to-mount-dev-md0-387769/)

---

