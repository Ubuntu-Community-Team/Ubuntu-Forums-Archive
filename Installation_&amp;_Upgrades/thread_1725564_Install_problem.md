---
title: "Install problem"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by Andrenap on 2011-04-09
I had a dual boot PC with Mac and Windows. I installed Ubuntu, it went ok that time. Then I wiped Macs partitions, and I couldn`t initialize either one of the other two. I tried reinstalling it (I was just using it for  a few hours, not such a big loss), but now, it throws a 'the ext4 file system creation in partition #2 of SCSI1 (0,0,0) (sda) failed.", in terminal I saw a end_request i/o error, dont remember exactly  what it said. how can I install ubuntu or, at least, use windows? grub init throws a invalid partition error

---

### Post by Rubi1200 on 2011-04-10
Hi,

we need to get a better overview of the current state of the system.

To that end, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Andrenap on 2011-04-10
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       307199999 sectors, but according to the info from 
                       fdisk, it has 307208946 sectors.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /wubildr /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   307,210,994   307,208,947   7 HPFS/NTFS
/dev/sda2         307,212,288   502,523,903   195,311,616  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1E4222194221F5E5                       ntfs                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/1E4222194221F5E5  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc 

```

---

### Post by Rubi1200 on 2011-04-10
Hi,
thanks for posting the results.

It appears you used to have a Wubi install, correct?

There is a problem with sda2, where I assume you were trying to install Ubuntu:
> mount: unknown filesystem type 
As far as I can tell, the Windows partition is okay.

So, do you want to try and reinstall (perhaps repair if possible) Ubuntu on sda2, delete the partition and recover Windows, or something else?

---

### Post by Andrenap on 2011-04-10
I didn't have a wubi. i had ubuntu for a few hours and then it kinda stopped working. I wanna install ubuntu in sda2, keeping winvista (coz of my family) in the sda1

---

### Post by Dutch70 on 2011-04-10
Wubi is the windows installer. You did install Ubuntu into windows programs, correct? 
Does it show up in windows programs?

---

### Post by Andrenap on 2011-04-10
First of all, I know what wubi is. But the boot loader is grub, i didn`t installed it, just ignore that info.
And second, I can`t use windows, grub is bugged...

---

### Post by Andrenap on 2011-04-11
Someone there? i'm havin to use 'try it from cd' for two days, cmon people!

---

### Post by Rubi1200 on 2011-04-11
This is what I would probably do in this situation:

1. use GParted from the LiveCD to delete whatever is on sda2 and then leave it as unallocated space

2. restore the Windows bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

3. make sure Windows is booting normally and run a chkdsk and defragment the Windows drive

4. if Windows is "happy," boot up the LiveCD again and install Ubuntu to the unallocated space on sda2

---

### Post by bcbc on 2011-04-11
Grub2 is pointing at /dev/sda2 which is type 83 - linux (so far so good). But /dev/sda2 looks like this:
> sda2: _________________________________________________________________________      File system:            Boot sector type:  -     Boot sector info:       Mounting failed: mount: unknown filesystem type ''  So from a live CD, you could try running fsck on /dev/sda2. Or see if testdisk or some other recovery tool can recover whatever was on there.

If you just recently installed on /dev/sda2 and don't have anything important on there, I'd do what Rubi1200 says - delete it and start again.

---

