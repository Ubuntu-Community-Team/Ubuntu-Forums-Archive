---
title: "Neither Windows XP or Ubuntu 10.10 will boot; No GRUB menu"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by CheshireKat on 2011-08-28
So awhile ago I downloaded 10.4 and later, 10.10, but was too afraid to install them for fear of messing something up on my desktop. Well, I managed to get a cheap cable for the hecka old Dell laptop and successfully installed Bodhi Linux and UberStudent (both branches of Ubuntu, I believe), so I decided to give it a try on my HP/Compaq desktop computer, since it worked on the laptop that was way, way outdated with minimal problems, although they were different OSs, technically.Yeah, now I can't boot into any OS on my desktop and I don't see any GRUB menu or anything. I'm completely new to Linux and Ubuntu, so I've spent the last three weeks researching and downloading and nearly ripped out my hair trying to get everything set up. The desktop is a recent problem from Thursday.
First, after installing Ubuntu, I got a blank screen on boot. I had chosen the "Install alongside my current OS" option, but I chose my external hard drive to host Ubuntu, which I created a 91 GB partition for using the Ubuntu partitioner thing. So rebooted from the live disk, did a little research, and re-installed Ubuntu using the advanced options. I left the boot loader location to install where it suggested and set the partition/drive for the Ubuntu partition.
This caused a black screen with a blinking underscore (_) and nothing else.
Honestly, I've tried so many things that it's gets too difficult to walk through all my processes, but I've tried:

