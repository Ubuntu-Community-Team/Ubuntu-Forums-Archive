---
title: "Ubuntu alongside Windows 7"
date: 2013-02-13
forum: Installation &amp; Upgrades
---

### Post by Akhj on 2013-02-13
Hello Friends,

I have purchased a new Aspire laptop with 500 GB HDD. I want to install Windows 7 & Ubuntu. Please suggest me about partitioning. For sure i'll use Windows for most of my use until i learn the basics of Ubuntu.

---

### Post by kc1di on 2013-02-13
Hello Akhj,

First Read this [page]("https://help.ubuntu.com/community/WindowsDualBoot").  It explains dual boot.

I always like to keep my personal data in a seperate /home partition so I partition my drives If I had your 500gb drive like this

250 gb for windows Drive c:/

15 gbs  Linux /
3 gbs  Linux /swap
Rest of disc /Home

But this is entirely up to you. as long as you have at least 
15 gb for Ubuntu. 

here another[ page]("http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/") that you may find helpful

good Luck

---

### Post by Mark Phelps on 2013-02-13
BEFORE you jump into dual-boot prep, you need to read the details below ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by oldfred on 2013-02-13
If dual booting I would like to suggest one more partition. A NTFS formatted shared data partition for any data you may want in both systems.

The Linux NTFS driver exposes all the hidden files & folders like in Windows turning that on. But then it becomes too easy to accidentally move or delete something vital. And Windows just does not like too much activity from outside. Best to set system partition as read-only and use the read-write shared data partition.

---

### Post by Akhj on 2013-03-01
Hello Friends,

Sorry for replying late but caught busy with work. Well Thanks a TON for great assistance. But....i ended up with formatting my existing Windows 7 :( Because after installing Ubuntu Windows was not loading even it couldn't be repaired.
What exactly i wish is Windows & Ubuntu do not share a single partition. Out of 500 GB i left 90 GB approx unpartitioned for Ubuntu.

1) What should i choose in Device for Boot Loader Installation ?
2) Like Windows do not show Ubuntu drives in Explorer the same i want with Ubuntu, that it should not list Windows Drives (But at certain points i guess it could be mounted ?)

---

### Post by oldfred on 2013-03-02
With BIOS/MBR you install the grub2 boot loader to the MBR as BIOS always boots from MBR.

It is a bit counterintuitive but you have to mount the Windows partition so you cannot automount it in Nautilus. When you mount with fstab then you can set it as read only or not readable at all.

 Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

 Hide mount but use your UUID and make the mount first.
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0

More Info:
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

---

### Post by Akhj on 2013-03-02
Thanks Oldfred but i am not that techy and couldn't get a single word :( 
Again i installed Ubuntu but when system boots up it directly goes to Windows 7 without giving any option to choose from boot menu :(

---

### Post by oldfred on 2013-03-02
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

It should not be techy to edit fstab. Just follow the details and copy & paste.

---

### Post by Akhj on 2013-03-02
This is what i got :

 ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]


============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /Boot/BCD /grldr

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 676128768 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/grub on this drive.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS 
    Boot files:        /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   102,402,047   102,195,200   7 NTFS / exFAT / HPFS
/dev/sda3         102,402,048   266,242,047   163,840,000   7 NTFS / exFAT / HPFS
/dev/sda4         266,244,094   763,967,487   497,723,394   f W95 Extended (LBA)
/dev/sda5         266,244,096   675,844,095   409,600,000   7 NTFS / exFAT / HPFS
/dev/sda6         675,846,144   677,844,991     1,998,848  83 Linux
/dev/sda7         677,847,040   685,844,479     7,997,440  82 Linux swap / Solaris
/dev/sda8         685,846,528   724,905,983    39,059,456  83 Linux
/dev/sda9         724,908,032   763,967,487    39,059,456  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7E126DDC126D99C3                       ntfs       
/dev/sda2        3C5C7AB35C7A6792                       ntfs       
/dev/sda3        BA10174A10170CCF                       ntfs       New Volume
/dev/sda5        562AF0CA2AF0A85F                       ntfs       New Volume
/dev/sda6        43f1e8aa-4040-4581-b10e-c448e1c4958f   ext4       
/dev/sda7        b28542ea-4da5-4d9e-9e30-9ad822b8c4e5   swap       
/dev/sda8        49615ffa-4df3-472f-8e36-c9937fe68824   ext4       
/dev/sda9        a1cb59a5-064e-4bca-91e3-8c22bd93c375   ext4       
/dev/sr0                                                iso9660    Ubuntu 12.04.1 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

============================= sda6/grub/grub.cfg: ==============================
```

---

### Post by oldfred on 2013-03-03
You did not install grub to the MBR but to the PBR or partition boot sector. But you have grldr in the Windows partition which is grub4dos usually from EasyBCD. Are you using EasyBCD? Some use that and find it works, but you comprimize grub2 as it is forced to squeze itself into the PBR with blocklists, not code to find the rest to grub. On a major update to grub you will probalbly have to reinstall grub to the PBR so have the liveCD handy.

       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

If you want to use grub, then just use Boot-Repair to install grub to the MBR.

---

### Post by Akhj on 2013-03-03
Yes i knew that i installed GRUB to PBR because i wanted to use the  Windows Boot loader to handle the boot sequence. Actually i don't want  to use EasyBCD to edit boot records, instead i will prefer the command  line (or something like boot.ini in earlier version of Windows).
Live  CD is with me but currently i am replying from Windows session. Will  you please help me with the Command Line instead of EasyBCD ?

Thanks & Regards

---

### Post by oldfred on 2013-03-03
I have seen some do the command line with XP by copying the PBR to a file and loading that somehow. Not sure you can even do that with Windows 7. But you would somehow have to manually edit BCD and tell it to load PBR file.

But Why? Grub works just fine and for those that insist on using Windows they use EasyBCD.

---

### Post by Akhj on 2013-03-03
[IMG][[img=http://s13.postimage.org/rstsll92b/Ubuntu.jpg]]("http://postimage.org/image/rstsll92b/")[/IMG]

I want my screen look like this.

---

### Post by oldfred on 2013-03-03
If you do a totally custom menu in grub2, you can have that. 
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)



As I said I do not know how to do that. I think that is a EasyBCD type screen?

---

