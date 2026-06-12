---
title: "the attempt to mount a filesystem with type ext4 failed"
date: 2012-08-25
forum: Installation &amp; Upgrades
---

### Post by Meshal-USA on 2012-08-25
i have a problem when trying to install ubuntu.

my situation is that i have external hard drive, and i have a windows 7 on my internal hard drive.

when i try to install ubunutu i always get this error

[COLOR=Red]the attempt to mount a filesystem with type ext4[/COLOR] [COLOR=Red]in SCSI7 (0,0,0). partition #6 at / failed. you may resume partitioning from the partitioning menu[/COLOR]

i also tried installing it with ext3 and ext2 but i also have the same problem

could you help me solving this?

---

### Post by TheFu on 2012-08-25
After you boot from the liveCD, run **blkid** and paste the output here.

---

### Post by Meshal-USA on 2012-08-25
/dev/sr0: LABEL="Ubuntu 12.04.1 LTS amd64" TYPE="iso9660"

---

### Post by Meshal-USA on 2012-08-25
that's my laptop information:
[http://www.amazon.com/HP-g6-1c57dx-Multiformat-Built-microphone/dp/B005WE5752](http://www.amazon.com/HP-g6-1c57dx-Multiformat-Built-microphone/dp/B005WE5752)

and i'll try to install it again while i'm on the liveCD and take screenshots

---

### Post by TheFu on 2012-08-25
My mistake.
We need to know about the other 2 hard drives and the partitions on them. 

Did you go into the advanced setup, and create partitions for the OS, HOME and swap storage on the drive(s) that you want?  When partitioning, it is usually best to use logical partitions. Those don't have the 4 max limitation that primary partitions have - almost any number of logical partitions can be used. Linux will boot from and see all of them no problem.  Windows can use logical partitions too, but I'd only use them for data, not the OS.

There's a script that gathers all sorts of data about the hdds inside a system ... run that and post the output. ... where is that ... [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
It is a great tool, especially when you are trying to do something outside the normal.

---

### Post by Meshal-USA on 2012-08-25
> **Meshal-USA said:**
> that's my laptop information:
[http://www.amazon.com/HP-g6-1c57dx-Multiformat-Built-microphone/dp/B005WE5752](http://www.amazon.com/HP-g6-1c57dx-Multiformat-Built-microphone/dp/B005WE5752)

and i'll try to install it again while i'm on the liveCD and take screenshots


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=223177&stc=1&d=1345944243[/IMG]


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=223178&stc=1&d=1345944243[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=223179&stc=1&d=1345944243[/IMG]

---

### Post by Meshal-USA on 2012-08-25
you can see the screenshots i took. all the partitions were logical except for the boot partition...

---

### Post by Meshal-USA on 2012-08-25
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd /wubildr

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /wubildr

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb7: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   938,397,695   937,988,096   7 NTFS / exFAT / HPFS
/dev/sda3         938,397,696   968,450,047    30,052,352   7 NTFS / exFAT / HPFS
/dev/sda4         968,450,048   976,771,119     8,321,072   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059348992 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048       503,807       501,760  83 Linux
/dev/sdb2             505,854   488,396,799   487,890,946   5 Extended
/dev/sdb5             505,856     4,409,343     3,903,488  82 Linux swap / Solaris
/dev/sdb6           4,411,392    23,941,119    19,529,728  83 Linux
/dev/sdb7          23,943,168   488,396,799   464,453,632  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        20AAB6ACAAB67DBA                       ntfs       SYSTEM
/dev/sda2        22EA25D1EA25A1D1                       ntfs       
/dev/sda3        24049F64049F382E                       ntfs       Recovery
/dev/sda4        AC7D-193C                              vfat       HP_TOOLS
/dev/sr0                                                iso9660    Ubuntu 12.04.1 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  55 53 42 43 5c 06 00 00  00 04 00 00 00 00 0a 2a  |USBC\..........*|
00000010  00 00 00 00 00 00 00 02  00 00 00 00 00 00 00 dc  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  52 b6 0c 00 00 00 00 20  |........R...... |
000001c0  21 00 83 5b 3c 1f 00 08  00 00 00 a8 07 00 00 7c  |!..[<..........||
000001d0  1c 1f 05 fe ff ff fe b7  07 00 02 a0 14 1d 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc

---

### Post by TheFu on 2012-08-26
Ok, perfect.  Much better than screen shots, IMHO. I can copy/paste text. Thanks!


[LIST]
[*] Did you tell the installer that sdb1 will be /boot and set the "bootable" flag?
[*] Did you tell the installer that sdb6 will be / ?  (this might be /home)
[*] Did you tell the installer that sdb7 will be /home ? (this might be / )
[/LIST]
 For each of these, you should tell them which file system you'd like too. EXT4 is probably the best choice for all.  Then you need to tell the installer where to install grub,  sda or sdb.

I am not an expert on grub, so take these ideas as just that, ideas, not directions.  I haven't done this myself, so I do not know the best answer.
I'd be inclined to put grub on sdb first. You can always put grub on sda later. 

Hopefully, someone else will explain whether installing grub to sda when some of the OSes are on an external HDD is a good idea. It seems dangerous to me.  To boot off grub on SDB, tell the BIOS to do it or have a USB flash drive that can boot off either the 1st or 2nd disk.  Something like YUMI can do this and having a portable save-your-butt flash drive with DBAN, gparted, and a rescue Linux distro doesn't hurt.  A great use for those smaller 1G-2G flash drives.

BTW, I am not a fan of running any OS off USB2. It is slow.  Installing an OS off USB is fine. USB3 is much faster, but it has "queuing issues" that make it good for 1 or 2 tasks at a time, not an entire running OS. eSATA is fantastic for external drives. USB has always been flaky for me.

Anyway, I hope this makes sense.  If you already did those suggestions - bootable, partition labels, then I'm stumped.  Those settings are inside the advanced partitioning section of the installer.

---

### Post by oldfred on 2012-08-26
Was sdb ever part of a RAID set? RAID puts meta data on a drive and usually then gparted will not even work with it.

Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sda
Run chkdsk on any NTFS partitions even if they currently work.

Your first screen showing mounts & formats with grub2's boot loader installed to sdb looks correct. I just do not use /boot and might make / a bit large like 25GB but that is not critical.

---

### Post by Meshal-USA on 2012-08-26
> **TheFu said:**
> Ok, perfect.  Much better than screen shots, IMHO. I can copy/paste text. Thanks!


[LIST]
[*] Did you tell the installer that sdb1 will be /boot and set the "bootable" flag?
[*] Did you tell the installer that sdb6 will be / ?  (this might be /home)
[*] Did you tell the installer that sdb7 will be /home ? (this might be / )
[/LIST]
 For each of these, you should tell them which file system you'd like too. EXT4 is probably the best choice for all.  Then you need to tell the installer where to install grub,  sda or sdb.

I am not an expert on grub, so take these ideas as just that, ideas, not directions.  I haven't done this myself, so I do not know the best answer.
I'd be inclined to put grub on sdb first. You can always put grub on sda later. 

Hopefully, someone else will explain whether installing grub to sda when some of the OSes are on an external HDD is a good idea. It seems dangerous to me.  To boot off grub on SDB, tell the BIOS to do it or have a USB flash drive that can boot off either the 1st or 2nd disk.  Something like YUMI can do this and having a portable save-your-butt flash drive with DBAN, gparted, and a rescue Linux distro doesn't hurt.  A great use for those smaller 1G-2G flash drives.

BTW, I am not a fan of running any OS off USB2. It is slow.  Installing an OS off USB is fine. USB3 is much faster, but it has "queuing issues" that make it good for 1 or 2 tasks at a time, not an entire running OS. eSATA is fantastic for external drives. USB has always been flaky for me.

Anyway, I hope this makes sense.  If you already did those suggestions - bootable, partition labels, then I'm stumped.  Those settings are inside the advanced partitioning section of the installer.


> [LIST]
[*] Did you tell the installer that sdb1 will be /boot and set the "bootable" flag?
[*] Did you tell the installer that sdb6 will be / ?  (this might be /home)
[*] Did you tell the installer that sdb7 will be /home ? (this might be / )
[/LIST]

[COLOR="Red"]yes i did all of that, you can see what exactly i did in the screenshots i took.[/COLOR]

> For each of these, you should tell them which file system you'd like too. EXT4 is probably the best choice for all.  Then you need to tell the installer where to install grub,  sda or sdb.

I am not an expert on grub, so take these ideas as just that, ideas, not directions.  I haven't done this myself, so I do not know the best answer.
I'd be inclined to put grub on sdb first. You can always put grub on sda later. 

[COLOR="red"]i chose to put grub on sdb and i tried to put it in sda but when i did it i had a problem with windows MBR that required to use system repair from a CD to fix it.[/COLOR]

> BTW, I am not a fan of running any OS off USB2. It is slow.  Installing an OS off USB is fine. USB3 is much faster, but it has "queuing issues" that make it good for 1 or 2 tasks at a time, not an entire running OS. eSATA is fantastic for external drives. USB has always been flaky for me.

[COLOR="red"]i'm not a fan either, but i have no options. my internal hard drive has windows and i cannot install ubunutu alongside with it because of the system recovery partition and that windows is taking all the primary partitions. i tried wubi but it's very slow especially most of my work on ubuntu is on programming. if you have any way to dual boot ubuntu with windows please tell me i would really appreciate it.[/COLOR]

> Anyway, I hope this makes sense.  If you already did those suggestions - bootable, partition labels, then I'm stumped.  Those settings are inside the advanced partitioning section of the installer.

[COLOR="red"]it does make sense. thanks for those ideas but i have tried them all before and non of them worked.[/COLOR]

---

### Post by Meshal-USA on 2012-08-26
> **oldfred said:**
> Was sdb ever part of a RAID set? RAID puts meta data on a drive and usually then gparted will not even work with it.

Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sda
Run chkdsk on any NTFS partitions even if they currently work.

Your first screen showing mounts & formats with grub2's boot loader installed to sdb looks correct. I just do not use /boot and might make / a bit large like 25GB but that is not critical.

> Was sdb ever part of a RAID set?

[COLOR="Red"]no it wasn't, i took it out from my old laptop and now i'm using it as external hard drive[/COLOR]

> Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sda
Run chkdsk on any NTFS partitions even if they currently work.

[COLOR="red"]can i change sdb parameters from BIOS? if yes, can you tell me how? also could you tell me what parameters i should i use for ext4?[/COLOR]

> sudo dmraid -E -r /dev/sda
Run chkdsk on any NTFS partitions even if they currently work.

[COLOR="Red"]ok i'll check that and post it here.[/COLOR]

---

### Post by oldfred on 2012-08-26
sudo dmraid -E -r /dev/sdb  --not sda if external is sdb.

You have to run chkdsk from Windows on the Windows NTFS partitions.

What BIOS mode do you have drives set to. They should be AHCI, but if you have not installed AHCI drivers to Windows you should do that before changing. If setting is RAID or IDE it needs to be changes.

---

### Post by Meshal-USA on 2012-08-26
> **oldfred said:**
> sudo dmraid -E -r /dev/sdb  --not sda if external is sdb.

You have to run chkdsk from Windows on the Windows NTFS partitions.

What BIOS mode do you have drives set to. They should be AHCI, but if you have not installed AHCI drivers to Windows you should do that before changing. If setting is RAID or IDE it needs to be changes.

> sudo dmraid -E -r /dev/sdb  --not sda if external is sdb.

[COLOR=Red]i ran that in the terminal and this is what i got:[/COLOR]
[COLOR=Red]no raid disks and with names: "/dev/sdb"[/COLOR]

> What BIOS mode do you have drives set to. They should be AHCI, but if  you have not installed AHCI drivers to Windows you should do that before  changing. If setting is RAID or IDE it needs to be changes

[COLOR=Red]i really have no idea, how can i check BIOS mode?[/COLOR]

---

### Post by oldfred on 2012-08-26
Boot into BIOS and find the settings for your hard drive.

My BIOS before I changed it to AHCI. I used IDE for compatibility with XP but now do not boot XP.

---

### Post by Meshal-USA on 2012-08-26
i don't have that option in my bios mode

---

### Post by oldfred on 2012-08-26
What is under system configuration? Some laptops do have limited settings but hard drive mode of some sort should be somewhere.

---

### Post by Meshal-USA on 2012-08-26
> **oldfred said:**
> What is under system configuration? Some laptops do have limited settings but hard drive mode of some sort should be somewhere.

Language
Virtualization technology
fan always on
action keys mode
boot options

---

### Post by oldfred on 2012-08-26
Is boot options just the choices on which device to boot or are there settings there also?

What computer is this?

---

### Post by Meshal-USA on 2012-08-27
there are no other options, it's just a list of which devices to boot. it's hp pavilion g6 series, the i5 version.

here you can all the info on my laptop
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03045098&tmp_task=prodinfoCategory&cc=us&dlc=en&lang=en&lc=en&product=5193775](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03045098&tmp_task=prodinfoCategory&cc=us&dlc=en&lang=en&lc=en&product=5193775)

---

### Post by oldfred on 2012-08-27
Most i5 systems now are UEFI, it looks like yours it just BIOS and a very limited BIOS at that. Did you update to the newest BIOS?

---

### Post by Meshal-USA on 2012-08-27
yes i did, it was f.33 and i updated it yesterday to f.34 but it's still limited nothing changed

---

### Post by oldfred on 2012-08-27
I do not know if related to this, but you could try the alternative installer.

Just saw this from arpanaut's post in another thread.
There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)
From liveCD before install. 
sudo apt-get remove ubiquity-slideshow-ubuntu
or (ubiquity-slideshow-lubuntu) (and ubiquity-slideshow-xubuntu)
The Alternate iso is another option as it is text based and also does not use the slideshow.
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

If you have a local mirror that might be faster.

---

### Post by Meshal-USA on 2012-08-27
ok i'll try it and let you know. thank you so much for your help.

---

### Post by Meshal-USA on 2012-08-27
it worked!!! but now i have another problem

i think some drivers were not installed and also when i restarted it i got this error.

---

### Post by oldfred on 2012-08-27
Grub must not have fully installed correctly. That says the MBR has grub, but grub cannot find grub.cfg or some parts of grub.

Did you install to a large / (root) partition or high up on hard drive. Grub sometimes gets lost with some BIOS.

Try Boot-Repair to see what may be wrong.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

and/or

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Boot repair has an advance screen to help on a full chroot & grub reinstall.

---

### Post by Meshal-USA on 2012-08-27
i think the problem is that i installed grub on sdb, which i think now i should have installed it on sda. i'll try the boot repair and let you know what happens

---

### Post by Meshal-USA on 2012-08-27
[http://paste.ubuntu.com/1171027/](http://paste.ubuntu.com/1171027/)

---

### Post by Meshal-USA on 2012-08-27
i still have the same problem

---

### Post by oldfred on 2012-08-27
You are the second one I have seen with no UUIDs on several partitions. There must be a bug somewhere.

Partition table shows the sdb partitions, but the blkid only has a UUID for sdb5 swap.

Did you try booting from sdb? I would like to know if the bug that is erasing UUIDs is part of Ubuntu and its install or if somehow Boot-Repair is somehow doing it.

Without UUIDs nothing will work.

You need to do this for all partitions on sdb except sdb5.

sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid
and we will have to edit fstab with new UUIDs.

Run this to see new UUIDs.
# To clear cache and get new view:
sudo blkid -c /dev/null -o list

These are your partitions:
```

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    58,593,279    58,591,232  83 Linux
/dev/sdb2          58,595,326   488,396,799   429,801,474   5 Extended
/dev/sdb5          58,595,328    60,547,071     1,951,744  82 Linux swap / Solaris
/dev/sdb6          60,549,120   128,907,263    68,358,144  83 Linux
/dev/sdb7         128,909,312   488,396,799   359,487,488  83 Linux


```

Then you'll have to edit fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

---

### Post by Meshal-USA on 2012-08-27
that's what i'm trying to boot to. sdb is the one that has ubuntu.

i ran what you gave me and this is what i got "i'm using liveCD right now":







ubuntu@ubuntu:~$ sudo tune2fs -U random/dev/sdb1
tune2fs 1.42 (29-Nov-2011)
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
    [-i interval[d|m|w]] [-j] [-J journal_options] [-l]
    [-m reserved_blocks_percent] [-o [^]mount_options[,...]] [-p mmp_update_interval]
    [-r reserved_blocks_count] [-u user] [-C mount_count] [-L volume_label]
    [-M last_mounted_dir] [-O [^]feature[,...]]
    [-E extended-option[,...]] [-T last_check_time] [-U UUID]
    [ -I new_inode_size ] device
ubuntu@ubuntu:~$ sudo tune2fs -U random/dev/sdb2
tune2fs 1.42 (29-Nov-2011)
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
    [-i interval[d|m|w]] [-j] [-J journal_options] [-l]
    [-m reserved_blocks_percent] [-o [^]mount_options[,...]] [-p mmp_update_interval]
    [-r reserved_blocks_count] [-u user] [-C mount_count] [-L volume_label]
    [-M last_mounted_dir] [-O [^]feature[,...]]
    [-E extended-option[,...]] [-T last_check_time] [-U UUID]
    [ -I new_inode_size ] device
ubuntu@ubuntu:~$ sudo tune2fs -U random/dev/sdb6
tune2fs 1.42 (29-Nov-2011)
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
    [-i interval[d|m|w]] [-j] [-J journal_options] [-l]
    [-m reserved_blocks_percent] [-o [^]mount_options[,...]] [-p mmp_update_interval]
    [-r reserved_blocks_count] [-u user] [-C mount_count] [-L volume_label]
    [-M last_mounted_dir] [-O [^]feature[,...]]
    [-E extended-option[,...]] [-T last_check_time] [-U UUID]
    [ -I new_inode_size ] device
ubuntu@ubuntu:~$ sudo tune2fs -U random/dev/sdb7
tune2fs 1.42 (29-Nov-2011)
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
    [-i interval[d|m|w]] [-j] [-J journal_options] [-l]
    [-m reserved_blocks_percent] [-o [^]mount_options[,...]] [-p mmp_update_interval]
    [-r reserved_blocks_count] [-u user] [-C mount_count] [-L volume_label]
    [-M last_mounted_dir] [-O [^]feature[,...]]
    [-E extended-option[,...]] [-T last_check_time] [-U UUID]
    [ -I new_inode_size ] device
ubuntu@ubuntu:~$ sudo blkid -c/dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/loop0 squashfs         /rofs          
/dev/sda1  ntfs    SYSTEM   (not mounted)  20AAB6ACAAB67DBA
/dev/sda2  ntfs             (not mounted)  22EA25D1EA25A1D1
/dev/sda3  ntfs    Recovery (not mounted)  24049F64049F382E
/dev/sda4  vfat    HP_TOOLS (not mounted)  AC7D-193C
/dev/sr0   iso9660 Ubuntu 12.04.1 LTS amd64 /cdrom 
/dev/sdb5  swap             <swap>         6de40c28-a5f7-4919-9cc7-f26ee9826bfc
ubuntu@ubuntu:~$

---

### Post by oldfred on 2012-08-27
Tunefs did not work on any of them, I do not know command well enough to know issue.

Just to see if it is a partition corruption issue of some sort, from liveCD:

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

then see if sdb1 shows a UUID?

---

### Post by Meshal-USA on 2012-08-27
result of running the code:

/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****

     230 inodes used (0.01%)
       0 non-contiguous files (0.0%)
       0 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 221
  165127 blocks used (2.25%)
       0 bad blocks
       1 large file

     217 regular files
       4 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
     221 files










                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd /wubildr

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /wubildr

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb7: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   938,397,695   937,988,096   7 NTFS / exFAT / HPFS
/dev/sda3         938,397,696   968,450,047    30,052,352   7 NTFS / exFAT / HPFS
/dev/sda4         968,450,048   976,771,119     8,321,072   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059348992 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    58,593,279    58,591,232  83 Linux
/dev/sdb2          58,595,326   488,396,799   429,801,474   5 Extended
/dev/sdb5          58,595,328    60,547,071     1,951,744  82 Linux swap / Solaris
/dev/sdb6          60,549,120   128,907,263    68,358,144  83 Linux
/dev/sdb7         128,909,312   488,396,799   359,487,488  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        20AAB6ACAAB67DBA                       ntfs       SYSTEM
/dev/sda2        22EA25D1EA25A1D1                       ntfs       
/dev/sda3        24049F64049F382E                       ntfs       Recovery
/dev/sda4        AC7D-193C                              vfat       HP_TOOLS
/dev/sdb5        6de40c28-a5f7-4919-9cc7-f26ee9826bfc   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04.1 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  00 00 00 00 00 00 00 03  0f 3c f0 c0 00 00 00 00  |.........<......|
00000010  0c 3c f0 c0 00 00 00 00  00 00 00 3f f0 f0 f1 f3  |.<.........?....|
00000020  f6 fc f8 3f 00 00 00 f0  7c fc bc 3c 3c 3c 3c f0  |...?....|..<<<<.|
00000030  00 00 00 03 0f ff 0f 0f  0f 0f 0f ff 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 f0  00 00 00 3f f0 f0 00 03  |...........?....|
00000050  0f 3c f0 ff 00 00 00 c0  f0 f0 f0 c0 00 00 f0 f0  |.<..............|
00000060  00 00 00 3f f0 00 00 0f  00 00 f0 3f 00 00 00 c0  |...?.......?....|
00000070  f0 f0 f0 c0 f0 f0 f0 c0  00 00 00 00 03 0f 3c f0  |..............<.|
00000080  ff 00 00 03 00 00 00 f0  f0 f0 f0 f0 fc f0 f0 fc  |................|
00000090  00 00 00 ff f0 f0 f0 ff  00 00 f0 3f 00 00 00 f0  |...........?....|
000000a0  00 00 00 c0 f0 f0 f0 c0  00 00 00 0f 3c f0 f0 ff  |............<...|
000000b0  f0 f0 f0 3f 00 00 00 c0  00 00 00 c0 f0 f0 f0 c0  |...?............|
000000c0  00 00 00 ff f0 f0 00 00  03 0f 0f 0f 00 00 00 fc  |................|
000000d0  3c 3c 3c f0 c0 00 00 00  00 00 00 3f f0 f0 f0 3f  |<<<........?...?|
000000e0  f0 f0 f0 3f 00 00 00 c0  f0 f0 f0 c0 f0 f0 f0 c0  |...?............|
000000f0  00 00 00 3f f0 f0 f0 3f  03 03 0f 3f 00 00 00 c0  |...?...?...?....|
00000100  f0 f0 f0 f0 c0 c0 00 00  00 00 00 00 00 0f 0f 00  |................|
00000110  00 0f 0f 00 00 00 00 00  00 c0 c0 00 00 c0 c0 00  |................|
00000120  00 00 00 00 00 0f 0f 00  00 0f 0f 03 0f 00 00 00  |................|
00000130  00 c0 c0 00 00 c0 c0 c0  00 00 00 00 03 0f 3c f0  |..............<.|
00000140  3c 0f 03 00 00 00 00 f0  c0 00 00 00 00 00 c0 f0  |<...............|
00000150  00 00 00 00 00 00 3f 00  3f 00 00 00 00 00 00 00  |......?.?.......|
00000160  00 00 fc 00 fc 00 00 00  00 00 00 3c 0f 03 00 00  |...........<....|
00000170  00 03 0f 3c 00 00 00 00  00 c0 f0 3c f0 c0 00 00  |...<.......<....|
00000180  00 00 00 3f f0 00 03 0f  0f 00 0f 0f 00 00 00 c0  |...?............|
00000190  f0 f0 c0 00 00 00 00 00  00 00 00 3f f0 f0 f3 f3  |...........?....|
000001a0  f3 f0 f0 3f 00 00 00 f0  3c 3c fc 1c fc 00 00 f0  |...?....<<......|
000001b0  00 00 00 0f 3f f0 f0 f0  ff f0 f0 f0 00 00 00 fe  |....?...........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c8 1d 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 7b cf  1d 00 87 10 13 04 00 00  |......{.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

---

### Post by Meshal-USA on 2012-08-27
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd /wubildr

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /wubildr

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb7: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   938,397,695   937,988,096   7 NTFS / exFAT / HPFS
/dev/sda3         938,397,696   968,450,047    30,052,352   7 NTFS / exFAT / HPFS
/dev/sda4         968,450,048   976,771,119     8,321,072   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059348992 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    58,593,279    58,591,232  83 Linux
/dev/sdb2          58,595,326   488,396,799   429,801,474   5 Extended
/dev/sdb5          58,595,328    60,547,071     1,951,744  82 Linux swap / Solaris
/dev/sdb6          60,549,120   128,907,263    68,358,144  83 Linux
/dev/sdb7         128,909,312   488,396,799   359,487,488  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        20AAB6ACAAB67DBA                       ntfs       SYSTEM
/dev/sda2        22EA25D1EA25A1D1                       ntfs       
/dev/sda3        24049F64049F382E                       ntfs       Recovery
/dev/sda4        AC7D-193C                              vfat       HP_TOOLS
/dev/sdb5        6de40c28-a5f7-4919-9cc7-f26ee9826bfc   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04.1 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  00 00 00 00 00 00 00 03  0f 3c f0 c0 00 00 00 00  |.........<......|
00000010  0c 3c f0 c0 00 00 00 00  00 00 00 3f f0 f0 f1 f3  |.<.........?....|
00000020  f6 fc f8 3f 00 00 00 f0  7c fc bc 3c 3c 3c 3c f0  |...?....|..<<<<.|
00000030  00 00 00 03 0f ff 0f 0f  0f 0f 0f ff 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 f0  00 00 00 3f f0 f0 00 03  |...........?....|
00000050  0f 3c f0 ff 00 00 00 c0  f0 f0 f0 c0 00 00 f0 f0  |.<..............|
00000060  00 00 00 3f f0 00 00 0f  00 00 f0 3f 00 00 00 c0  |...?.......?....|
00000070  f0 f0 f0 c0 f0 f0 f0 c0  00 00 00 00 03 0f 3c f0  |..............<.|
00000080  ff 00 00 03 00 00 00 f0  f0 f0 f0 f0 fc f0 f0 fc  |................|
00000090  00 00 00 ff f0 f0 f0 ff  00 00 f0 3f 00 00 00 f0  |...........?....|
000000a0  00 00 00 c0 f0 f0 f0 c0  00 00 00 0f 3c f0 f0 ff  |............<...|
000000b0  f0 f0 f0 3f 00 00 00 c0  00 00 00 c0 f0 f0 f0 c0  |...?............|
000000c0  00 00 00 ff f0 f0 00 00  03 0f 0f 0f 00 00 00 fc  |................|
000000d0  3c 3c 3c f0 c0 00 00 00  00 00 00 3f f0 f0 f0 3f  |<<<........?...?|
000000e0  f0 f0 f0 3f 00 00 00 c0  f0 f0 f0 c0 f0 f0 f0 c0  |...?............|
000000f0  00 00 00 3f f0 f0 f0 3f  03 03 0f 3f 00 00 00 c0  |...?...?...?....|
00000100  f0 f0 f0 f0 c0 c0 00 00  00 00 00 00 00 0f 0f 00  |................|
00000110  00 0f 0f 00 00 00 00 00  00 c0 c0 00 00 c0 c0 00  |................|
00000120  00 00 00 00 00 0f 0f 00  00 0f 0f 03 0f 00 00 00  |................|
00000130  00 c0 c0 00 00 c0 c0 c0  00 00 00 00 03 0f 3c f0  |..............<.|
00000140  3c 0f 03 00 00 00 00 f0  c0 00 00 00 00 00 c0 f0  |<...............|
00000150  00 00 00 00 00 00 3f 00  3f 00 00 00 00 00 00 00  |......?.?.......|
00000160  00 00 fc 00 fc 00 00 00  00 00 00 3c 0f 03 00 00  |...........<....|
00000170  00 03 0f 3c 00 00 00 00  00 c0 f0 3c f0 c0 00 00  |...<.......<....|
00000180  00 00 00 3f f0 00 03 0f  0f 00 0f 0f 00 00 00 c0  |...?............|
00000190  f0 f0 c0 00 00 00 00 00  00 00 00 3f f0 f0 f3 f3  |...........?....|
000001a0  f3 f0 f0 3f 00 00 00 f0  3c 3c fc 1c fc 00 00 f0  |...?....<<......|
000001b0  00 00 00 0f 3f f0 f0 f0  ff f0 f0 f0 00 00 00 fe  |....?...........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c8 1d 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 7b cf  1d 00 87 10 13 04 00 00  |......{.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb7

00000000  55 53 42 43 97 2e 01 00  00 10 00 00 00 00 0a 2a  |USBC...........*|
00000010  00 07 af 00 00 00 00 08  00 00 00 00 00 00 00 d3  |................|
00000020  33 cc 3c 59 db 9e 74 04  cb 7f a1 eb df 1c fb cf  |3.<Y..t.........|
00000030  ff fb 90 64 d7 00 04 8b  5f d5 d3 0f 5b 6a 33 61  |...d...._...[j3a|
00000040  7a ba 61 88 26 11 dd 8d  56 cc 61 6d a8 d1 86 6a  |z.a.&...V.am...j|
00000050  dd 84 98 98 c0 23 b1 47  65 65 17 1e 41 8e ea d0  |.....#.Gee..A...|
00000060  82 aa cd 4e eb 17 57 a0  c3 c9 57 4b 00 00 00 00  |...N..W...WK....|
00000070  d0 38 74 4e 00 00 da 1c  0c a2 e2 4a a2 42 e8 46  |.8tN.......J.B.F|
00000080  04 00 ec c4 7e 8c 4f d5  f7 b1 cf 42 50 e7 41 f6  |....~.O....BP.A.|
00000090  5a 4e 7c d1 74 20 9b a9  33 b9 28 a7 79 e4 54 60  |ZN|.t ..3.(.y.T`|
000000a0  e5 f3 e0 0f d0 00 00 0b  41 72 a8 c3 7d 9c 81 f9  |........Ar..}...|
000000b0  22 f8 50 18 9d ef 64 04  4b b0 dd b6 7e bd ff 44  |".P...d.K...~..D|
000000c0  c9 7e 8f bf f6 bd dc 86  24 e4 22 9e 42 1d 18 f5  |.~......$.".B...|
000000d0  3b 7a 7a b9 15 f2 26 4d  3f ef f3 bf ab a7 ff 3a  |;zz...&M?......:|
000000e0  11 18 f5 39 33 b9 18 f6  3b b6 ca e8 b3 b6 cf 55  |...93...;......U|
000000f0  20 d2 5d 8e 82 f5 43 ee  10 00 00 02 db 91 29 4c  | .]...C.......)L|
00000100  b1 0c 01 5c 7a 0c e3 04  86 c4 b6 ea 96 9b 7a 4f  |...\z.........zO|
00000110  1f ee 74 cd 00 00 00 00  03 ed 4b 21 00 00 00 00  |..t.......K!....|
00000120  c9 c1 9c 8d e5 be fb 20  ce f3 a9 da ca 73 6f 18  |....... .....so.|
00000130  9d d1 65 b1 96 8a 73 29  2e 73 14 89 fc e8 6a 9c  |..e...s).s....j.|
00000140  79 6c c2 00 a2 2c c5 20  da ce 82 e5 5e df fb 2a  |yl...,. ....^..*|
00000150  ee ec ec 44 54 52 1a d5  5a 95 55 e9 a2 1a d7 35  |...DTR..Z.U....5|
00000160  4e a8 a4 26 a7 72 b0 e3  33 a1 df a8 42 00 00 00  |N..&.r..3...B...|
00000170  09 12 01 37 00 00 10 f4  9a 8e 2d e9 5c 4e cd f0  |...7......-.\N..|
00000180  04 00 01 ae bf fc ff 97  ff fe 45 28 de cd bb ed  |..........E(....|
00000190  eb 7a ee b4 ff ff ff ff  ff fe ff 69 2a ea c4 52  |.z.........i*..R|
000001a0  dd 12 e8 64 26 b9 4a 54  77 62 cc 43 1d 00 e1 a5  |...d&.JTwb.C....|
000001b0  e8 f5 ef a7 92 95 b6 08  00 14 9b 64 ba 92 ef 48  |...........d...H|
000001c0  50 0a 81 cb 02 1e 5d 33  6a 49 30 b8 71 ef 8d 17  |P.....]3jI0.q...|
000001d0  fa ff fb 90 64 d1 80 03  b1 64 57 d3 0b 2b 60 53  |....d....dW..+`S|
000001e0  4c 7a f9 3c a2 6d 0e 8d  93 63 a7 ac ad 81 25 30  |Lz.<.m...c....%0|
000001f0  6c 74 f0 95 b1 51 a7 9b  fe 11 d7 c1 17 3d 8c 0a  |lt...Q.......=..|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

---

### Post by Meshal-USA on 2012-08-27
do you think a previews version of ubnutu might work? because i'm thinking to uninstall it and install 11.10

---

### Post by Meshal-USA on 2012-08-27
ok i'll try installing 10.4 and see, it might work

---

### Post by Meshal-USA on 2012-09-02
i finally been able to install ubuntu... this replay for anyone having the same problem i have

the problem i've got is that i couldn't install ubuntu alongside windows because windows is using all the four partitions. so i thought i should use my external hard drive and install ubuntu on it and dual boot it with windows. but then every time i install ubuntu i experienced a filesystem error, i tried the text version and it was installed but for some reason the grub was always deleted. i even tried fedora but i also had the same error after installing it.

how to install ubuntu:
this is the only way i could install ubuntu. first you will have to change one of the partitions to logical partition. you should install "partition wizard home version" to be able to change it. i changed C: partition to logical because my HP laptop does not boot windows from C: so it wasn't necessary to make it primary. if your C: is bootable, you have to delete one of the partitions or try to make one of them logical "you should search for which one is least necessary for your windows system". then resize your C: partition so that you make space for ubuntu. then use the ubuntu CD and make three logical partitions, "swap", "/", and "/home" and ubuntu will be install alongside windows.

---

