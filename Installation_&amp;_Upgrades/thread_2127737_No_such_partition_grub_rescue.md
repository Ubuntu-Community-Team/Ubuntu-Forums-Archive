---
title: "No such partition grub rescue"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by mysteron75 on 2013-03-20
I was reformating a partition on my storage drive to put my VMs on and when i booted the next day i got   No such partition grub rescue. How do i fix this i tried the boot repair disk and it did work. I really dont want to reinstall ubuntu again.Help
   

             Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader is installed in the MBR of 
    /dev/mapper/isw_cfcjbedich_Volume0.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/shimx64.efi

sdc3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

isw_cfcjbedich_Volume01: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_cfcjbedich_Volume03: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   950,219,263   950,219,263  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1             512   916,783,615   916,783,104 Data partition (Windows/Linux)
/dev/sda3     916,783,616   950,218,751    33,435,136 Swap partition (Linux)

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda3 ends after the last sector of /dev/sda
Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,640,847,844 1,640,845,797   7 NTFS / exFAT / HPFS
/dev/sdc2    *  1,953,329,152 1,953,523,711       194,560   b W95 FAT32
/dev/sdc3       1,640,849,408 1,953,329,151   312,479,744  83 Linux


Drive: isw_cfcjbedich_Volume0 _____________________________________________________________________

Disk /dev/mapper/isw_cfcjbedich_Volume0: 486.5 GB, 486512263168 bytes
255 heads, 63 sectors/track, 59148 cylinders, total 950219264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_cfcjbedich_Volume01                  1   950,219,263   950,219,263  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/mapper/isw_cfcjbedich_Volume01            512   916,783,615   916,783,104 Data partition (Windows/Linux)
/dev/mapper/isw_cfcjbedich_Volume03    916,783,616   950,218,751    33,435,136 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_cfcjbedich_Volume0p1 6abd668c-95dd-4cae-aef6-34cf59958ea4   ext4       
/dev/mapper/isw_cfcjbedich_Volume0p3 d9280847-b8d3-46d6-bd2c-b52bad844b53   swap       
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 
/dev/sdc1        F4CCC20FCCC1CC54                       ntfs       Storage
/dev/sdc2        3E52-C3DD                              vfat       
/dev/sdc3        724678c8-b515-4ea0-9171-2e0783d71eee   ext4       VMWare
/dev/sr1                                                iso9660    Ubuntu 12.10 amd64

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_cfcjbedich_Volume0
isw_cfcjbedich_Volume0p1
isw_cfcjbedich_Volume0p3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/ubuntu/Storage    fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda3


Unknown BootLoader on isw_cfcjbedich_Volume01


Unknown BootLoader on isw_cfcjbedich_Volume03



========= Devices which don't seem to have a corresponding hard drive: =========

sdd 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/mapper/isw_cfcjbedich_Volume01: No such file or directory
hexdump: /dev/mapper/isw_cfcjbedich_Volume01: No such file or directory
hexdump: /dev/mapper/isw_cfcjbedich_Volume03: No such file or directory
hexdump: /dev/mapper/isw_cfcjbedich_Volume03: No such file or directory
  No volume groups found

---

### Post by lindsay7 on 2013-03-20
Sounds like you are booting from sda and not sdc.  Go into bios and make sure the hard drive that is designated as sdc is the first boot drive.

---

### Post by oldfred on 2013-03-20
With RAID grub is installed to the root volume of the RAID not to the MBR of a drive or isw_cfcjbedich_Volume0

Something is not right with your partition table. But I do not know RAID.

> /dev/sda1 ends after the last sector of /dev/sda
/dev/sda3 ends after the last sector of /dev/sda


       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by mysteron75 on 2013-03-21
I had to install the mbr on my 2nd hard drive since i was not able to install it on the raid and every thing worked till i reformated a 160 gig partition on my second drive. I have been trying to reinstall grub on the 100 mb partition.

---

### Post by darkod on 2013-03-21
Hold on. We need more info, and crucial info. For example, you are mentioning a second disk but never mention that you are using raid. So, that would make three disks in total, minimum. Right?

