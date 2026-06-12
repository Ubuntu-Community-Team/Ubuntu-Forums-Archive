---
title: "Install success/reboot failure"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by rediron on 2010-05-27
I successfully installed 10.04 x86_64 and let it run for a few days. I rebooted a couple of times. Week 2, I did all the updates, then rebooted.   It comes back up with:

error: out of disk
grub rescue>

It was a fresh install on a 500G disk.  I made a /boot 100M, 8G swap, 20G / ext4 partitions.

I have some suspicions, don't know which of them to pursue, which are red herrings.

1.  Perhaps grub2 can't do ext4.  ls shows all the correct disks and filesystems, but ls on all the partitions results in "unknown filesystem" error.   There are 5 disks in system, 2-4 partitions each, some ntfs, some ext2, ext3, some swap and 3 new ext4.   Grub can't read any of them ?

2.  Different components of Ubuntu are deciding to reorder the disks.   I can boot to the 10.04 cd and look at all the partitions,  the new 10.04 OS has /etc/fstab with entries that are commented "this was /dev/sda1 at time of installation..."   I notice that when in the Live CD,  the disks have been reordered for me.   what used to be disks 1 2 3 4 5  is now 3 4 5 1 2.   Both orders are completely reliable: order 34512 when booting to Live CD and 12345 when booting to grub2 or the Live CD installer.

I know have some more suspicions, but my head hurts right now with this trouble.   I will will write down more after a break and some grub (the food kind).   Anyone have an idea what can be going on ?  

Thanks

Red

---

### Post by darkod on 2010-05-27
Sounds like this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

Give it a shot.

---

### Post by rediron on 2010-05-28
> **darkod said:**
> Sounds like this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

Give it a shot.

Thanks - I gave it a try, removing the search lines in the grub config, but it still doesn't boot.   The article seems to say that problem occurs when you get to the grub menu, then something goes wrong from there.   This problem is that grub is on the mbr, then thats it.  It can't read ext filesystems.  It can't ready any other filesystems either, but I think it should be able to read ext2.

Well, I'll poke around some more.

---

### Post by garvinrick4 on 2010-05-28
If the new ubuntu OS is in sda1 and you made a seperate boot partition which should
then be sda1 not your OS. Did you make sure when you installed that you specified in advanced on last page of install to put boot in sda. Your mbr then will be in sda1 and whatever your linux install will be sda2, sda5 or whatever it is not in sda1. And you said
sda1 was just a 100 meg or so. Enough for mbr. If you can show the results of below will help a bit. 

```
sudo fdisk -l
```


```
sudo blkid
```

---

### Post by rediron on 2010-05-28
> **garvinrick4 said:**
> If the new ubuntu OS is in sda1 and you made a seperate boot partition which should
then be sda1 not your OS. Did you make sure when you installed that you specified in advanced on last page of install to put boot in sda. Your mbr then will be in sda1 and whatever your linux install will be sda2, sda5 or whatever it is not in sda1. And you said
sda1 was just a 100 meg or so. Enough for mbr. If you can show the results of below will help a bit. 

