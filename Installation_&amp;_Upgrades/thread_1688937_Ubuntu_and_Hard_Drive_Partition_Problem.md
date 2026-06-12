---
title: "Ubuntu and Hard Drive Partition Problem"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by nvdkgm on 2011-02-16
What I did to get me in this mess:
I had Windows XP and another OS booting side by side. I tried installing Ubuntu over the second OS and noticed some partition errors. Ubuntu installed still but Windows XP and the OEM Recovery section on C:, for the netbook, just disappeared more or less from the boot menu. I tried mounting the volume from Ubuntu that was installed and it threw up an error.

"Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x00000000  size: 4096  usa_ofs: 0  usa_count: 65535: Invalid argument
Actual VCN (0x0) of index buffer is different from expected VCN (0x1).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, ..."

Then I tried TestDisk based on a quick scan on support forums no knowing what it would fully do and I hit GRUB rescue.
Now since I was in this problem before once I used a liveUSB and tried ...
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Now it goes past the BIOS and straight to the OEM Recovery portion. And that's good and all that I can get Windows XP back, although I am not sure on what partition it would install. But what if I want to fix all of this and get the data.

What should I do now? Please explain things in a more simplistic manner as I am new but getting used to of Linux. Thank you in advance.

---

### Post by srs5694 on 2011-02-16
I don't recommend you attempt any potentially destructive recovery procedures (anything that would write to the disk) until you fully understand the nature of the problem and/or have done a full low-level backup of the drive (using, for instance "dd if=/dev/sda of=/dev/sdb" to back up /dev/sda to another disk, /dev/sdb). You could make things worse if you write changes to the disk.

I recommend you run the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) from a Linux emergency boot and post the RESULTS.txt file that it produces, either as an attachment or between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. This will provide us with additional diagnostic information.

---

### Post by nvdkgm on 2011-02-16
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
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

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    10,233,404    10,233,342   b W95 FAT32
/dev/sda2          10,233,405   263,838,143   253,604,739   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16026435072 bytes
255 heads, 63 sectors/track, 1948 cylinders, total 31301631 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    31,301,630    31,301,568   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0159-6699                              vfat       PQSERVICE                     
/dev/sda2        3E504CAB504C6C29                       ntfs       ACER                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D039-8751                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)

=============================== StdErr Messages: ===============================

ls: reading directory sda2/: Input/output error
```

---

### Post by srs5694 on 2011-02-16
It looks like your Windows installation is damaged, and there's no trace of a Linux installation on /dev/sda.

If you have important data on /dev/sda, I recommend you first do a low-level backup to another disk, as in "sudo dd if=/dev/sda of=/dev/sdc", with a suitable blank disk available as /dev/sdc. This will take a while to complete, but it will give you a way to recover should you make matters worse.

Backup in hand, you'll need to use Windows recovery tools to attempt to recover the data from the Windows disk. Linux lacks any but the most trivial NTFS repair tools, so there's not much you can do from Linux. (An exception: If things are really bad on that disk, you could use [PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) to attempt to recover individual files.) If you need more help with Windows recovery, I recommend you post to a Windows forum, since your disk is basically all-Windows at the moment. (The one exception is that you've got LILO in your MBR.)

There's a possibility that you've got a hard disk hardware problem. You can investigate this by using GSmartControl or various other utilities to check the hardware status. If the hard disk is going bad, you should replace it ASAP. Such problems are not repairable. It's not certain that you've got such a problem, though. I mention it only because it's not clear to me what triggered your initial problems; it could have been a bug, random data corruption, cosmic rays, bad hardware, or whatever.

---

### Post by nvdkgm on 2011-02-16
A couple of question and comments.

-If I use the Recovery partition on C: will it work and what will it install to? Will that also restore the partition tables?
-I was installing Linux and had set the partition to overwrite a section I did not want and so I aborted the install mid-way after which Windows XP still started up fine. Following this I installed Ubuntu properly, or so I hope, to the second partition and saw the errors which could explain a lot. I am hoping this is a recoverable gaffe I made.
-I do not know how to work the low level back-up so is there any documentation about how to do that? I have a netbook so a USB is what I will  be off loading the data to.
-Linux and Windows XP are in fact installed and Ubuntu did work before the GRUB rescue.

I do know about PhotoRec but have never used it so that will be something to look into.

What I want to know is there any other data that you could use that would help narrow the problem down or does it even seem remotely repairable. If not I am going to have to learn SFTP and stat because I am running off of a liveUSB and this is the only computer I have right now.

---

### Post by srs5694 on 2011-02-17
There is no evidence that you have Linux installed. Perhaps it's installed via WUBI or in a virtual machine, but your partition tables have no Linux partitions and the Boot Info Script has found no Linux filesystems. Thus, you're basically on a Windows-only system (aside from LILO in your MBR). I'm not a Windows expert, so I can't advise you on what Windows will do for recovery.

As to dd, I provided the complete syntax for its use in this specific case. If you need more information, type "man dd" at a shell prompt or find a Web site on dd, such as [this one.](http://www.debianhelp.co.uk/ddcommand.htm)

---