sdb is not even shown as present. So.....

1. Are you using raid? If yes, what exactly, fakeraid or mdadm SW raid? Which disks make up your raid?
2. Are you dual booting with windows or not?

EDIT PS. Also there is one thing I don't understand but it seems too late for that. Why are you using gpt tables on the disks? They are not bigger than 2TB which is when you would usually use gpt. I am asking because GPT and UEFI make things more complicated, especially if dual booting.

You had the option to use msdos tables and standard bios boot which would be much better option.

As for installing grub on fakeraid, it doesn't work with the desktop live cd. You need to use the alternate installer or add grub later after the install. When you add it later, you install it onto the array MBR, not on any partition on the array. Or likewise not to any partition on a non-raid disk. Grub goes to the MBR of a disk or array.

---

### Post by mysteron75 on 2013-03-21
I am running a raid 0 with 2 ssds and i have a 1TB storage drive
/dev/sda isw_raid_member
 /dev/sdb isw_raid_member . 

My raid is running of a intel controller on my motherboard. My storage drive has 3 partitions

 /dev/sdc1 F4CCC20FCCC1CC54 ntfs Storage
/dev/sdc2 3E52-C3DD vfat 
/dev/sdc3 724678c8-b515-4ea0-9171-2e0783d71eee ext4 VMWare

 the largest is the NTFS that was my storage when my computer was a windows box. There's a 100mb mbr and the other is 160gig partition that i used to have ubuntu until i got my raid up. I had everything installed and running on the raid. I decided to delete the 160 gig and make it storage and that is when my problem happened. I am not dual booting but i had in the past.

---

### Post by darkod on 2013-03-21
OK. If not dual booting it's better to use mdadm SW raid but if you had the fakeraid from before when you were dual booting, that would mean destroying the array and redoing it as SW raid.

What I would do in your place:
1. Since ubuntu can work with bios boot on gpt I would go into bios and disable uefi boot. Set the setting to Legacy Only or depending how it's called in your bios. That will get uefi boot out of the way.
2. Boot the machine with the ubuntu cd in live mode, activate the fakeraid if not activated by default, go into the installation with chroot and purge reinstall grub2. I suggest purge reinstall because of the change to bios boot from uefi. That will also make sure grub2 is installed as new. The grub2 destination would be /dev/sdc and you would have to set bios to boot from the 1TB disk first.

If you need help with the chroot procedure, let as see the whole partition setup by booting into live mode, activating the fakeraid and posting the parted output:
```
sudo dmraid -ay
sudo parted -l (that's small L)
```

If you can, in the parted output specify which partition from the raid is your root, but I think it would be obvious. It all depends on your fakeraid partitions.

That is what I would do, if you don't like the idea, let us know.

---

### Post by mysteron75 on 2013-03-21
This fakeraid was setup as a ubunutu install. Windows has not touched this raid.  Is there no way to get to keep my setup and fix grub?

---

### Post by darkod on 2013-03-21
There is, only mdadm would have been much better option than fakeraid.

What do you think about the idea to use legacy (bios) boot and reinstall grub2? If you would like to try, post the output of the parted command as per my previous post and I can help with the chroot commands you need.

---

### Post by mysteron75 on 2013-03-21
I like what you have proposed. I am just thinking about all the wine bottles i have installed lol!!!

---

### Post by darkod on 2013-03-21
Well, when you make up your mind post the parted output. :)

---

### Post by mysteron75 on 2013-03-21
How do you use mdadm?

---

### Post by darkod on 2013-03-21
It depends which cd (ISO) you are using. The Server and Alternate CDs have it included, the Desktop (live cd) doesn't, unless they changed it for the latest version 12.10. So, with the alternate or server cd you can do it in the installer, with the desktop cd you need to load live mode, add the mdadm package and make the raid devices first, only then you start the install from the Install icon on the desktop.

In any case you can use live mode and prepare the partitioning and raid devices first, regardless which cd you will use.

Do you need the exact commands to create array? But redoing the array with mdadm will destroy the current data, you will have to move it temporarily.

---

