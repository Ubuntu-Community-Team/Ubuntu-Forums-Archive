---
title: "Grub error"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by nipunreddevil on 2011-02-24
System config:
Ubuntu 10.10 installed with wubi inside win vista
I followed the procedure at [PHP]http://www.android-x86.org/documents/installhowto[/PHP] but ended up running the script ```
# zcat android-x86-1.6-r2_usb.img.gz | dd of=/dev/sda1
```
Now i am not able to boot as the grub loader is gone missing.
There's a blank screen with the words "Grub" and no progress.
I tried using LiveCd both Ubuntu and Fedora to try and recover Grub to no avail.
Upon running livecd,i am not able to mount my hard disk.
Messed up.What can be done to get back Windows and Ubuntu running?

---

### Post by nipunreddevil on 2011-02-24
If not get everything back working,is there any way to get my data.

---

### Post by Rubi1200 on 2011-02-24
Hi,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by nipunreddevil on 2011-02-24
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 1 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on the same partition for 
                       /boot/grub/stage2.
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 1 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on the same partition for 
                       /boot/grub/stage2.
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 1 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on the same partition for 
                       /boot/grub/stage2.
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 1 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on the same partition for 
                       /boot/grub/stage2.

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
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

/dev/sda1    *          2,048   164,153,343   164,151,296   7 HPFS/NTFS
/dev/sda2         164,153,344   307,861,503   143,708,160   7 HPFS/NTFS
/dev/sda3         307,861,504   471,699,455   163,837,952   7 HPFS/NTFS
/dev/sda4         471,700,530   488,392,064    16,691,535   5 Extended
/dev/sda5         471,702,578   471,849,689       147,112  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 16.0 GB, 16039018496 bytes
256 heads, 25 sectors/track, 4894 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,224    31,326,207    31,323,984   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2: PTTYPE="dos" 
/dev/sda3: PTTYPE="dos" 
/dev/sda4: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdc1        7F0F-CC6B                              vfat       SAGAR                         
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/SAGAR             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by Rubi1200 on 2011-02-24
Is sda1 your Windows installation?

There are 2 main problems:

1. you have grub installed in the boot sectors except sda5 (did you install Ubuntu to its own partition and do a Wubi install?)

2. the file-systems are not mounting

Do you have the Windows installation/recovery CD?

---

### Post by nipunreddevil on 2011-02-24
I did a Wubi Install in drive E and don't have Windows recovery.

---

### Post by oldfred on 2011-02-24
That the script or Ubuntu will not mount the windows/NTFS partitions says you have some sort of partition issue. I would always try chkdsk first after repairing the boot sector. But windows may not see the partitions with grub legacy installed to the partition. They have to have  a NTFS signature.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Then download this and run chkdsk.

Download the correct windows repair CD for your windows.
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If chkdsk does not work, then I would try testdisk, but lets see what chkdsk says. If it gives any errors be sure to rerun until there are no errors.

---

### Post by Rubi1200 on 2011-02-25
I agree with oldfred regarding how to approach this issue. Be very careful and do not attempt to write anything to disk.

Take one step at a time, reporting back here if you encounter problems.

---