[LIST]
[*]booting from LiveCD, downloading & installing lilo to Windows drive as suggested from online
[*]testdisk copy from backup MBR
[*]Plop boot manager (Windows wouldn't boot, had blinking _; booting from USB froze)
[*]Super GRUB disk 2 & the other one, Rescatix
[*]re-installing Ubuntu 3 times with different settings each time
[/LIST]
Errors I've gotten:


[LIST]
[*]black screen (occurred after first Ubuntu install)
[*]blinking _ (occurs when trying to boot Windows; used to be Ubuntu as well after the third install I got the second error below)
[*]error: no such device: [long string of letters and numbers--my external drive's UUID thing] and then grub rescue >
[*]error: no partition device found (or something like that); this appears when trying to boot from my USB external drive after I did something (I think install Ubuntu once again, but I think I chose a wrong partition or something..ERG:mad:)
[*]and my current one, MBR 1: [blinking underscore]; this appeared when booting from internal hard drive/Windows after running testdisk's Copy-from-Backup MBR thing
[/LIST]
Now, here's a BUNCH of information; I ran bootinfo several times after each various fixes that failed to solve my problem:

**RESULTS:**



```

============================= Boot Info Summary: ===============================


 => Lilo is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.


===========================

sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 600615768 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /ntdetect.com


sdc1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......Sf.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 845056 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ldlinux.sys


sdd1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdd2: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  


sdd5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


sdd6: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info:  


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *             63   135,749,249   135,749,187   7 NTFS / exFAT / HPFS
/dev/sda2         135,765,315   156,280,319    20,515,005   7 NTFS / exFAT / HPFS




Drive: sdc _____________________________________________________________________


Disk /dev/sdc: 16.2 GB, 16231956480 bytes
255 heads, 63 sectors/track, 1973 cylinders, total 31703040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdc1    *             63    31,696,244    31,696,182   c W95 FAT32 (LBA)




Drive: sdd _____________________________________________________________________


Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdd1                  63   440,960,921   440,960,859   7 NTFS / exFAT / HPFS
/dev/sdd2         440,961,022   625,141,759   184,180,738   5 Extended
/dev/sdd5    *    440,961,024   618,999,807   178,038,784  83 Linux
/dev/sdd6         619,001,856   625,141,759     6,139,904  82 Linux swap / Solaris




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        A4DC262ADC25F768                       ntfs       COMPAQ
/dev/sda2        64EC36AAEC367680                       ntfs       HP_RECOVERY
/dev/sdc1        E8AD-290C                              vfat       
/dev/sdd1        C2BC0FD9BC0FC6BF                       ntfs       Expansion Drive
/dev/sdd5        18cca15c-36dc-489d-8588-0bacc4ec38bb   ext4       
/dev/sdd6        c213d1f4-7e89-4d0a-a389-f7bd7f686601   swap       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/E8AD-290C         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdd1        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd5        /media/18cca15c-36dc-489d-8588-0bacc4ec38bb ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)




================================ sda1/boot.ini: ================================


--------------------------------------------------------------------------------
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------


================= sdc1: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1


============== sdc1: Version of COM32(R) files used by Syslinux: ===============


 menu.c32                           :  COM32R module (v4.xx)


=========================== sdd5/boot/grub/grub.cfg: 

```


**RESULTS1** (after running the "Fix Windows MBR" of the aforementioned Rescatix:
```

============================= Boot Info Summary: ===============================


 => Testdisk is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdd.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 600615768 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /ntdetect.com


sdc1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdc2: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  


sdc5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sdc6: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info:  


sdd1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......Sf.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 845056 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ldlinux.sys


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *             63   135,749,249   135,749,187   7 NTFS / exFAT / HPFS
/dev/sda2         135,765,315   156,280,319    20,515,005   7 NTFS / exFAT / HPFS




Drive: sdc _____________________________________________________________________


Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdc1                  63   440,960,921   440,960,859   7 NTFS / exFAT / HPFS
/dev/sdc2         440,961,022   625,141,759   184,180,738   5 Extended
/dev/sdc5         440,961,024   618,999,807   178,038,784  83 Linux
/dev/sdc6         619,001,856   625,141,759     6,139,904  82 Linux swap / Solaris




Drive: sdd _____________________________________________________________________


Disk /dev/sdd: 16.2 GB, 16231956480 bytes
255 heads, 63 sectors/track, 1973 cylinders, total 31703040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdd1    *             63    31,696,244    31,696,182   c W95 FAT32 (LBA)




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        A4DC262ADC25F768                       ntfs       COMPAQ
/dev/sda2        64EC36AAEC367680                       ntfs       HP_RECOVERY
/dev/sdc1        C2BC0FD9BC0FC6BF                       ntfs       Expansion Drive
/dev/sdc5        18cca15c-36dc-489d-8588-0bacc4ec38bb   ext4       
/dev/sdc6        c213d1f4-7e89-4d0a-a389-f7bd7f686601   swap       
/dev/sdd1        E8AD-290C                              vfat       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/E8AD-290C         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)




================================ sda1/boot.ini: ================================


--------------------------------------------------------------------------------
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------


```
**RESULTS2** (after running testdisk on LiveCD) Syslinux is my flashdrive that has bootinfo on it; it's a bootable MacPup Linux USB...just ignore it.
```

============================= Boot Info Summary: ===============================


 => Testdisk is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdd.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /ntdetect.com


sdc1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdc2: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  


sdc5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sdc6: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info:  


sdd1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......Sf.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 845056 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ldlinux.sys


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *             63   135,749,249   135,749,187   7 NTFS / exFAT / HPFS
/dev/sda2         135,765,315   156,280,319    20,515,005   7 NTFS / exFAT / HPFS




Drive: sdc _____________________________________________________________________


Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdc1                  63   440,960,921   440,960,859   7 NTFS / exFAT / HPFS
/dev/sdc2         440,961,022   625,141,759   184,180,738   5 Extended
/dev/sdc5         440,961,024   618,999,807   178,038,784  83 Linux
/dev/sdc6         619,001,856   625,141,759     6,139,904  82 Linux swap / Solaris




Drive: sdd _____________________________________________________________________


Disk /dev/sdd: 16.2 GB, 16231956480 bytes
255 heads, 63 sectors/track, 1973 cylinders, total 31703040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdd1    *             63    31,696,244    31,696,182   c W95 FAT32 (LBA)




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        A4DC262ADC25F768                       ntfs       COMPAQ
/dev/sda2        64EC36AAEC367680                       ntfs       HP_RECOVERY
/dev/sdc1        C2BC0FD9BC0FC6BF                       ntfs       Expansion Drive
/dev/sdc5        18cca15c-36dc-489d-8588-0bacc4ec38bb   ext4       
/dev/sdc6        c213d1f4-7e89-4d0a-a389-f7bd7f686601   swap       
/dev/sdd1        E8AD-290C                              vfat       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/COMPAQ            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/E8AD-290C         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)




================================ sda1/boot.ini: ================================


--------------------------------------------------------------------------------
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------


=========================== sdc5/boot/grub/grub.cfg: ===========================


```


I don't know what else is needed, but as you probably can tell, I'm a fix-it-myself kind of person. Well, I can't fix this myself even with hours of research, so I need some help from people who actually know what they're doing or talking about that's tailored to my scenario. I can't keep spending so much time on trying to get everything working, as I have to go to school. The computer is my LIFE and I can't use this ancient laptop primarily; I merely got it up and running for Creative Writing and the like, although it's so flippin' heavy it's not fun carrying it around (stupid Dell).
And I do NOT have Windows Recovery disk or anything of the sort, which keeps coming up in my research. Windows came pre-installed on all of our computers. I CAN, however, access my Window drive's original I386 folder through Ubuntu LiveCD, so if I need to use those files, then I will be able to. In fact, all my files and all my drives are accessible via LiveCD, which is a great source of relief for me.
I'm sorry for writing and pasting so much, but I want to make sure there's enough information to go off of. I hope someone can help me! I at least need ONE OS working on my desktop, and I don't want to reformat or reinstall Windows XP. Even if I get Ubuntu working now, I might need Windows later (since that's what my family uses and all).


Thanks!

---

### Post by Hakunka-Matata on 2011-08-28
Welcome to the forums.

OK, let's start here.  The blinking cursor on a black screen is often a driver issue with Nvidia graphics.  Let's find out if your graphics are Nvidia.
```
sudo lshw -C display
```Post the results please

**EDIT:  **Also post the output of ```
sudo fdisk -l
``` please

---

### Post by YesWeCan on 2011-08-28
Hi there. You have been round the houses a few times. I assume at the moment you can neither boot XP nor Ubuntu.

Lets sort XP out first. Your XP drive is the 80GB sda. There are two boot codes: one in the MBR and another in the sda1 partition boot sector. Both have been changed. It says "test disk" is in the MBR and I do not know what that means. I know that the Lilo code works:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
Whether the partition boot code still works is another matter. Try lilo and post the results when you tell the bios to boot the 80GB drive.

Ubuntu on the external 320GB drive. What now happens when you tell the bios to boot this drive? Do you get a Grub boot menu?

---

### Post by SiathLinux on 2011-08-28
There is a guide to 'restore' the MBR for the 'Windows' - it's an easy Google ....

You can as a 'quick' fix for a 'working system - set BIOS to boot to CD - then USB - then HDD - this will allow you to use the Ubuntu CD/DVD to reinstall Linux to the external  - setting the GRUB (locate on the external MBR) to boot with 'Windows' as the secondary boot option (this will create a 'chainloader -1 method which directs to boot from the 'C:' MBR which will not know that you have a second OS on machine) - remove your CD/DVD - reboot to a working GRUB - 

I've been Dual/Triple booting for a while now and have ran across all sorts of issues like this one - I'll gladly help anyway that I can.

On a side note - XP> on Windows OS tend to really dislike sharing :)

