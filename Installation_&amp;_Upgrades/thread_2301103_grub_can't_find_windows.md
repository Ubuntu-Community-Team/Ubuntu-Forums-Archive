---
title: "grub can't find windows"
date: 2015-10-30
forum: Installation &amp; Upgrades
---

### Post by jeff147 on 2015-10-30
hey yall for some god dang reason grub2 can't find the wind'ers installation majigger. i've ran `update grub` or whatever and os-prober doesnt tell me any info. i downloaded a thingy majigger called bootinfoscript and here's the results:

> 
\                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   270,292,991   270,290,944   7 NTFS / exFAT / HPFS
/dev/sda2         372,695,040   488,392,703   115,697,664   7 NTFS / exFAT / HPFS
/dev/sda3    *    270,292,992   357,070,335    86,777,344  83 Linux
/dev/sda4         357,070,846   372,695,039    15,624,194   5 Extended
/dev/sda5         357,070,848   372,695,039    15,624,192  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        72F81449F8140DCB                       ntfs       SSD MASTERRACE
/dev/sda2        A8224746224718A8                       ntfs       Windows7
/dev/sda3        66d770cf-c84d-447d-83c1-0259f3dc3c16   ext4       
/dev/sdb         2678-0495                              vfat       NO

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sdb         /media/thor/NO           vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)


thank u all and god bless u

---

### Post by oldfred on 2015-10-30
Windows generally looks ok.
Most of the time os-prober does not find Windows because it is hibernated or needs chkdsk.
You need to run chkdsk from a Windows repairCD or flash drive.
You may be able to temporarily reinstall a Windows boot loader and use f8 to get into the internal Windows repair console. Grub only boots working Windows, so you need to make sure Windows boots ok on its own, then restore grub and boot Ubuntu. And run the sudo update-grub again.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

      [/URL]
 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

    [URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by yancek on 2015-10-30
Your bootinfo script is missing the majority of data it usually outputs for whatever reason.  In addition to the suggestions above, not that sda3, the Linux partition is marked as bootable/active which is not necessary but is necessary for windows so set the windows partition as active.  Probably sda2 as it seems to have boot files on it.

---