### Post by mysteron75 on 2013-03-21
I will be using 12.10 live cd. i have never used mdadm before. So i will need to know what commands to use.

---

### Post by darkod on 2013-03-21
OK. Are we talking about raid0 or raid1? If you want to use raid0, there has to be a separate /boot partition outside the raid. If using raid1 this is not necessary.

First of all delete your existing fakeriad array into the raid settings, and then in ubuntu live mode destroy the raid meta data from the disks:
```
sudo dmraid -Er /dev/sda
sudo dmraid -Er /dev/sdb
```

Another important thing to know about mdadm is that all separate mount points you want need a separate partition. After that the raid is assembled on OS level. So, for a simple root + swap installation with raid1, you need two partitions on each disk, one bigger for root and one smaller for swap.

You can create this partitions with Gparted for example. When creating the bigger partition select the Use As: Physical device for raid, or similar. When creating the swap partitions select Use As: swap area.

After the partitions are done, open the terminal, install mdadm and create the arrays like this (assuming the bog partition on both disks is sda1 and sdb1):
```
sudo apt-get install mdadm
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
```

Check if it's created and synced with:
```
cat /proc/mdstat
```

After it's synced, start the installer with the Install icon without rebooting the machine. Select the Something Else manual option and in the partitions list you should see the md0 device. Select it, click the Change button below and select the Use As: ext4, mount point /.
Select both swap partitions and again set the Use As: swap area. Swap doesn't use mount point so that field will be greyed out.

Device for bootloader select /dev/sda right now. That should be it. Finish the installation and set bios to boot from /dev/sda.

---

### Post by mysteron75 on 2013-03-21
I did the software raid and it worked. WHen i do the install i get this error


[IMG]http://ubuntuforums.org/image/png;base64,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[/IMG]

I setup my 2 ssds as a raid 0 and put the bootloader on  my sdc and it fails. I have done this on previous installs and it worked but not it doesnt. I ran the boot info script and i got

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

