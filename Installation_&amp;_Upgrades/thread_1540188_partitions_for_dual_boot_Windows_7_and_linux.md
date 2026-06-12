---
title: "partitions for dual boot Windows 7 and linux"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by rawlins02 on 2010-07-27
I'm setting up a new Dell as dual boot.  I'm leaning toward first partition for Windows 7, a second partition that can be accessed from either OS, and an extended partition that will have root, swap, /home, etc.  

Questions: For the partition to be accessible to both, what is the preferred format? I've read that FAT32 or NTFS will suffice. ext4 is what I understand should be set for the linux partitions. 

For the linux partitions, is there an advantage to setting one or two of the partitions as primary, rather than logical?  Also, any clear advantages or disadvantages to having a /boot partition?  It is likely I'll only have installed one version of Ubuntu at a time.

---

### Post by Mark Phelps on 2010-07-27
> **rawlins02 said:**
> ... Questions: For the partition to be accessible to both, what is the preferred format? I've read that FAT32 or NTFS will suffice. ext4 is what I understand should be set for the linux partitions. 
To share data between Linux and current MS Windows versions, NTFS is the best format.  All these OSs can read and write those filesystems.

However ... and this IS important, there are no MS Windows utilities that can currently read or write Ext4 filesystems.

> For the linux partitions, is there an advantage to setting one or two of the partitions as primary, rather than logical?  
Not that I know of.
> Also, any clear advantages or disadvantages to having a /boot partition?  It is likely I'll only have installed one version of Ubuntu at a time.
Win7 did that as a new standard in order to allow for the full-partition encryption of the Win7 OS partition -- because, it can not boot if the boot loader is contained on an encrypted partition.

Don't know if Ubuntu has this limitation -- have not mess with encryption in Linux.

---

### Post by rawlins02 on 2010-07-27
Excellent. I plan to set up a one data partition formatted NTFS for access by both systems. Don't expect to access the Linux ext4 partitions from Windows.

---

### Post by rawlins02 on 2010-07-27
Mark... Just re-read your post and comment about new Windows 7 boot partition. I've been investigating whether I can delete the small 41MB FAT32 partition at front of disk from factory Windows installation. I was thinking that everything Windows (boot loader, etc) would go under the one main Windows OS partition.   Your comment suggests that small partition is integral and must stay. I have a post at the Wondows 7 forums asking about this as well.

---

### Post by efflandt on 2010-07-27
Something to note about Dell is that they no longer provide discs for the Windows system or recovery, so you should make sure that you can create those before you start tampering with your system.  I bought a a Dell Studio XPS 8100 from Best Buy and the only discs it came with was a drivers and utilities disc and Works9 disc.  And once you register you can download other software the comes with it for DVD playing, Roxio, etc.

But everything worked in 64-bit Lucid out of the box, including its built-in wireless.  All I really had to do was enable nvidia(195) drivers to make its GT220 video card faster.  Although, something strange is that it cannot boot from the far end of a 500 GB USB drive, even though it can boot fine from a 160 GB USB drive or from the far end (beyond 900 GB point) of its 1 TB internal drive.  The 500 GB drive boots fine from two 4 year old laptops (I am running from it now on a company laptop in a motel).

---

### Post by rawlins02 on 2010-07-28
Right after turning it on for first time I wrote the recovery DVDs. I've used them once already to bring the system back to factory state. Then I called Dell and requested the Windows 7 OS Re-installation DVD. After I deleted the recovery partition and collapsed the space into the Windows OS partition I used the Re-installation DVD to install Windows 7 onto that partition.  

At the moment I am assessing the value in the small FAT32 partition at front of the drive, which I now understand is a "Dell diagnostic partition". Somewhere I read that those functions can be performed, if needed, by downloading files from Dell. Probably should leave it there as it is only 41MB.

Sure would like to get on to the Ubuntu install.  I do very little under Windoze...

---

