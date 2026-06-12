---
title: "Screwed up, stuck in grub rescue, need help ASAP"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by erikvduyn on 2010-11-16
So I wanted to switch distros and I was apparently supposed to do that by formatting the partitions with Linux and booting from a Live USB/CD to install it. I did that, went into setup and couldn't remember what partition I needed for /home, so I decided I wanted to boot into Windows to check. However, all it gives me is the grub rescue dialog.

How do I fix this?

---

### Post by drs305 on 2010-11-16
You can
1) try to do it yourself by following the instructions on booting from the grub rescue prompt:
[http://ubuntuforums.org/showthread.php?t=1594052]("http://ubuntuforums.org/showthread.php?t=1594052")
or
2) boot the LiveCD and run the boot info script from this link and post the contents of RESULTS.txt
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")
Please post the RESULTS.txt content between 'code' tags, which you generate by pressing the # icon.

---

### Post by erikvduyn on 2010-11-16
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 938324583.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    25,382,699       208,845   7 HPFS/NTFS
/dev/sda3          25,382,700   938,324,519   912,941,820   7 HPFS/NTFS
/dev/sda4         938,324,581 1,250,258,624   311,934,044   f W95 Ext d (LBA)
/dev/sda5         938,324,583   958,791,329    20,466,747   7 HPFS/NTFS
/dev/sda6         958,791,393   967,594,949     8,803,557   7 HPFS/NTFS
/dev/sda7         967,595,013 1,144,599,119   177,004,107   7 HPFS/NTFS
/dev/sda8       1,144,599,183 1,250,258,624   105,659,442   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16001269760 bytes
255 heads, 63 sectors/track, 1945 cylinders, total 31252480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    31,252,479    31,252,417   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C26CD4A86CD4990D                       ntfs       PQSERVICE                     
/dev/sda2        0208D4FD08D4F121                       ntfs       SYSTEM RESERVED               
/dev/sda3        CEACD691ACD67385                       ntfs       Acer                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        01CB85ABCFF54290                       ntfs       linux mount                   
/dev/sda6        01CB85ABD1FE5900                       ntfs       linux swap                    
/dev/sda7        01CB85ABD3D93380                       ntfs       linux home                    
/dev/sda8        01CB6634E143CA80                       ntfs       Schoolwerk                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D61C-6964                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by drs305 on 2010-11-16
According to RESULTS.txt, you don't have any Ubuntu installations.

You can regain the ability to boot Windows by using the Windows repair disk or installing *lilo* from the LiveCD.

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
lilo will give you a few warning messages - just disregard them as you aren't really doing a full install of lilo.

Once you run the above command Windows should boot again if the Windows boot files haven't been altered.

---