---

### Post by CheshireKat on 2011-08-28
Okay, I can tell you right now that I don't have an Nvidia card, but I wish I did cuz my built-in Intel chip sucks. I've run fdisk before, but I'll run it again for fresh results.
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1fedd87a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8450    67874593+   7  HPFS/NTFS
/dev/sda2            8452        9728    10257502+   7  HPFS/NTFS


```

Hmmm...I've done the Lilo thing, but I don't think I had "mbr" at the end of it, so I guess I'll try that.
Okay, so I did, and...oh my goddess, I can't believe that those three little letters were the key to getting Windows up again. **Thank you**! Now if I can just get Ubuntu properly installed. I don't think I'm doing the configuration properly when installing. I know now that "Install alongside other OS" is not the way to go, as that broke my Windows MBR, but I've tried the advanced options as well and still no go.
When I tried to boot from my external drive, it says, "error: no such partition. grub rescue>" and I can type stuff there, probably a command line or something?

---

### Post by YesWeCan on 2011-08-28
You got Windows booting again, good :)

Also good is getting a grub rescue prompt. This means Grub is installed to the MBR of your external drive and works up to a point. It works to the point where it has to find its other files in the Ubuntu root partition. For some reason the location it has hard-coded  is not correct. So you just have to tell it where Ubuntu root is and then tell it to boot it.

Like this:
First, type ls for listing the partitions that Grub can detect.
rescue> ls

You should get a list that looks *something* like this
(hd0,1), (hd0,2), (hd2,1), (hd2,2) (hd2,5) (hd2,6)

The one you are looking for ends with a 5. The partition is called sdc5 in bootinfoscript but Grub uses different terminology. So you should see (hd2,5) or maybe it won't be 2 and maybe it will be msdos5 or something. But look for the 5 and then note number just before it. My guess is it will be 2,5 but use the numbers you see.
Then do these commands:

rescue> set prefix=(hd2,5)/boot/grub
rescue> insmod (hd2,5)/boot/grub/linux.mod
rescue> set root=(hd2,5)
rescue> linux /vmlinuz root=/dev/sdc5 ro
rescue> initrd /initrd.img
rescue> boot

Once it has booted, you then need to reinstall Grub to the MBR area of the external drive.
Run sudo fsdisk -l to just check again that the external drive is sdc. Then do
sudo grub-install /dev/sdc
sudo update-grub

---

### Post by CheshireKat on 2011-08-28
Okay, I ran ls and got: (hd0) (hd0,msdos1) (hd1) (hd1,msdos2) (hd1,msdos1) (fd0)
I'm assuming the hd1,msdos2 is the correct drive, the external hard drive?

---

### Post by YesWeCan on 2011-08-28
No. There should be one with a 5 in it. Would you boot a live CD and post
sudo sfdisk -luM

---

### Post by CheshireKat on 2011-08-28
from the LiveCD? Because the grub rescue> says "unknown command" for sudo and fdisk.

---

### Post by Hakunka-Matata on 2011-08-28
As your RESULTS2.txt reported in Post# 1.

---

### Post by YesWeCan on 2011-08-28
Yes, using a live CD. I forgot that crucial detail! Also, I meant this command:
sudo sfdisk -luM

---

### Post by YesWeCan on 2011-08-28
Is this PC a little on the old side? There is an issue with some older  bios' that means the Grub initial boot code cannot see partitions that  start more than 137GB into a drive. This may be the cause.

So grub rescue reported:
[COLOR=Navy](hd0) (hd0,msdos1)[/COLOR] which is the external drive and only its 1st partition. This partition is 226GB so the others start higher than 137GB and cannot be detected.

[COLOR=Navy](hd1) (hd1,msdos1) (hd1,msdos2)[/COLOR] which is your Windows drive with 2 partitions. The first partition is 70GB so the second partition can be detected.

---

### Post by CheshireKat on 2011-08-28
Okay. *sigh* I can't wait to get this all setup...I am *so* tired of rebooting a million different times. Thanks for the help :)
The result was:
```