### Post by Mark Phelps on 2010-07-28
IF you're not sure what an OEM-provided partition does, and it's not otherwise hindering what you need to do, I would just leave it alone for now.

Most other OEMs insert a small partition at the beginning of the drive to serve as the Win7 boot partition.  I think Dell puts their diags partition there and inserts the boot partition at the end of the drive.

---

### Post by DrMelon on 2010-07-28
> **rawlins02 said:**
> Right after turning it on for first time I wrote the recovery DVDs. I've used them once already to bring the system back to factory state. Then I called Dell and requested the Windows 7 OS Re-installation DVD. After I deleted the recovery partition and collapsed the space into the Windows OS partition I used the Re-installation DVD to install Windows 7 onto that partition.  

At the moment I am assessing the value in the small FAT32 partition at front of the drive, which I now understand is a "Dell diagnostic partition". Somewhere I read that those functions can be performed, if needed, by downloading files from Dell. Probably should leave it there as it is only 41MB.

Sure would like to get on to the Ubuntu install.  I do very little under Windoze...

You could back up the contents of that partition and put them back if needed.

---

### Post by rawlins02 on 2010-07-28
Yes Mark and DrMelon, I understand it is a diagnostic partition with utilities for testing CPUs, memory, etc.  The Dell site has this utility available for download to burn to a bootable CD.  Moreover, I just put in the Software and Utilities CD that came with the machine and ran the diagnostics after selecting the BIOS option and booting the CD.  I'm interacting with folks at the Dell support forums to confirm this is stand-alone and, thus, I can delete the partition.  Of course, I can always use DVDs I created to recover to factory state with all partitions if needed.

But there is no other partition, other than the main OS, so now I'm wondering which partition handles booting. No one at the Dell forum mentioned losing ability to boot if I delete that partition...

---

### Post by oldfred on 2010-07-28
This will tell what boots:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by rawlins02 on 2010-07-28
When running Windows, the main OS partition info shows the word 'boot'. Unless I'm mistaken, the results of this test back that up (?)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   163,920,324   163,840,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        20AC-6762                              vfat                                     
/dev/sda2        3AAE49ABAE49610D                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by oldfred on 2010-07-28
All your windows boot is in sda2 and only the Dell Utilities are in sda1. I would back that up. IF you delete it you may end up changing partition numbers so windows may be sda1 and require repairs to see that it is sda1??

---

### Post by rawlins02 on 2010-07-28
I've created a bootable CD with the diagnostic utilities, appropriate for my machine, that I've downloaded from Dell support. I'm now back in LiveCD ready to delete that partition, and understand this may hose Windows OS.  I'll use reinstallation DVD if needed. Fresh system so nothing to lose...

Now I'd like to be sure of the best way to set up all partitions. I'm hoping to have the one NTFS for Windows, another for data (NTFS) that I can access from both Windows and linux, and the other partitions for linux. What would be the best order?   I leaning toward:

Windows OS partition, NTFS data partition, and then an extended partition for linux with swap, (linux) root, /home.

---

### Post by oldfred on 2010-07-28
Your partition order is fine, everyone has different opinions on partitions.

The installer may not have the ntfs-3g driver as you are installing Ubuntu, so you may not be able to format the NTFS partition you want. Once installed you can download gparted (since you cannot edit mounted partitions gparted is not automatically installed), but the ntfs-3g driver is auto installed so you can mount ntfs partitions. Then you can format that partition or do it from windows.

I always like to set up partitions totally separate from the install. And make sure windows boots before I do the final install. That is more important when it involves resizing windows.

---

### Post by rawlins02 on 2010-07-28
gparted on the Live CD has ntfs.  

I just notice that my new ntfs partition for data got placed first (sda1), when I used gparted in "try Ubuntu". But Windows booted fine a moment ago so crossing my fingers.  I've now got my linux partitions set and Ubuntu is installing. Hopefully my next post is not about installing but, perhaps, after some time, how well 10.04 works on this new Dell.

---