md0: ___________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1             512   916,783,615   916,783,104 Data partition (Windows/Linux)
/dev/sda3     916,783,616   950,218,751    33,435,136 Swap partition (Linux)
/dev/sda25 868,804,802,739,790,453             0-868,804,802,739,790,452 -
/dev/sda26              04,159,542,507,221,225,7974,159,542,507,221,225,798 -
/dev/sda27 4,611,686,021,648,613,3754,611,686,021,648,613,375             1 -
/dev/sda28 4,611,686,021,648,613,3754,611,686,021,648,613,375             1 -
/dev/sda61  1,000,235,007            34-1,000,234,972 -
/dev/sda65          2,048   969,140,223   969,138,176 Data partition (Windows/Linux)
/dev/sda66    969,140,224 1,000,232,959    31,092,736 Swap partition (Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,640,847,844 1,640,845,797   7 NTFS / exFAT / HPFS
/dev/sdc2    *  1,640,849,408 1,641,043,967       194,560   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/md0p1       0bc9a2f2-f2d2-4ad3-92d2-dbd20df30f17   ext4       
/dev/md0p2       c6c0882a-d82a-49c0-863c-c11dc4336845   swap       
/dev/sda         bae12b6c-67c9-1615-42d9-6060312e963a   linux_raid_member ubuntu:0
/dev/sdb         bae12b6c-67c9-1615-42d9-6060312e963a   linux_raid_member ubuntu:0
/dev/sdc1        F4CCC20FCCC1CC54                       ntfs       Storage
/dev/sdc2        DB3F-2AA5                              vfat       
/dev/sr1                                                iso9660    Ubuntu 12.10 amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
fc4e2ba9010000000000000000000000
Unknown GPT Partiton Type
1000000000000000a032cf1d00000000
Unknown GPT Partiton Type
00000100ffffffffffffffffffffffff
Unknown GPT Partiton Type
ffffffffffffffffffffffffffffffff
Unknown GPT Partiton Type
4546492050415254000001005c000000

========= Devices which don't seem to have a corresponding hard drive: =========

sdd 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
  No volume groups found

---

### Post by mysteron75 on 2013-03-21
crap the pic did not post. It told  me grub failed to install and the ubuntu install stopped

---

### Post by darkod on 2013-03-22
Did you join whole disks or partitions in the md device? You used /dev/sda or /dev/sda1?

I think your SSDs have messed up partition tables. In your place i would write new empty tables, you can't keep the data anyway. Look at the boot info, sdb is not even shown in the fdisk results, and sda has lots of weird partitions.

Since you decided to do raid0 did you make a raid1 device for /boot?

Without chaning anything, boot the machine in live mode, install mdadm, assemble the devices, and post the output of parted:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
sudo parted -l (small L)
```

Don't touch anything else, just post this because I want to see it as it is now. First lets see how it looks right now.

---

### Post by mysteron75 on 2013-03-22
after the sudo parted  -l i get

Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?        
 I typed yes and i got

Error: /dev/sdb: unrecognised disk label                                  

Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  840GB  840GB   primary  ntfs
 2      840GB   840GB  99.6MB  primary  fat32        boot


Model: Linux Software RAID Array (md)
Disk /dev/md0: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name  Flags
 1      1049kB  496GB  496GB   ext4
 2      496GB   512GB  15.9GB  linux-swap(v1)


Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: Can't have a partition outside the disk!                           
ubuntu@ubuntu:~$

---

### Post by darkod on 2013-03-22
As I suspected, a real mess. On sda you have remains of gtp table because if the disk had gpt table and you use windows to create new msdos table it doesn't delete the backup gpt table. It leaves it there and later you can get issues.

sdb is not even recognized as a disk.

On another note, why did you make gpt table on md0? Any particular reason for that?
And you didn't create separate /boot array which I said you need to do if you want / on raid0. /boot can't be inside raid0.

I assume you don't mind destroying the array since it's new and there should be no data to lose on it. Here is what I would do:
1. Go into bios and make sure you use only Legacy boot, not uefi boot. Disable uefi boot.
2. Boot into live mode and remove the dmraid meta data, if you didn't do this yet.
3. Open terminal and write new msdos tables for sda and sdb.
```
sudo parted /dev/sda
mklabel msdos
select /dev/sdb
mklabel msdos
quit
```
That should write new empty msdos tables on both sda and sdb.
4. Open Gparted (or use parted) and again create following partitions on both disks:
-create small 500MB partition for boot first
-create the root partition (all the rest minus swap size)
-create swap
Create all partitions as primary and the partitions for boot and root create them as physical device for raid, not as ext4.
5. Make the md0 for boot and md1 for root and wait till they sync:
```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
sudo mdadm --create /dev/md1 --level=0 --raid-devices=2 /dev/sda2 /dev/sdb2
```
6. Start the installer and use the created md0 as ext4 with mount point /boot, the md1 as ext4 with mount point /, and both swap partitions as swap area (no need to raid the swap).
7. Put the bootloader on /dev/sda. It should work and install on sda without problems now. Later you will add it to sdb once you have the system up and running.

See if that works.

---

### Post by mysteron75 on 2013-03-22
When i am creating the partitons in gpart, what should i format the boot partition and the root partition ie. ext4 ext2 etc? I am reading your  line you typed 

Create all partitions as primary and the partitions for boot and root create them as physical device for raid, not as ext4. 

I just want to make sure i get the formating right

---

### Post by darkod on 2013-03-23
When using mdadm the filesystem like ext4 goes on the md device, not the physical partitions like sda1, sda2, etc. I don't have garted in front of me right now but when creating the partition there should be option like raid. If not create them as RAW, without any filesystem. In that case add a raid flag with parted after creating the partition with gparted first.
You can also use parted at the command line to create them, it creates partitions with no filesystem by default.

---

### Post by mysteron75 on 2013-03-23
Gets to the end and it gets a fatal error when grub is trying to install on /dev/sda.I get the installation compete popup behind this error. It gives me the the options to choose another device to install the bootloader on , continue without a boot loader or cancel installation. I have tried other drives and i get nothing.

---

### Post by mysteron75 on 2013-03-25
i figured it out. i just reinstall grub at the end of the install before rebooting with boot repair

---