```
sudo fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003b8e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13       96256   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        2444    19530752   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5911a7ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488383968+  83  Linux

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00064cd1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1275    10241406   83  Linux
/dev/sdd2            1276        1402     1020127+  82  Linux swap / Solaris
/dev/sdd3            1403       24321   184096867+  83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e4c67

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4433    35602024+   7  HPFS/NTFS
/dev/sdc3            4433        9730    42547176    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.




> ```
sudo blkid
```
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4054b636-1f03-46c4-8d40-59f67c147090   ext4                                     
/dev/sda2        302aa423-ec08-4376-ba80-06cf7bd66f64   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        54vsIx-hxzD-gOAd-pJeG-oOiw-ezau-kV12C2 LVM2_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        E644BDE944BDBD1D                       ntfs                                     
/dev/sdc3        FC94535194530D90                       ntfs       Bilbo                         
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        7dc7a6e7-96b7-4dc1-937a-bd5ba2dc64ea   ext3                                     
/dev/sdd2        e529b5f4-2fc6-4335-b1f0-01231e39ccf4   swap                                     
/dev/sdd3        c63c7381-9a55-4fe1-83f0-ffae924ef602   ext3                                     
/dev/sdd: PTTYPE="dos"

I've run the "boot info" script and I just noticed that grub installed itself into Windows C drive.  I'm terrified at what its doing to my data.  Sometime when I boot into the Ubuntu 10 cd all the disks are in order ala bios.  Sometimes, booting to the same cd they all in different order.  Appearantly the system got up and running, then the system reordered it's disks while it was running, then update manager ran and put the kernel and /boot/grub into disk #3.  I did check; the new updated packages have been installed into Windows.

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub 0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc1 has 
                       71200008 sectors, but according to the info from 
                       fdisk, it has 71204048 sectors.
    Operating System:  Windows XP
[B]    Boot files/dirs:   /grub/grub.cfg /boot.ini /ntldr /NTDETECT.COM 
                       /grub/core.img
[/B]
sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:

---

### Post by darkod on 2010-05-28
Grub2 works just fine with ext4, that's not the problem. Maybe there is some problem with your ext4 filesystem, or ext3, but generally, I was using grub2 with 9.10 and ext4, and now using it with 10.04 and ext4. So it works.

Also, are you booting all the time from /dev/sda or sometimes when needing XP you just set /dev/sdc as primary disk? Some people do that, and I'm just guessing, but it might confuse grub sometimes maybe.

Are the disks correct in /boot/grub/device.map? You can recreate new device.map with:

sudo grub-mkdevicemap

After that you might try running update-grub to update the grub.cfg.

Also, if you suspect grub is looking at your other disks when doing updates too, run:

sudo dpkg-reconfigure grub-pc

and select only /dev/sda to be looked at by grub2. If other disks are selected, deselect them.

One reason the order of disks might change is if you unplugged some of them during install. Lots of people do that because they feel safe with their data that way, but I can't really tell what would happen when plugging the disks back in, and what order they will take. My opinion is that when installing any OS all hardware should be present. If you pay attention what you install and where, your data is safe. :)

---

### Post by rediron on 2010-05-28
I've wondered maybe, grub2 installed on an mbr needs access to a /boot/grub/ before it can access filesystems, lvm, ext(n), etc..   But theres a chicken/egg problem with that idea. 

Then down to main problem:  hardware (probably) is reordering disks.  I've noticed that when I boot to the Ubuntu 10 cd and look around, the disks are in different order.   I haven't changed anything in bios and I haven't done anything with the cables.  Just sometimes, the disks are in different order.  I'm not sure yet if it is happening at boot or when the system is up and running.

<wondering outloud> Are ata disks hot plug ?  i.e., if there was a loose cable and a sata drive went away does hardware notice and remove it from live hw resources ?   Same for ide.  Same for sata and ide controllers; if one was slow on the startup, then would bios put the ones that are responding first despite order ? 

Some of grub is installed in mbr, some in the right partition, and some of it in a Windows C drive partition.   I will have to regen the device.map, reinstall grub and perhaps the Ubuntu 10, depending on how badly the install is messed up.   Before I write to a disk, I am going to go through the other OS/disks and make sure there hasn't been any corruption or loss.  

I would like to know about the h/w issue of resources moving around under what conditions before I try to install Ubuntu again.  

I will update later.  Thank you, Darko and Garvin, for your help so far.

---

### Post by darkod on 2010-05-28
The grub2 config files seem in place. The results say Grub2 is installed in the MBR of /dev/sda and look in partition #1. And /dev/sda1 is really your /boot partition, so it has grub.cfg and grub.core inside.

Yes, the /grub/grub.cfg and /grub/grub.core seem in the wrong place on /dev/sdc1 and shouldn't be there, but you also have files where needed in /dev/sda, so it looks fine.

I would still try the command to recreate new device.map though.

The disks are not hot plug. Not in general, except disks specially made usually for servers. In fact, if the system is running you should not plug/unplug the cables in the hdd. It can kill the disk that way. So you need to power down the computer and make sure the connections are firm, if in any doubt.

Out of curiosity, why is /dev/sda only used up to cylinder 2444 out of 60801? That's barely 20GB from a 500GB disk.

---

### Post by rediron on 2010-05-28
Thank you for the encouragement,  I will try tonight; I will rebuild the device map.  That might be all it needs if I can keep the hardware from reording the disks. 

I wanted to install into lvm, but there was no lvm option in the installer.  So,  I thought I'd keep /boot up front, make a small partition to hold the os install, then while the system is up, build the volume group with the rest of the space, a lv for the os /, then boot to cd later and copy the os into it.   If it worked, then I would take the free 20G partition and add it to the volume group.

---

### Post by darkod on 2010-05-28
For RAID and/or LVM you need to use the Alternate Install image, not the standard desktop (live cd). It has text based installer but you still end up with the same system. It can install RAID and LVM.

---

### Post by rediron on 2010-06-01
There was no device.map file, so I created one.  The boot still went to grub rescue mode, though.   I will have to reinstall grub 2 from the cd.  I've read the full grub 2 manuals a few times and there is note in there that says that it isn't production ready.  I am not sure if I have the patience to stick with it.  My Ubuntu 9 system (same hardware) never once reordered the hard drives and I see many "disks out of order" issues regarding grub 2 so I am suspicious that it is inside g2 when my problems occur.  There is nothing about the reordering scheme in g2 manuals. 

If I do try the full reinstall method, I'll look for the alternate disk for lvm.   

thanks again for all the help.

---

