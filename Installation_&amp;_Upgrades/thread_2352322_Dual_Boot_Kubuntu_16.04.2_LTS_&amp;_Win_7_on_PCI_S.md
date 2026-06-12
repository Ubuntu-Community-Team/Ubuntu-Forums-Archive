---
title: "Dual Boot Kubuntu 16.04.2 LTS &amp; Win 7 on PCI SSD"
date: 2017-02-11
forum: Installation &amp; Upgrades
---

### Post by shadragon on 2017-02-11
Hi Guys and Gals, 

I have a Win7 PC set up on an OCZ Revodrive 3 PCIe SSD with a RAID 1 3TB set of NTFS data drives.  

I installed Ubuntu 16.04.1 LTS on a separate 2TB HD and am trying to get it to dual boot using Grub2. However, when running Kubuntu, the Windows install on the OCZ drive is not recognized. 

I can force a boot to either OS by going into BIOS and selecting the Revodrive or the HD as needed, but it is a PIA. I'd like to get Grub2 working. Any ideas? 

Drive info enclosed below. 


          ```
 Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 97 for .
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.
 => No boot loader is installed in the MBR of /dev/sde.


sda1: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda2: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


sdb2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 262178.
    Operating System:  
    Boot files:        


sdb3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb3 starts at sector 2929817634. The info in boot 
                       sector on the starting sector of the MFT is wrong. The 
                       info in the boot sector on the starting sector of the 
                       MFT Mirror is wrong. According to the info in the boot 
                       sector, sdb3 has 2929557307 sectors, but according to 
                       the info from fdisk, it has -291668165 sectors.
    Operating System:  
    Boot files:        


sdc1: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''


sdc2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdc2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc2 starts at sector 262178.
    Operating System:  
    Boot files:        


sdc3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdc3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc3 starts at sector 2929817634. The info in boot 
                       sector on the starting sector of the MFT is wrong. The 
                       info in the boot sector on the starting sector of the 
                       MFT Mirror is wrong. According to the info in the boot 
                       sector, sdc3 has 2929557307 sectors, but according to 
                       the info from fdisk, it has -291668165 sectors.
    Operating System:  
    Boot files:        


sdd1: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''


sdd2: __________________________________________________________________________


    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________
Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048 3,840,129,023 3,840,126,976  83 Linux
/dev/sda2       3,840,131,070 3,907,028,991    66,897,922   5 Extended
/dev/sda5       3,840,131,072 3,907,028,991    66,897,920  82 Linux swap / Solaris




Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2         262,178 2,929,817,633 2,929,555,456 Data partition (Windows/Linux)
/dev/sdb3   2,929,817,634 2,638,149,469  -291,668,164 Data partition (Windows/Linux)


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdc1                   1 4,294,967,295 4,294,967,295  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdc1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdc2         262,178 2,929,817,633 2,929,555,456 Data partition (Windows/Linux)
/dev/sdc3   2,929,817,634 2,638,149,469  -291,668,164 Data partition (Windows/Linux)


Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdd1    *          2,048       915,704       913,657   7 NTFS / exFAT / HPFS
/dev/sdd2             915,712   468,879,359   467,963,648   7 NTFS / exFAT / HPFS


/dev/sdd2 ends after the last sector of /dev/sdd


Drive: sde _____________________________________________________________________
Disk /dev/sde: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


Invalid MBR Signature found.




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        411b0522-bc33-456a-a85d-02108d142ca1   ext4       
/dev/sda5        d1163b45-b41b-4b47-9601-490550585a4d   swap       
/dev/sdb1                                                          
/dev/sdb2        01D0E954132F51D0                       ntfs       Data
/dev/sdb3        01D0E95416916890                       ntfs       Store
/dev/sdc1                                                          
/dev/sdc2        01D0E954132F51D0                       ntfs       Data
/dev/sdc3        01D0E95416916890                       ntfs       Store
/dev/sdd1                                                          


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sda1        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)



```

---

### Post by ajgreeny on 2017-02-11
Have you run command **sudo update-grub** to see if that finds Windows and adds it to grub?

I don't know if the fact that you have a Win7 PC set up on an OCZ Revodrive 3 PCIe SSD with a RAID 1 3TB set of NTFS data drives has any effect on this problem, but I suspect it may be the cause.

---

### Post by shadragon on 2017-02-11
I'm sure it's the OCZ revodrive causing the issue as the Linux side does not even recognize there is a partition there. 

Is there any way for me to manually edit this?

---

