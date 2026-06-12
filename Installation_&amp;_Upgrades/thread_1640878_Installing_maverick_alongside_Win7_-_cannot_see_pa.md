---
title: "Installing maverick alongside Win7 - cannot see partitions"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by verbal.kint on 2010-12-08
I'm after getting a lenovo s10-3t manufacturer refurb and I'm trying to dual boot the existing Win7 with ubuntu. When I try to install ubuntu it does not recognise the existing NTFS partitions in GParted, it just shows as unallocated space.

Here are the results of the infamous boot info script:

```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       409599 sectors, but according to the info from fdisk, 
                       it has 417626 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       393564159 sectors, but according to the info from 
                       fdisk, it has 393576434 sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63. According to the info in the boot 
                       sector, sda5 has 63475711 sectors, but according to 
                       the info from fdisk, it has 63488816 sectors.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       417,689       417,627   7 HPFS/NTFS
/dev/sda2             417,690   393,994,124   393,576,435   7 HPFS/NTFS
/dev/sda3         393,994,125   457,483,005    63,488,881   5 Extended
/dev/sda5         393,994,188   457,483,004    63,488,817   7 HPFS/NTFS
/dev/sda4         457,483,005   488,392,064    30,909,060   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 7889 MB, 7889485824 bytes
243 heads, 62 sectors/track, 1022 cylinders, total 15409152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62    15,397,451    15,397,390   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4CDC0BCCDC0BAEF0                       ntfs                                     
/dev/sda2        10AC0DF4AC0DD4DE                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        F8AA16C2AA167CF6                       ntfs       LENOVO_PART                   
/dev/sda5        12F458ADF45894B7                       ntfs       LENOVO                        
/dev/sda: PTTYPE="dos" 
/dev/sdc1        FC2E-CDDD                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


```

Attached is what the partitions look like in Windows 7.


I can tell from the bootinfo that there seems to be some inconsistency in the partition sizes although I dont fully understand the problem.

Is it possible to repair this without effecting the current windows install?

One of the partitions is a recovery partition that I would need to reinstall windows, because its a netbook I am not able to burn a recovery CD so its a priority to hold on to a copy of windows.

---

### Post by sikander3786 on 2010-12-08
I am unable to figure out any problems with your partition setup whatsoever.

I would suggest to fire up the Ubuntu installer, proceed to the partitioning step and see if it is able to recognize the partitions. If yes, you can definitely create/delete/manage partitions there.

If that doesn't either show up your partitions, go to your computers Bios and change the HDD mode to 'ahci' or 'compatible' and try again.

Others might have better suggestions than mine ;-)

---

### Post by coffeecat on 2010-12-08
Gparted showing the whole disc as unallocated when there's a problem with the partition table is a known issue. [See here.]("http://www.rodsbooks.com/missing-parts/index.html") However, the problem described in that link - an extended partition apparently extending beyond the physical limit of the drive - is not what you have. The only things I can see (possibly) wrong from your bootscript output is the grumbling about the number of sectors in sda5, and the end and start sectors for sda3 and sda4. They are the same: 457,483,005. That doesn't seem right. I would have thought they would need to be different, perhaps adjacent, numbers.

The only things I can suggest are to edit the partition table according to that link to adjust the end sector of sda3 to make it 457,483,004, although I will admit I don't have enough experience to be sure that is the correct thing to do.

More drastically, you could back up whatever is on sda5 and sda4 and then use Windows to delete the corresponding LENOVO and LENOVO_PART partitions. Hopefully that will remove the problem and Gparted will then see sda1 and sda2 and the rest as (correctly) unallocated which you can then partition yourself. The trouble with that is that one of your LENOVO* partitions is probably your OEM restore partition. If you have a utility to make Lenovo restore DVDs, I suggest you use it first.

Health warning: if you do the latter and the problem is elsewhere in the partition table you will have lost sda3,4,5 to no good purpose. Sorry, but I don't know whether this is the right thing to do.

---

### Post by Rubi1200 on 2010-12-08
Hi,
there are 2 things I think you need to do.

1. run chkdsk a few times to make sure Windows is "happy" with the changes you made (which may account for the inconsistencies you noticed).

2. read the information in this link about changes to the Ubuntu installer:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by verbal.kint on 2010-12-08
thanks for the quick responses.

I'm just running some chkdsks and defrags at the moment, i'll check afterwards if gparted can pick the partitions up.

Where is the partition info stored in the boot sector as distinct from where the fdisk utility is pulling the info from? One of the main things that jumped out at me was that the boot sector has sda 5 starting at sector 63, i thought it should be 393,994,188.

Can I make an ISO of the OEM partition that would allow me to restore if I mess it up? I don't have access to a USB DVD burner, i might be able to get one when i go home at Christmas but i'd prefer to sort it sooner.

---

### Post by coffeecat on 2010-12-08
> **verbal.kint said:**
> One of the main things that jumped out at me was that the boot sector has sda 5 starting at sector 63, i thought it should be 393,994,188.

Yes, I've seen that before in some people's Windows partitions that are not partition 1, whereas sector 63 is the start of partition 1. Sorry, I don't understand that.

> **verbal.kint said:**
>  Can I make an ISO of the OEM partition that would allow me to restore if I mess it up? I don't have access to a USB DVD burner, i might be able to get one when i go home at Christmas but i'd prefer to sort it sooner.

I would prefer to use a Windows backup imaging application. If you have access to Acronis True Image, that would be a good choice. Alternatively, there's a free version of Macrium Reflect here:

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

I've used it to image and restore Windows C: partitions and it can image other NTFS partitions although I've not used it for this. One of the nice things about Macrium (apart from being free) is that the rescue CD you make with it is Linux based.

---

