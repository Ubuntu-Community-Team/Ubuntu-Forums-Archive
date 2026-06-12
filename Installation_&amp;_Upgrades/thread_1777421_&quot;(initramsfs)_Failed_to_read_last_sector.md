---
title: "&quot;(initramsfs) Failed to read last sector?"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by Alaza on 2011-06-07
Hello there,

I'm trying to do an installation of Ubuntu 11.04 on my Windows 7 setup. I have another harddrive, which only has one partition. It is fresh formatted with NTFS, I launch Wubi, choose the partition, everything's fine, reboot, and when I choose Ubuntu for the first time, I get this error:

[http://img59.imageshack.us/img59/5875/20110607220500.jpg]("http://img59.imageshack.us/img59/5875/20110607220500.jpg")

My Windows 7 installation is on a SSD harddrive, and my Ubuntu installation is a Western Digital WD360 SATA disk. In my BIOS I have "SATA Mode" set to "IDE".

I have no idea whether it's anything to do with that, but I reckon I'd share it.

What can I do?

---

### Post by wildmanne39 on 2011-06-07
> **Alaza said:**
> Hello there,

I'm trying to do an installation of Ubuntu 11.04 on my Windows 7 setup. I have another harddrive, which only has one partition. It is fresh formatted with NTFS, I launch Wubi, choose the partition, everything's fine, reboot, and when I choose Ubuntu for the first time, I get this error:

[http://img59.imageshack.us/img59/5875/20110607220500.jpg]("http://img59.imageshack.us/img59/5875/20110607220500.jpg")

My Windows 7 installation is on a SSD harddrive, and my Ubuntu installation is a Western Digital WD360 SATA disk. In my BIOS I have "SATA Mode" set to "IDE".

I have no idea whether it's anything to do with that, but I reckon I'd share it.

What can I do?Hi, if you are installing to a second hard drive I think you should just do a normal install without wubi, that might be the problem I do not know if you can install to a second drive with wubi.Hi download and install this script it will let us look at your hard drives. 

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read. Also you can look at the wubi mega thread and see if you see the answer to your problem there.

---

### Post by Rubi1200 on 2011-06-08
Hi and welcome to the forums Alaza :-)

Definitely post the results of the boot script that wildmanne39 asked for.

The other thing to do is follow the advice in that error message and run chkdsk in Windows. It might also be a good idea to defragment the drives too before you attempt to resume the installation process.

---

### Post by Alaza on 2011-06-08
Hello again,

I will do both, thanks, as soon as I get home from work.

Thanks. :)

---

### Post by Alaza on 2011-06-08
I just see know that the boot_info_script.sh is supposed to run on a Linux setup.

What to do seeing I only have a Win7?

---

### Post by Rubi1200 on 2011-06-08
> **Alaza said:**
> I just see know that the boot_info_script.sh is supposed to run on a Linux setup.

What to do seeing I only have a Win7?
You need to get hold of an Ubuntu CD because it is quite possible that the only way we can help you repair this is from a LiveCD/USB.

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

On that same page are instructions on how to create a LiveCD/USB and how to boot the computer with it.

---

### Post by Alaza on 2011-06-08
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdd1/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 150.0 GB, 150039945216 bytes
16 heads, 63 sectors/track, 290721 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   293,044,719   293,044,657  42 SFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdc2             206,848    86,507,519    86,300,672   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 37.0 GB, 37019566080 bytes
240 heads, 63 sectors/track, 4782 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048    72,300,543    72,298,496   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             63   234,436,544   234,436,482   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        64F01914F018EDD4                       ntfs       1337 Raptor
/dev/sdb1        426036CE6036C905                       ntfs       Kæmpe lager
/dev/sdc1        9A4886DF4886B991                       ntfs       System Reserved
/dev/sdc2        44809068809061EA                       ntfs       OS
/dev/sdd1        6ADC9585DC954BE7                       ntfs       New Volume
/dev/sde1        F64072D040729759                       ntfs       Lager

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdd1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200




