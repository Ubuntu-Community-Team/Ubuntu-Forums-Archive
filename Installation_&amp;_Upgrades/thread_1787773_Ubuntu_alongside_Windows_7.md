---
title: "Ubuntu alongside Windows 7"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by Fruitynoob on 2011-06-21
Hello,

I installed Windows 7 on my new pc, and I wanted to dual-boot ubuntu with it. So I installed Ubuntu alongside Windows 7, but now I can't boot windows anymore. 

First there was an option to boot windows 7 in the grub boot menu, when I tried to boot windows 7, it went back to the grub menu. So I did bootrec /fixboot and bootrec /fixmbr, after that the grub menu didn't show up anymore, and no OS booted.

So I fixed grub with a couple of commands. Grub is working again and I can boot in Ubuntu, but I still can't boot in windows. When I try to boot in Windows, there is only a black screen with a white exclamation mark on it, I waited 10 minuted but nothing happens.

These are the results of Boot_info_script



```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid fd29955b-f00c-4fae-b2d1-c2974d2101d0 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1             206,848 1,953,519,615 1,953,312,768   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    85,723,959    85,721,912   7 NTFS / exFAT / HPFS
/dev/sdb2          85,725,182   125,044,735    39,319,554   5 Extended
/dev/sdb5          85,725,184   116,662,271    30,937,088  83 Linux
/dev/sdb6         116,664,320   125,044,735     8,380,416  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        32DAC81CDAC7DA6D                       ntfs       Games en Media
/dev/sdb1        6AA28335A2830533                       ntfs       
/dev/sdb5        fd29955b-f00c-4fae-b2d1-c2974d2101d0   ext4       
/dev/sdb6        95adb519-4501-42bb-af38-31198e06b06c   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /tmp/BootInfo0/sdb1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)


========================== sdb1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
./boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

```SDA is my HDD, and SDB is my ssd with windows 7 and ubuntu on it. I use my HDD to store my music and photos and such. (So I can't format the HDD right now)

---

### Post by YesWeCan on 2011-06-22
There seems to be some stuff missing from your bootinfoscript output, like some of the partitions of sdb, your fstab and grub.cfg. There are some errors reported.

You have two disks which is handy. You have Grub installed to the MBRs of both disks.

I think it is a good idea to keep the MBR code of the disk Windows is on as Windows MBR code. This way you can always boot Windows if you want to without recourse to Grub or Ubuntu. So I would recommend reinstalling Grub MBR on the HDD (sda) and use this to boot from normally, and restore the standard MBR on your SSD using Windows so you can boot Windows directly if you need to.

Boot into Ubuntu
run [COLOR="Blue"]sudo fdisk -l[/COLOR] and double check the drive letters. Identify the HDD. I'll assume it is still sda - if not, use sdb here or whetever it is called:
[COLOR="Blue"]sudo grub-install /dev/sda[/COLOR]

Reboot and tell the bios to boot the HDD. Check Ubuntu boots ok.
Reboot and use the Windows CD to restore the standard MBR to the SSD. Reboot to SSD and make sure Windows boots.

Then reboot and set the bios boot priority to boot the HDD first, and SSD second. Or CD first, then HDD and SSD if you prefer.


Now you should get a Grub boot menu and choice of Ubuntu or Windows. If you tell the bios to boot the SSD you should go straight into Windows.

---

### Post by Fruitynoob on 2011-06-22
So If I re-install grub on de hdd, I can still boot in windows 7, with grub?

*edit*

I Re-installed grub on the HDD, when I wanted to repair the MBR to the SSD with the recovery CD, it didn't recognize windows 7 anymore, so it couldn't repair anything.

These are the new results from boot_info_script:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid fd29955b-f00c-4fae-b2d1-c2974d2101d0 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1             206,848 1,953,519,615 1,953,312,768   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    85,723,959    85,721,912   7 NTFS / exFAT / HPFS
/dev/sdb2          85,725,182   125,044,735    39,319,554   5 Extended
/dev/sdb5          85,725,184   116,662,271    30,937,088  83 Linux
/dev/sdb6         116,664,320   125,044,735     8,380,416  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        32DAC81CDAC7DA6D                       ntfs       Games en Media
/dev/sdb1        6AA28335A2830533                       ntfs       
/dev/sdb5        fd29955b-f00c-4fae-b2d1-c2974d2101d0   ext4       
/dev/sdb6        95adb519-4501-42bb-af38-31198e06b06c   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /tmp/BootInfo0/sdb1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)


========================== sdb1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

```

---

### Post by Mark Phelps on 2011-06-22
Safest approach is to have only one disk connected at a time when doing installs or repairing installs.

Disconnect the Ubuntu drive, leaving the Win7 drive connected, and do startup repair -- could take several passes to get it working.

Then try booting the Ubuntu drive with only it connected.  IF it doesn't boot, then replace GRUB on THAT drive.

When Ubuntu is booting OK, reconnect the Win7 drive, reboot -- but continue to boot from the Ubuntu drive.  Then, open a terminal in Ubuntu and enter "sudo update-grub".  This will regenerate the GRUB menu and add an entry for Win7.

When you reboot, you should see a GRUB menu and be able to select either OS.

---

### Post by Fruitynoob on 2011-06-22
Well, the problem is, that I have Ubuntu AND windows 7 on the same drive (the ssd). But for some weird reason when I did: [COLOR=Blue]sudo grub-install /dev/sda (to install grub into the hdd)[/COLOR], windows 7 didn't show up anymore in the recovery cd, there is still an entry for windows 7 in Grub.

When I try to install grub on the sdd, it give some error messages:
```
yordi@yordi-desktop:~$ sudo grub-install /dev/sda

/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
/usr/sbin/grub-setup: warn: Sector 33 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.

```I switched the sata cables, so the ssd is sda and the hdd is now sdb.


I am going to re-install windows 7, after that I am going to make some partitions in windows 7, reboot to windows, and then re-install ubuntu with the correct partitions and bootloader to the correct drive. Hopefully this is going to work. Fingers crossed.

---

### Post by YesWeCan on 2011-06-22
What is FlexNet?

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)

Ok, I see. Another application is using the "no mans land" in the sectors immediately after the MBR. BTW I don't believe Grub has any legitimacy using this area either, even though the article arrogantly says this is someone else's bug. :)

Are you actually able to boot the HDD or not?

---

### Post by Fruitynoob on 2011-06-22
I don't know, but what I do know is that I can boot in Windows 7 and Ubuntu now. What I did was:
 
Re-install Windows 7, make an extra partition on the ssd. When the installation was complete, I booted Windows, then I made an extra partition on the hdd.
 
After that, I put the ubuntu cd in my pc, I configured it that / was installed to the extra partition on de ssd, made an extra partition out of the 100gb partition from the hdd for swap (4gb swap), so /home was installed on the 100gb partition on the hdd, and swap on the 4gb partition.
 
Now I only need to set windows as default in grub, and then I can put the solved tag in the title :D

---

### Post by YesWeCan on 2011-06-22
Where did you install Grub?

---

### Post by Fruitynoob on 2011-06-22
sda (de ssd with windows and ubuntu on it)

I just found out that the 105MB filesystem partition of windows 7, (when I re-installed windows 7, it made that partition automaticly), is some sort of a boot partition or something, there is a folder named: boot, and a file named: bootsec.bak, bootmgr and grldr.

---

