---
title: "External HDD Woes with 10.10"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by drgame93 on 2011-02-06
Hello I am having issues installing 10.10 on my external HDD. 

The first time I attempted to install the OS I got to a blank screen with a cursor (But the install completed sucessfully)

On my second Attempt i managed to get to grub-rescue.

Basically I created a new partition for the OS, it was an ext4 filesystem, and the mount point was "/" it was a primary partition. Then I created a swap area. The boot went to my External HDD. And upon restarting and booting into grub-rescue.

The third time I can't exactly remember what happened but my hdd didn't even appear in my boot option list.

So what am I doing wrong? And how can I fix this?

---

### Post by presence1960 on 2011-02-06
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with the external HDD connected. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by drgame93 on 2011-02-06
EDIT: After Several Tries it finally worked.

```
            Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdf and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdf5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdf6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdf6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,221,582,599 1,221,582,537   7 HPFS/NTFS
/dev/sda3       1,221,582,600 1,250,258,624    28,676,025   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63   614,389,859   614,389,797   7 HPFS/NTFS
/dev/sdf2         614,389,921 1,474,542,089   860,152,169   f W95 Ext d (LBA)
/dev/sdf5         614,389,923   819,186,479   204,796,557   7 HPFS/NTFS
/dev/sdf6         819,186,543 1,474,542,089   655,355,547   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A896FF3196FEFF1E                       ntfs       HP                            
/dev/sda3        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 
/dev/sda: PTTYPE="dos" 
/dev/sdf1        01CBC3BDAE2A15A0                       ntfs       Drew's Files                  
/dev/sdf2: PTTYPE="dos" 
/dev/sdf5        01CBC3BDB28B9B00                       ntfs       Mom's Files                   
/dev/sdf6        17EB-20C6                              vfat       PS3                           
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdg 
```

---

### Post by presence1960 on 2011-02-08
> **drgame93 said:**
> EDIT: After Several Tries it finally worked.

```
            Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdf and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdf5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdf6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdf6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,221,582,599 1,221,582,537   7 HPFS/NTFS
/dev/sda3       1,221,582,600 1,250,258,624    28,676,025   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63   614,389,859   614,389,797   7 HPFS/NTFS
/dev/sdf2         614,389,921 1,474,542,089   860,152,169   f W95 Ext d (LBA)
/dev/sdf5         614,389,923   819,186,479   204,796,557   7 HPFS/NTFS
/dev/sdf6         819,186,543 1,474,542,089   655,355,547   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A896FF3196FEFF1E                       ntfs       HP                            
/dev/sda3        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 
/dev/sda: PTTYPE="dos" 
/dev/sdf1        01CBC3BDAE2A15A0                       ntfs       Drew's Files                  
/dev/sdf2: PTTYPE="dos" 
/dev/sdf5        01CBC3BDB28B9B00                       ntfs       Mom's Files                   
/dev/sdf6        17EB-20C6                              vfat       PS3                           
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdg 
```

According to the output above you do not have ubuntu installed. Did you miss some of the output?

---

### Post by drgame93 on 2011-02-09
I was running the boot script from the live cd, and I may have not had it re-installed to my external. So I will re-install and then re-post the results.

Edit: Ok I no longer will be attempting to install Ubuntu to hdd, I am now focusing on my old pc I am currently re-habing, and I have 10.04 install on it now.

---