ubuntu@ubuntu:~$ sudo sfdisk -luM

Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sda1   *     0+ 66283- 66284-  67874593+   7  HPFS/NTFS
/dev/sda2     66291+ 76308- 10018-  10257502+   7  HPFS/NTFS
/dev/sda3         0      -      0          0    0  Empty
/dev/sda4         0      -      0          0    0  Empty

Disk /dev/sdc: 38913 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sdc1   *     0+ 215312- 215313- 220480429+   7  HPFS/NTFS
/dev/sdc2     215312+ 305244  89933-  92090369    5  Extended
/dev/sdc3         0      -      0          0    0  Empty
/dev/sdc4         0      -      0          0    0  Empty
/dev/sdc5     215313  302245  86933   89019392   83  Linux
/dev/sdc6     302247  305244   2998    3069952   82  Linux swap / Solaris

```it shows that two new empty partitions (3&4) were added to each drive, but they don't appear in GParted or anything, so I don't know what that's all about.


***EDIT: ***um, it's about three years old, but it was a rather cheap computer, nothing fancy, so it very well could have an outdated BIOS or something, compared to the recent and/or more high-tech computers.

---

### Post by YesWeCan on 2011-08-28
Ok, that all adds up.
Every formatted drive has a partition table. The type of drive format your drives have is called Master Boot Record or MBR. It always has 4 "primary" partitions and was invented by IBM in the 1970s. There is a new format out now called GUID Partition Table or GPT which allows 128+ partitions but we won't go into that.

Some time ago, they extended the MBR format to allow one primary partition to "contain" as many "logical" partitions as you like. This is just an accounting trick...all the partitions are really the same. So any partitions numbered 1 to 4 are called primary and any numbered higher are called logical. Windows does not usually use logical partitions. In fact, it now has a totally different scheme for using more than 4 called dynamic drives (I think).

Anyway, back to your problem. What you need to do is make sure the Ubuntu root partition starts at the front of the drive. More accurately, the /boot directory has to be near the front of the drive (it can be put in its own small 500MB partition).

An important question is what does the 215GiB first partition on your external drive contain? Does it have vital data in it?

---

### Post by YesWeCan on 2011-08-28
> **CheshireKat said:**
> ***EDIT: ***um, it's about three years old, but it was a rather cheap computer, nothing fancy, so it very well could have an outdated BIOS or something, compared to the recent and/or more high-tech computers.
One thing you might want to do if you can figure out how is to check whether your BIOS has been updated. Sometimes they update them to fix things like this. You'd want to check the support section on the mfr website and you would want to download and install any update using Windows. Your current BIOS version should be displayed (briefly) during power on.

---

### Post by CheshireKat on 2011-08-28
> 
An important question is what does the 215MiB first partition on your external drive contain? Does it have vital data in it? 	
Oh, you mean the 215312MiB partition? sdc1? That contains storage data--music, open office documents, some videos, and the like. So yeah, pretty vital stuff.

---

### Post by YesWeCan on 2011-08-28
> **CheshireKat said:**
> Oh, you mean the 215312MiB partition? sdc1? That contains storage data--music, open office documents, some videos, and the like. So yeah, pretty vital stuff.
Yes. So GParted can be used to move it and your other partitions so that you make a gap at the front of the drive for Ubuntu. And it should work just fine. But I am always wary of recommending messing with partitions that contain important data unless that data has been backed up somewhere.

If the BIOS has an update and this fixes the problem your external drive will probably suddenly boot Ubuntu ok without your changing anything.

I will tell you what you will need to do to move the partitions but you'll have to decide whether you want to do this without backing up the data first.

Can you give me some idea how well you know GParted? Have you used it to resize or move partitions before? Have you copied and pasted partitions before?

[edit] Oh. Another option I should just mention is that if you have a spare 4GB USB stick you can install Ubuntu on that and use the stick to boot your Ubuntu on your external disk drive. This would work fine but mean you need the USB stick inserted to boot Ubuntu.  It doesn't have to be a USB stick - it can be some old hard disk you might have lying around. Not an ideal solution, tho.

---

### Post by CheshireKat on 2011-08-28
Yeah, I used GParted to create the partitions and stuff on my external drive. I've never used it before Thursday, but I've had to use it to edit/review my partitions and check flags since then.

Is there a way to check my BIOS version through Ubuntu LiveCD? xD I really don't want to reboot AGAIN just to look at my BIOS version, especially if I do not, if fact, need to update it after all. But I will of course, if it leads to that.

---

### Post by YesWeCan on 2011-08-28
After some consideration this is what I would do. I would make a small gap at the front of the drive for a primary partition. I think the smallest GParted will make is 1MB and that is plenty. Then use this for the Ubuntu boot directory. This should be easy to do because your NTFS partition probably has 500MB still free at its end so all you need to do is resize it from the front.
Boot live CD
run GParted
Select sdc
Highlight the first partition, sdc1
Click on resize
make "Free space preceding" 500MiB
Then in the unallocated space, create a new primary partition (sdc3) of type ext4.
Apply changes.

That will be all the changes needed to the partitions.

---

### Post by YesWeCan on 2011-08-28
> **CheshireKat said:**
> Yeah, I used GParted to create the partitions and stuff on my external drive. I've never used it before Thursday, but I've had to use it to edit/review my partitions and check flags since then.

Is there a way to check my BIOS version through Ubuntu LiveCD? xD I really don't want to reboot AGAIN just to look at my BIOS version, especially if I do not, if fact, need to update it after all. But I will of course, if it leads to that.
Have a look here: [http://ubuntuforums.org/showthread.php?t=857399](http://ubuntuforums.org/showthread.php?t=857399)

---

### Post by CheshireKat on 2011-08-28
Okay, applying operations...this may take awhile. Nearly 2 hours, according to Ubuntu, but I don't put much faith in those since they frequently jump up and down between numbers.

---

### Post by YesWeCan on 2011-08-28
Once a 500MB or so boot partition is made, you need to copy your existing boot directory to it:

[COLOR=Navy]sudo mkdir /mnt/root
sudo mkdir /mnt/boot

sudo mount /dev/sdc5 /mnt/root[/COLOR] [COLOR=Navy]
sudo mount /dev/sdc3 /mnt/boot[/COLOR]

Just check that the new boot partition is actually sdc3.

[COLOR=Navy]sudo cp -ax /mnt/root/boot/* /mnt/boot[/COLOR]


Then, the fstab file needs to be changed to tell it to use the new boot partition for the /boot directory.

[COLOR=Navy]sudo blkid[/COLOR]

This will show the UUID numbers for every partition. Find the one for sdc3 and copy it

[COLOR=Navy]sudo gedit /mnt/root/etc/fstab[/COLOR]

and add a line at the end,
UUID=abcfde1234...    /boot   ext4   defaults 0 2

Then reinstall Grub, this time specifying the new boot partition

[COLOR=Navy]sudo grub-install --boot-directory=/mnt/boot /dev/sdc
[COLOR=Black]
If all that went well, you are ready to boot the external drive again.[/COLOR]
[/COLOR]

---

### Post by YesWeCan on 2011-08-28
> **CheshireKat said:**
> Okay, applying operations...this may take awhile. Nearly 2 hours, according to Ubuntu, but I don't put much faith in those since they frequently jump up and down between numbers.
It will take a long time. I think it will first shrink the partition and then move it. So it might take even longer. Don't turn the computer off until it has finished.
I have to go, but I'll check back tomorrow. It's late here. Others will be able to help if you encounter any problems.

---

### Post by YesWeCan on 2011-08-28
In my post #19 the pictures show linux root as sdc6 and swap as sdc5. Yours are the other way around. So don't get confused - it is my picture that is wrong.
[edit] I have now replaced the diagrams with the partitions correctly numbered and the boot partition 500MiB.

---

### Post by CheshireKat on 2011-08-28
Okay, thank you so much! I'll just let it continue and post an update once it's finished.

---

### Post by YesWeCan on 2011-08-28
Hey, I made a big mistake. Sorry about this. I think i am tired.
The boot partition needs to be 500 MB or so, not 1MB! That is way too small and normally I would not have made such a stupid mistake.
So you will have to let it finish and then start again. Which is a waste of your time.
Sorry about that. I must have had GB in mind. Really dumb of me.
You need to let it finish what its doing. Do not interrupt it.

Strangely, I said 500GB in post #14 but then used 1MB in the following posts. I've corrected them to avoid misleading anyone else who may read this.

---

### Post by CheshireKat on 2011-09-18
I guess I never got around to following up (and sorry for posting so late), but I did get this to work...sort of. I made a partition in the front of my external hard drive just a little over 500mb as instructed, then re-installed Ubuntu. I put the /boot mount point on the new 500+mb partition and the / mount point on the partition I wanted Ubuntu to be installed on. I believe I selected the first partition to install the boot loader on as well, but I don't remember. It installed; I tried to boot from the external hard drive and got the same error as before the re-installation. So I re-booted, this time from the Plop Boot Manager disk I made, selected the hard drive partition I wanted to boot from, and was able to get into Ubuntu. I've been using Ubuntu primarily for awhile now and am happy with it. I haven't even loaded Windows XP since I got it to work :) oh, and once it boots from the external HD, my disk drive is free so I can still use it. I just thought I'd explain my process in case anyone else can benefit from it.
Thanks for all the help!

---