```Here it is :)

---

### Post by Rubi1200 on 2011-06-08
Thanks for posting the results. I am a bit concerned about some of the errors being reported and have asked forum member bcbc, a Wubi expert, to take a look and offer some perspectives.

Please be patient and wait for his response (time differences and all that).

Meantime, please don't attempt any changes that could make fixing this more difficult.

Thanks.

---

### Post by Alaza on 2011-06-08
Hi again,

I didnt see your post before just now, so Ive been trying around a bit. I got to install Ubuntu alongside my Windows 7 on the same physical harddrive with no problems. I did have some driver issues though, so I decided to make a reinstallation of Ubuntu, by deleting the partitions it had made and reclaiming the harddrive space. This works fine.

So I thought Id try to boot up again on the LiveCD and install on another harddrive, but when doing so I get a new error: No root file system is defined. Please correct this from the partitioning menu.

Ive tried to deleted the partition on the harddrive I wanted to use, and Ive even tried another one, but with no luck.

After I saw your post Ive made a new result.txt and added it here in case changes has been made.


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid ab4d9e4d-39ed-4ca4-9217-778586d999e6 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 150.0 GB, 150039945216 bytes
16 heads, 63 sectors/track, 290721 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   293,044,719   293,044,657  42 SFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdc2             206,848   117,225,471   117,018,624   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 37.0 GB, 37019566080 bytes
240 heads, 63 sectors/track, 4782 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048    72,300,543    72,298,496   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             63   234,436,544   234,436,482   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        64F01914F018EDD4                       ntfs       1337 Raptor
/dev/sdb1        426036CE6036C905                       ntfs       Kæmpe lager
/dev/sdc1        9A4886DF4886B991                       ntfs       System Reserved
/dev/sdc2        44809068809061EA                       ntfs       OS
/dev/sdd1        B0BA2D3EBA2D0288                       ntfs       New Volume
/dev/sde1        F64072D040729759                       ntfs       Lager

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Rubi1200 on 2011-06-08
Alaza,
I have to go offline now (it is late here) but I ask you to please wait for a response from bcbc before doing anything else.

Part of the problem is the fact that sda is labeled as a dynamic disk, which can be an issue.

For more information read the posts here by oldfred and srs5694:
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)

Again, I would like to reiterate that I think you need to wait for bcbc or oldfred or srs5694 to comment on the best way to move forward in this situation.

I will look in on the thread again tomorrow.

---

### Post by Alaza on 2011-06-08
Alright, I will leave it be for the moment. :)

I might try and test a solution on my laptop getting more familiar, but I will leave the desktop until I hear from you or the others. :)

---

### Post by bcbc on 2011-06-09
Hi - apologies for late response.... long day.

This is a bit of a tough one. The first error you got had to do with mounting /dev/sda2 (which doesn't exist according to the bootinfoscript). It should have been /dev/sdc2

So I think there is some setup (raid/dynamic disks etc) that is making the drive setup appear different from within Windows - compared to Ubuntu. And this is a problem no matter whether you install Wubi or normal Ubuntu.

You should be concerned with data loss if you are trying to install Ubuntu on a drive that has Windows 'dynamic drives'. As far as I know Ubuntu has no way to interpret these and this can lead to issues. The fact that it doesn't even detect what sort of file system is present is an indication.

Anyway... I'm by no means an expert on dynamic drives/logical volumes/raid etc. so it's hard for me to give advice on this. 

Maybe start off by figuring out how Windows sees your underlying drives - either through Disk Management console, or using DISKPART.

---

### Post by Rubi1200 on 2011-06-09
Thanks bcbc for responding.

Alaza, I would follow the advice and start by investigating from the angle suggested by bcbc. The more information you can post here, the better.

I have also asked srs5694 to take a look and hope you can wait until he responds.

Thanks.

---

### Post by Alaza on 2011-06-09
Hi,

No problem at all, there is no rush. I have in the meantime with no problems got Ubuntu up and running on my laptop on a free partition (on the same harddrive as Win7).

I have uploaded a screenshot of my harddrive configuration seen in Win7 here:

[http://img38.imageshack.us/img38/7853/diskmanagement.png]("http://img38.imageshack.us/img38/7853/diskmanagement.png")

Now, it is possible for me to do formatting of either G: or I: - one of those would be used and has nothing that hasn't been backed up.

I am not sure to be honest, how the "status" configuration should look like - hope you have any ideas.

Thank you

---

### Post by srs5694 on 2011-06-09
If I understand correctly, Linux is not currently installed to the computer in any form and it boots Windows, but you're unable to *re*-install it because of the "no root filesystem is defined" error message.

If so, your situation isn't bad at all; you just need to get past that re-installation error. The problem there is that you *must* tell Linux what partition to use as its "root" (main) partition when you install it. Some methods of partitioning and installation fill in this information automatically, but others don't. To do it manually, you've got to tell the installer to mount the root partition as "/". Check [this Web site](http://techie-buzz.com/foss/ubuntu-10-04-lts-installation-guide.html) (which is for 10.04, but the relevant screens haven't changed much). Partway down the page you'll see a screen shot from a "Prepare Partitions" dialog box, and below that from "Edit a Partition". That's what you need to do.

Also, note the advice given by others: Don't try to touch /dev/sda with your Ubuntu installation. Install it anywhere else and it'll be fine, but /dev/sda uses Microsoft's proprietary "dynamic disk" configuration. One exception to this rule is that you *should* install Ubuntu's boot loader, GRUB, to /dev/sda. It seems to be there are the moment and is working for now, so you want to overwrite this old GRUB configuration with a new one when you re-install.

---

### Post by Alaza on 2011-06-19
I'm sorry that I haven't been able to answer before now, but here goes.

I just did what the guide said, and so now I have installed Ubuntu 11 on /dev/ssd. What I did further was to create a 2GB partition on /dev/ssd for SWAP area. Additionally I chose /dev/sda as boot partition, but now when I boot it just goes directly into my Windows 7 installation, and I can (obviously I guess), not see my harddrive now with the EXT4 file system.

Should I have chosen the "Windows 7 loader" boot in the installation?

---

### Post by Rubi1200 on 2011-06-19
With all the changes that have gone on, best thing to do is let us see the results of the boot info script again:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Alaza on 2011-06-20
Hi again,

Here's the new results:

```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 5f3c7b36-bc95-4c1d-b423-5278faa03d48 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 150.0 GB, 150039945216 bytes
16 heads, 63 sectors/track, 290721 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   293,044,719   293,044,657  42 SFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdc2             206,848   117,225,471   117,018,624   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048    68,361,422    68,359,375  83 Linux
/dev/sdd2          68,362,238    72,302,591     3,940,354   5 Extended
/dev/sdd5          68,362,240    72,302,591     3,940,352  82 Linux swap / Solaris


Drive: sde _____________________________________________________________________

Disk /dev/sde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             63   234,436,544   234,436,482   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        64F01914F018EDD4                       ntfs       1337 Raptor
/dev/sdb1        426036CE6036C905                       ntfs       Kæmpe lager
/dev/sdc1        9A4886DF4886B991                       ntfs       System Reserved
/dev/sdc2        44809068809061EA                       ntfs       OS
/dev/sdd1        5f3c7b36-bc95-4c1d-b423-5278faa03d48   ext4       
/dev/sdd5        72c63c76-8099-4bd9-8442-41f922b7cd13   swap       
/dev/sde1        F64072D040729759                       ntfs       Lager

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdd1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdd,msdos1)'
search --no-floppy --fs-uuid --set=root 5f3c7b36-bc95-4c1d-b423-5278faa03d48
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdd,msdos1)'
search --no-floppy --fs-uuid --set=root 5f3c7b36-bc95-4c1d-b423-5278faa03d48
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root 5f3c7b36-bc95-4c1d-b423-5278faa03d48
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=5f3c7b36-bc95-4c1d-b423-5278faa03d48 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root 5f3c7b36-bc95-4c1d-b423-5278faa03d48
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=5f3c7b36-bc95-4c1d-b423-5278faa03d48 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root 5f3c7b36-bc95-4c1d-b423-5278faa03d48
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdd,msdos1)'
    search --no-floppy --fs-uuid --set=root 5f3c7b36-bc95-4c1d-b423-5278faa03d48
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 9A4886DF4886B991
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdd1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdd1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=72c63c76-8099-4bd9-8442-41f922b7cd13 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  10.216342926 = 10.969714688   boot/grub/core.img                             1
  18.305446625 = 19.655323648   boot/grub/grub.cfg                             1
   0.926956177 = 0.995311616    boot/initrd.img-2.6.38-8-generic-pae           1
   0.688903809 = 0.739704832    boot/vmlinuz-2.6.38-8-generic-pae              1
   0.926956177 = 0.995311616    initrd.img                                     1
   0.688903809 = 0.739704832    vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by drs305 on 2011-06-20
I would make sdd the controlling drive and point it's MBR to sdd1. This will allow Grub2 to control the boot, and hopefully G2 will also find Windows and automatically add it's entry to the menu.

To make this happen, mount sdd1 (Ubuntu) from the LiveCD, then install Grub 2:

```
sudo mount /dev/sdd1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdd

```
Do NOT use the partition number (sdd1) in the second command.

When you reboot, make sure the BIOS points to your Ubuntu drive (sdd - 37GB) as the first boot device. That should display the Grub menu on boot.

If it doesn't show a Windows entry, run "sudo update-grub" after booting into your normal Ubuntu installation. If it still doesn't find it, you can access Windows by changing the BIOS boot order back to what it was originally until we can figure out what happened. (It's probably booting sdc first).

---

### Post by Alaza on 2011-06-21
Hi again guys,

A big thanks to you all, it works now. After I ran the mount and installed Grub, and finally booted on /dev/sdd, the boot part is solved. I do have two more questions though that I hope you can help with.

Can I somehow move Windows up the Grub list for it to me the automatic boot OS, and secondly I have a NVidia 8800 GTX and two monitors, but after installing the recommended nVidia driver, Ubuntu doesn't seem to detect my other monitor. Do I need to install the official nVidia driver, and if so, how do I install the driver? I have tried it, and I get a .run file from here:

[http://www.nvidia.com/object/linux-display-ia32-275.09.07-driver.html](http://www.nvidia.com/object/linux-display-ia32-275.09.07-driver.html)

But when I try to execute it I get a "gedit has not been able to detect the character coding..." error.

Thank you

---

### Post by drs305 on 2011-06-21
> **Alaza said:**
> 
Can I somehow move Windows up the Grub list for it to me the automatic boot OS, and secondly ...

You can manually edit the /etc/default/grub file to set the default OS if all you want to do is change which OS boots if you don't select anything at boot. For that, see the "Tasks" link in my signature.

An easier (and IMO better) solution is to use a GUI app called Grub Customizer. This program will let you set the default OS, rename the entries, reorder the menu items, and lots more. Click on the "Customizer" link to go to a page on how to install and use GC.

---

