---
title: "Installer can't see drives.  Alternate installer doesn't detect Windows. No boot."
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by Engineeringtech on 2011-02-16
Hi!  I'm new to Linux.  No familiarity with installation issues, commands, etc.   I have a Windows XP system, and wanted to install Ubuntu to a 100 GB XT3 partition on the same drive.  I was told I could chainload Ubuntu from the NT Loader menu.  I booted from a Ubuntu 10.04 CD and ran the installer.  It didn't find any hard drives.  On a hunch, I tried the 10.04 alternate installer CD.  That DID find the hard drive and partitions.  I had the installer make /dev/sda7 (the XT3 partition) the root.  Installation proceeded smoothly, but then the installer told me it did not see any other OS's on my drive!  Why?  I directed the installer to place grub on /dev/sda7 instead of the MBR.  

Per the instructions I was given, I used DD to copy the first 512 bytes of /dev/sda7 to the Windows primary partition (sda1) as bootloader.lnx.   But the resulting file is empty, and it won't boot.   I repeated the whole process - formatting, installing FOUR times, and same results.   I have no idea where GRUB was installed.  It is apparently not in the MBR, because I still have my normal Windows boot.

I downloaded the 10.10 alternate installer and got the same exact results.  Even switched from XT3 to XT4.   

After two weeks of this nonsense, I still have yet to see Linux boot.  

Can anyone help?

Thanks for your time.

---

### Post by Rubi1200 on 2011-02-17
Hi and welcome to the forums :-)

Two things:

1. who "told" you? "Per the instructions I was given;" whose instructions?

2. please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

We need this information to help you sort this out.

---

### Post by Engineeringtech on 2011-02-17
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Two things:

1. who "told" you? "Per the instructions I was given;" whose instructions?

2. please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

We need this information to help you sort this out.


Sir:
Thanks for replying.  A friend of mine, who has used Linux for years, gave me a written procedure to chainload Linux from NTLDR.  It worked on an old laptop with Ubuntu 9.04, but the laptop failed due to broken hardware before I could learn anything about Linux.  I've seen the same procedure in dozens of postings on the internet and Ubuntu forums. It involves installing to an XT3 or XT4 partition, loading Grub on the same partition, and then using the "dd" command to copy the first 512 bites of the partition to a file (bootsector.lnx) which can be referenced in windows "boot.ini".  

The problems I've had getting 10.04 or 10.10 installed are similar to those reported at: [http://ubuntuforums.org/showthread.php?t=1608255](http://ubuntuforums.org/showthread.php?t=1608255)    (I should note that I have also been unsuccessful with a Fedora 14 installer disk.)  However, the alternate install CD (suggested as a solution), only solved one of the problems.  It found  partitions to install to, but  did not detect my Windows installation.  It asked me where to place Grub, and I directed it to place it on the install partition.  Unfortunately,  the bootsector.lnx file I created with dd, was blank.  I have tried alternate SATA ports, both XT3 and XT4 partitions, and legacy drive support.  My suspicion is that the GRUB2 used in 10.04 and 10.10 cannot be booted in the manner my friend instructed me.

I downloaded your script on another machine, and placed it on a floppy disk.  I then booted into linux on the target machine with my 10.04 Live CD,  However, although that machine has a standard floppy drive, the drive does not mount, and is not found in the "places" pulldown menu.  In fact, no removable drives are found there.  

So with no way to get your target script into the target machine, I'm at an impasse.  I suppose I can print it out, and recreate it.  That will take some time.

Have any other ideas?

---

### Post by Engineeringtech on 2011-02-17
Ok, I managed to find a USB drive to get the script file into the target machine.  Attached is the Results.txt file

---

### Post by Rubi1200 on 2011-02-18
Thanks for getting the script results back here. This is important if we are to help you.

There seem to be a number of issues going on, including partitions not being mounted, RAID, and an HFS partition.

My experience with RAID arrays is limited, therefore I will ask someone with more experience to take a look at this.

Meantime, I suggest that you not make further changes to the current setup until we can move forward with sorting out what is going on here.

Thanks.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/mapper/isw_djghjfdhfj_Multiboot

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy
mount: /dev/sda5 already mounted or sda5 busy

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy
mount: /dev/sda5 already mounted or sda5 busy
mount: /dev/sda6 already mounted or sda6 busy

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy
mount: /dev/sda5 already mounted or sda5 busy
mount: /dev/sda6 already mounted or sda6 busy
mount: /dev/sda7 already mounted or sda7 busy

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy
mount: /dev/sda5 already mounted or sda5 busy
mount: /dev/sda6 already mounted or sda6 busy
mount: /dev/sda7 already mounted or sda7 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda10: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy
mount: /dev/sda5 already mounted or sda5 busy
mount: /dev/sda6 already mounted or sda6 busy
mount: /dev/sda7 already mounted or sda7 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda10 already mounted or sda10 busy

isw_djghjfdhfj_Multiboot1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  MS-DOS 6.22
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

isw_djghjfdhfj_Multiboot2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_djghjfdhfj_Multiboot5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy
mount: /dev/sda5 already mounted or sda5 busy
mount: /dev/sda6 already mounted or sda6 busy
mount: /dev/sda7 already mounted or sda7 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda10 already mounted or sda10 busy
mount: unknown filesystem type ''

isw_djghjfdhfj_Multiboot6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy
mount: /dev/sda5 already mounted or sda5 busy
mount: /dev/sda6 already mounted or sda6 busy
mount: /dev/sda7 already mounted or sda7 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda10 already mounted or sda10 busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_djghjfdhfj_Multiboot7: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy
mount: /dev/sda5 already mounted or sda5 busy
mount: /dev/sda6 already mounted or sda6 busy
mount: /dev/sda7 already mounted or sda7 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda10 already mounted or sda10 busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_djghjfdhfj_Multiboot8: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy
mount: /dev/sda5 already mounted or sda5 busy
mount: /dev/sda6 already mounted or sda6 busy
mount: /dev/sda7 already mounted or sda7 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda10 already mounted or sda10 busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_djghjfdhfj_Multiboot9: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy
mount: /dev/sda5 already mounted or sda5 busy
mount: /dev/sda6 already mounted or sda6 busy
mount: /dev/sda7 already mounted or sda7 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda10 already mounted or sda10 busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_djghjfdhfj_Multiboot10: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy
mount: /dev/sda5 already mounted or sda5 busy
mount: /dev/sda6 already mounted or sda6 busy
mount: /dev/sda7 already mounted or sda7 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda10 already mounted or sda10 busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     1,028,159     1,028,097   6 FAT16
/dev/sda2           1,028,221   976,768,064   975,739,844   f W95 Ext d (LBA)
/dev/sda5           1,028,223   205,840,844   204,812,622   b W95 FAT32
/dev/sda6         205,840,908   222,227,144    16,386,237   b W95 FAT32
/dev/sda7         222,227,208   427,039,829   204,812,622  83 Linux
/dev/sda8         427,039,893   431,248,859     4,208,967  82 Linux swap / Solaris
/dev/sda9         431,248,923   956,301,254   525,052,332   7 HPFS/NTFS
/dev/sda10        956,301,318   976,768,064    20,466,747  af HFS


Drive: isw_djghjfdhfj_Multiboot ___________________ _____________________________________________________

Disk /dev/mapper/isw_djghjfdhfj_Multiboot: 500.1 GB, 500104826880 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976767240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_djghjfdhfj_Multiboot1   *             63     1,028,159     1,028,097   6 FAT16
/dev/mapper/isw_djghjfdhfj_Multiboot2          1,028,221   976,768,064   975,739,844   f W95 Ext d (LBA)
/dev/mapper/isw_djghjfdhfj_Multiboot5          1,028,223   205,840,844   204,812,622   b W95 FAT32
/dev/mapper/isw_djghjfdhfj_Multiboot6        205,840,908   222,227,144    16,386,237   b W95 FAT32
/dev/mapper/isw_djghjfdhfj_Multiboot7        222,227,208   427,039,829   204,812,622  83 Linux
/dev/mapper/isw_djghjfdhfj_Multiboot8        427,039,893   431,248,859     4,208,967  82 Linux swap / Solaris
/dev/mapper/isw_djghjfdhfj_Multiboot9        431,248,923   956,301,254   525,052,332   7 HPFS/NTFS
/dev/mapper/isw_djghjfdhfj_Multiboot10        956,301,318   976,768,064    20,466,747  af HFS

/dev/mapper/isw_djghjfdhfj_Multiboot2 ends after the last sector of /dev/mapper/isw_djghjfdhfj_Multiboot
/dev/mapper/isw_djghjfdhfj_Multiboot10 ends after the last sector of /dev/mapper/isw_djghjfdhfj_Multiboot

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_djghjfdhfj_Multiboot1 3E47-9144                              vfat       DOS                           
/dev/mapper/isw_djghjfdhfj_Multiboot: PTTYPE="dos" 
/dev/sda10       627b8bc1-828e-344a-8efb-13f61e48f528   hfsplus    Mac Volume                    
/dev/sda1        3E47-9144                              vfat       DOS                           
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5ABE-8C00                              vfat       WINDOWS                       
/dev/sda6        C55A-5E00                              vfat       WIN_SWAP                      
/dev/sda7        14d907ca-8924-479c-88b3-710f4ab34273   ext4       LINUX                         
/dev/sda8                                               swap                                     
/dev/sda9        4233A174FDF5EAB9                       ntfs       DATA                          
/dev/sda                                                isw_raid_member                               
error: /dev/mapper/isw_djghjfdhfj_Multiboot10: No such file or directory
error: /dev/mapper/isw_djghjfdhfj_Multiboot2: No such file or directory
error: /dev/mapper/isw_djghjfdhfj_Multiboot5: No such file or directory
error: /dev/mapper/isw_djghjfdhfj_Multiboot6: No such file or directory
error: /dev/mapper/isw_djghjfdhfj_Multiboot7: No such file or directory
error: /dev/mapper/isw_djghjfdhfj_Multiboot8: No such file or directory
error: /dev/mapper/isw_djghjfdhfj_Multiboot9: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


===================== isw_djghjfdhfj_Multiboot1/boot.ini: =====================

[boot loader] 
timeout=08 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="XP Pro" /fastdetect 
C:\ = "MS-DOS" 
C:\UBUNTU.LNX = "Ubuntu 10.10" 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on isw_djghjfdhfj_Multiboot2


Unknown BootLoader  on isw_djghjfdhfj_Multiboot5


Unknown BootLoader  on isw_djghjfdhfj_Multiboot6


Unknown BootLoader  on isw_djghjfdhfj_Multiboot7


Unknown BootLoader  on isw_djghjfdhfj_Multiboot8


Unknown BootLoader  on isw_djghjfdhfj_Multiboot9


Unknown BootLoader  on isw_djghjfdhfj_Multiboot10



=============================== StdErr Messages: ===============================

ERROR: isw: wrong number of devices in RAID set "isw_djghjfdhfj_Multiboot" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_djghjfdhfj_Multiboot" [1/2] on /dev/sda
ERROR: creating degraded mirror mapping for "isw_djghjfdhfj_Multiboot"
ERROR: dos: partition address past end of RAID device
ERROR: isw: wrong number of devices in RAID set "isw_djghjfdhfj_Multiboot" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_djghjfdhfj_Multiboot" [1/2] on /dev/sda
hexdump: /dev/mapper/isw_djghjfdhfj_Multiboot2: No such file or directory
hexdump: /dev/mapper/isw_djghjfdhfj_Multiboot2: No such file or directory
hexdump: /dev/mapper/isw_djghjfdhfj_Multiboot5: No such file or directory
hexdump: /dev/mapper/isw_djghjfdhfj_Multiboot5: No such file or directory
hexdump: /dev/mapper/isw_djghjfdhfj_Multiboot6: No such file or directory
hexdump: /dev/mapper/isw_djghjfdhfj_Multiboot6: No such file or directory
hexdump: /dev/mapper/isw_djghjfdhfj_Multiboot7: No such file or directory
hexdump: /dev/mapper/isw_djghjfdhfj_Multiboot7: No such file or directory
hexdump: /dev/mapper/isw_djghjfdhfj_Multiboot8: No such file or directory
hexdump: /dev/mapper/isw_djghjfdhfj_Multiboot8: No such file or directory
hexdump: /dev/mapper/isw_djghjfdhfj_Multiboot9: No such file or directory
hexdump: /dev/mapper/isw_djghjfdhfj_Multiboot9: No such file or directory
hexdump: /dev/mapper/isw_djghjfdhfj_Multiboot10: No such file or directory
hexdump: /dev/mapper/isw_djghjfdhfj_Multiboot10: No such file or directory
ERROR: isw: wrong number of devices in RAID set "isw_djghjfdhfj_Multiboot" [1/2] on /dev/sda
ERROR: dos: partition address past end of RAID device
```

---

### Post by ronparent on 2011-02-18
Ok Rubi1200, I see what you mean. It appears that the sda had at one time been part of a raid1 set. That will often allow the drive to function to a degree as a 'broken' raid since one drive of the raid set is supposed to mirror the other and is complete in itself. Since dmraid is activating the raid on boot (to the live cd) the non raid partitions are already mounted! At least that is what I think is going on. Win xp without the raid driver won't know that there is any raid there. Ubuntu will function the same way with out dmraid. 

Since there appears to be only one drive in the system, I would advise verifying that the drive is not configured in the raid bios. There is a danger that the existing partition table could be destroyed in the process, but unlikely. Then uninstall dmraid from the live cd session and verify that the system functions properly and that a normal grub reinstall can be made to sda. The OP will also have to uninstall dmraid from the installation once he is able to boot to it.

Normally I would suggest erasing the raid meta data, but, it might be safer to leave it alone in this case (since the system seems to already have been mucked around excessively but still contains valid data). The meta data should cause no problem without raid drivers or dmraid as long as the user remains aware of it in the case of a future clean install of Ubuntu. I will keep an eye on this thread to help if needed. Good luck.

---

### Post by oldfred on 2011-02-18
I also do not know much about RAID, but see lots of issues.

I have seen your instructions on installing grub to a partition and copying the image to boot from windows. But that always was for grub legacy and now we are using grub2. Grub2 gives major warnings about installing to a partition. It should work, at least initially but is considered unreliable. I like grub2 and it is a good boot loader. It makes booting simple, not complex like trying to maintain a boot image and use the windows boot loader that is not designed to boot other systems.

Also your windows boot.ini says it is in partition 2 but windows is in partition 5. Windows officially only boots from/thru a primary partition, so are you booting DOS then XP? I do not understand how that even works.

While I normally like to try to repair a system even if it takes a long time, you may want to consider just backing up all your data, scrub drive,  and doing a clean install of XP, then install Ubuntu. Grub2 will let you boot both without any hassles.

---

### Post by Stephann on 2011-02-18
Hiya ET,

Looking your partition table over, it looks like your drive has a pretty complex partitioning schema.  Your system has NTFS, HFSPlus, RAID, EXT4, and linux swap partitions; no small feat.  Was this a dual boot mac/windows machine?  

The very best advice I could give you is to get an external drive at least equal or larger than your existing hard drive.  Boot Ubuntu (or some other live linux file system, knoppix, Gparted live, etc) and do a 'dd' (DiskDump) from your computer's drive to the external drive.  This will make your life infinitely easier in cleaning up your existing drive.  From there, you can first clear the raid 'superblocks' (bits of information written on your drive to alert the computer that there's a raid system) using the 'mdadm --remove /dev/isw_djghjfdhfj_Multiboot' command (which will clear the system of superblocks) and then initialize your partition table on your computer's drive (essentially wiping it clean.)  From there, you can create a partition schema that will better serve your needs, something like (assuming a 500 gig drive):

sda1 - Windows - 80 gigs
sda2 - Extended Partition 
sda3 - Linux Swap - 2 gigs
sda4 - Linux Root - 10 gigs
sda5 - Linux Home - 20 gigs
sda6 - 'Data' - Remaining Drive (NTFS formatted, so that you can access music, video, documents, etc from both Linux and Windows)

For sake of brevity, I haven't included step by step instructions.  I'm happy to clarify and provide them, if you'd like to go this route.

Best of luck to you.

---

### Post by Engineeringtech on 2011-02-18
I would like to thank everyone for answering.  Yes, my INITIAL GOAL was to make this a triple boot (DOS, XP and Ubuntu) on a mirrored RAID 1 array.  I use some engineering utilities that ONLY operate under 6.22 DOS. I need XP for my CAD package.  And I wanted the security and advertised ease of use of UBUNTU for web browsing, etc. The HFS partition is there only because at some time in the future I wanted to emulate my old Mac long enough to export some data files.  I've done the emulation before, and it helps if you have a Mac partition.  I have setup the triple boot before on an old computer with SCSI drives and a SCSI controller.  It worked fine, but the hardware failed before I could learn Linux.

Not wanting to buy new SCSI gear, I bought some SATA drives (WD), and created a RAID1 array using the (ICH10R) tools in my motherboard BIOS.  Normally, the next step with fakeraid is to load a driver while installing Windows.  But I wanted my OS's installed in sequence (DOS, WINDOWS, LINUX) to make use of NTLDR.  Partition Magic was the only tool that would recognize the array before the driver was loaded.  When I ran into problems with the installations and boot manager, I got a friend involved.  He's been using Linux for years. He finally gave up after several months of on and off work.  Never got all three to boot. 

He recommended that I buy a hardware SATA RAID card.  So I shelled out $185 for a Highpoint card, and hooked it up to my drives.  The array said it was "normal", but three weeks later, I was STILL trying to get ANY OS to install.  High point never responded to any of my pleas for help, and I sent the card back.

At this point, I thought I would just use one of my drives, connected to the ICH10R sata ports.  But I did not enable RAID in the BIOS.  I set it to IDE.    Partition Magic no longer worked, and I bought Partition Commander to do the partitioning and reformating.  I reformated every single partition.  Didn't that wipe out the RAID information?

Not sure where I should go from here.  I'm not sure I am experienced enough to do this without someone to walk me through it.   Western Digital has a tool to write zeros to the drive.  Sure hate to do that, the partitioning, the formatting, the installation of DOS and Windows all over again.

And I'm still not sure the Grub2 can be chainloaded from NTLDR. The Ubunto 10.10 Alternate install CD detected the partitions, and it disabled the RAID information.  It even allowed me to instal "grub" (grub2?) at /dev/sda7.  But the bootsect.lnx I generated with DD contains all blanks, and won't boot Ubuntu. Does that mean GRUB WASN'T installed to /sdev/sda7?    Is there any chance the LIVE CD would allow me to place GRUB on the Ubuntu install partition, where I could use DD to create a "bootsect.lnx" file I can reference in "boot.ini"?

All I ever really wanted with the RAID was a reliable system I could use for CAD.  If I had known it would mess with me for all these months, I never would have attempted using it. Fakeraid OR hardware raid.

---

### Post by oldfred on 2011-02-18
If you are sure you do not want RAID, this will remove the meta data from the drive.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

You then could rerun script as it will see all the partitions that it could not see into without mdadm package.

---

### Post by matt_symes on 2011-02-18
l

---

### Post by Engineeringtech on 2011-02-18
> **oldfred said:**
> If you are sure you do not want RAID, this will remove the meta data from the drive.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

You then could rerun script as it will see all the partitions that it could not see into without mdadm package.

Thanks.  I will try this.   I am assuming I should boot from LiveRaid to do it, right?  

Do you have any idea how I go about getting Grub2 to work with the NT bootloader?  Can I still install Grub to the Linux install partition, then copy the first 512 bytes to a file, and then reference that file in Boot.ini?  Whether I fix the RAID or not, the ultimate goal is to get it to boot.

JC

---

### Post by ronparent on 2011-02-18
The easiest route to getting your system to boot is to reinstall grub from a live cd. That is described here: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

The problem you have probably been experiencing is that Ubuntu with dmraid is blocking you from installing the grub boot loader to sda because sda is identified as a raid member. Simply boot to the live cd and uninstall dmraid from the live cd session (ie sudo apt-get purge dmraid). Once grub is reinstalled you should be able to boot into the install on your drive - ignore any raid errors and again uninstall dmraid permanently. I suggest this rather than trying to use the NTLDR for multibooting. This is fast, easy and should get you up and running.

Normally I recommend erasing the raid meta data which remains on both drives to which you had attempted a raid setup. There is some danger (slight) of erasing your current partiton tables and you may want to ignore that measure for the time being.

---

### Post by Stephann on 2011-02-18
Thanks ET, that's a good deal more information, that explains a lot of the problems you're facing.

Speaking from experience, the type of triple booting you're hoping to do, while entirely possible, is a bit like building an entirely new house next to yours, so that you can have an extra bathroom.  Sure, it's a functional system and does the job, but it's a looooot of time and energy (as you've found.)

All modern motherboards have a 'boot menu' when you boot, usually activated by hitting F12 or some such, and usually that flashes on your bios screen when you boot, saying "HIT F10 TO SELECT BOOT DEVICE."  Given that you have three distinct systems, your best bet is to use at *least* two different drives.  In fact, using a different drive for each system would probably be your best bet, as it completely bypasses all of your grub issues, conflicting system issues, etc.  That said, Ubuntu and XP certainly do play nicely, leaving you in a spot where you could install DOS to the secondary drive.  The other (better, in my humble opinion) option is to run DOS from a virtual machine.  Some info on how to achieve this can be found here:  [http://communities.vmware.com/message/476734](http://communities.vmware.com/message/476734)

So, with this in mind, the raid issue is simple to clear up.  My advice, again, is to boot using a live CD system, then clone your drive to an external drive, so that you don't lose any data.  Once that's done, you can safely initialize your drive; it doesn't require writing 0s to every sector, it simply wipes the partition table (the first 512 kilobytes of the drive) rendering it 'new' to any system that looks at it.  It won't see any partitions to go looking for raid bytes.  From there, you can safely repartition using gparted (a nice, handy graphical tool.  Alternatively, once you've cloned your drive, you can simply reboot and install XP, taking care to create a windows partition suitable for your needs, and leaving the rest of the disk to configure in Ubuntu.

Again, I can elaborate with a step by step if you'd like to go that route.

---

### Post by Engineeringtech on 2011-02-18
Thanks to everyone who responded.  I have plenty of good ideas now.  Now I have to mull over this and decide which is the best approach for me.  Give me a few days.  I'll try to remember to check back in with a progress report.

---

### Post by Engineeringtech on 2011-02-19
> **oldfred said:**
> If you are sure you do not want RAID, this will remove the meta data from the drive.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

You then could rerun script as it will see all the partitions that it could not see into without mdadm package.


Oldfred,

So many nice people have tried to help me in this thread, that I'm afraid I  have gotten confused, and uncertain of the best approach.  I think I have to pick one approach and hope for the best.  Since your suggestion (above) really peaked my interest, I'm directing these comments and questions to you, hoping you'll be able to give me some further conclusion.  If you can't afford the time, or have nothing further to add, I will understand.  

Some people said I should zero my drive, and start from scratch.   I  don't want to do any of these things if I can help it.  It took weeks of  experimentation -  partitioning, formatting, and installing DOS, Windows  and Linux to arrive at a working DOS / Windows dual boot.  Another  person suggested I use a separate drive for Linux, and run DOS in a virtual machine.    If I'm not going to run RAID, I don't want to waste power running a second hard drive, when there's plenty of room for all three OS's on one drive.  

Right now I have a WORKING dual boot system.  DOS and Windows.  I just don't have a bootable Linux partition.  If it is at all possible to add Linux without destroying my dual boot, I'm eager to do what is required.   **Will the method you suggest above remove the RAID Meta Data WITHOUT damaging my existing DOS &  Windows boot?** 

And will the removal of the meta data correct the boot problems?   Recall that I have tried both the Ubuntu 10.10 Live CD and Alternate installers.   The Live CD installer did not find a drive.  The Alternate installer found the drive, ignored the meta data, and allowed me to install on sda7.  However, it did not detect my DOS and Windows installations.  If I had allowed it to install GRUB2 to the MBR, it would have damaged my DOS and Windows boot.  So I directed it to install Grub2 to SDA7. 

The question is, how do I get GRUB2 to chainload from the Windows NTLDR?   I've tried to DD the first 512 bytes of SDA7 to a file, and reference that file in BOOT.INI.  But that file appears to be blank, and does not boot Linux.    WILL the removal of the RAID meta data fix the Grub2 problem?  Or will GRUB 2 just not work with NTLDR?

Thank you for your time.

JC.

---

### Post by oldfred on 2011-02-20
A lot of users have used the commands to remove the RAID metadata and I have not seen any with complaints. That said any time you are doing system related changes, backups are important.

I do not understand why you do not want grub2 in the MBR. It boots just about anything. 

If you installed grub2 to the PBR and used dd to copy it and it was all 00's then it was not installed, or you copied the wrong sectors. Boot script always shows data in partition boot sector if it is installed there.

Even if a windows boot is damaged, it is easy to repair, if the partition still has all the system. With XP you can do all the repairs except chkdsk from a Linux liveCD. Other versions of windows & chkdsk require a windows repair CD.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Engineeringtech on 2011-02-21
Oldfred,

Thanks again.  The Ubuntu installer never detected my bootable DOS or Windows installations,  so that is why I didn't want GRUB put in the MBR.  Right now I have a working DOS and XP boot, controlled by NTLDR.  I didn't want to break that.

I've attempted the Linux install 4 times.  Each time, I reformatted first, then installed Ubuntu to /dev/sda7.  Every time, it failed to detect my DOS or Windows installations, and gave me the choice to install Grub (Grub2?)  elsewhere.  I directed  it to install to /dev/sda7.  But I don't know how to get the Linux to boot.  I've followed the only procedure I know.  I open a terminal, and type "mount -t vfat /dev/sda1 /mnt"  followed by "dd if=/dev/sda7 of=/mnt/bootsect.lnx bs=512 count=1".  This results in the creation of bootsect.lnx, but the file is all zeros.  

Did the Results.txt file I sent show an installation of Ubuntu to sda7?  And does it show Grub or Grub2 in the place I directed it to install?  If so, why is my bootsect.lnx all zeros?

I'd like to try and remove the RAID meta data using the method you described if you don't think it is going to damage my DOS and Windows boot, and if you think it will make Grub work properly.   I've done backups of data on active windows partitions, but I don't know how to backup my drive image, so I could restore this dual boot.  

Jim C.

---

### Post by oldfred on 2011-02-21
The installer and grub's osprober are not the same. Grub2 will find your other installs or we can help you on the rare occasions it does not.

Grub2 in a partition is not consisdered reliable.

The boot script does not parse LVM or RAID partitions unless the additional software to manage them is also installed, so it did not see all your system.

My suggestions is remove RAID and install grub2 to the MBR. We can easily reinstall a windows boot loader if you end up not likeing grub2.

---

### Post by ronparent on 2011-02-21
The raid meta data is located at the end of the disk and its removal will in no way damage your windows or DOS. Just follow oldfred's instructions.

---

### Post by Engineeringtech on 2011-02-21
**I removed the RAID meta data exactly per Oldfred's instructions.  But before I get into that, I have to discuss with everyone where my head is on this project.**

I just realized that during this whole thread I have repeatedly asked a question that has gone unanswered.  Namely, HOW do you boot Ubuntu 10.10 from NTLDR when Grub (or is it Grub2?) has been placed on the Linux install partition?  Yes, I know you say it is unreliable.   That means you have done it, right?   HOW?  Was it the method I talked about in my first post?  (DD'ing the first 512 bytes of the partition to a file, and pointing to that file in Boot.ini?)  If that is a valid  method (reliable or not), why is the bootsect.lnx I generate always BLANK?  I know from booting the LiveCD and looking at hard drive install partition that thee is a folder called "grub". So the installer must have installed Grub.  RIGHT? 

I know you prefer I use Grub to boot the OS's, and install it to the MBR.  But the installer has REPEATEDLY failed to detect my other OS's (DOS and Windows).  Even AFTER I removed the RAID meta data.   I DO NOT want to mess up my DOS / WIndows dual boot!  At least that is working!   I know you said you think you can recover Windows if I install Grub to the MBR.  Are you CERTAIN about that?  What about DOS?  I don't want to run DOS "virtual".  That doesn't do well with peripherals.  

I want you to understand where I am coming from with this aversion to ditch NTLDR.  I built this system from brand new hardware in March of '09.  In the almost 2 years I've had this $2000  lump of iron sitting on my desktop, the hardware has already become obsolete.  As of now I have yet to do one half hour of work with it!    And that work was lost when the controller in my first RAID1 setup (SCSI) failed.    I have installed drives and controllers, partitioned and formatted, installed OS's, rebooted and rebooted ad nauseum until I am just SICK of it!  I may have these drives worn out before I get any work done with them!   I started with  a SCSI RAID 0 setup that took days to configure and whose controller failed hours after it was finally working.  Progressed to a SATA RAID1 array running from the motherboard's fakeRAID.  That defied at least SIX MONTHS attempts to get it to work, and even the efforts of a very experience tech from my employer's IT department.     I was then  told to replace the motherboard.  And I did.  That was followed by another three months trying to get the fakerRAID to work.   I was then told to buy a hardware RAID card.  Highpoint suggested a card that would do the triple boot.   I  sunk another $200 into that, and suffered another month of grief.  Now I have downsized my expectations (I nixed the RAID), and am just trying to install the triple boot to ONE drive.  And I can't even seem to get that to work!   I did not buy this system to be a permanent troubleshooting platform or to watch reboots!

** I am not resistant to following instructions, but I can't do it forever without seeing results.   I am about ready to give up on Linux altogether. **

This afternoon,  I booted from the 10.10 Alternate Install CD and for the FIFTH time formatted SDA7  (XT4), made it the "root" and installed there.  For the FIFTH time neither of my two working OS's were detected, and I was asked to install Grub to the MBR.  Since I do not want to mess up my dual boot, I AGAIN directed GRUB (or is it GRUB2?)  to /dev/sda7.   The installer gave me every indication it installed GRUB, and asked me to restart.  I rebooted with the LiveCD, opened a terminal window,  uninstalled DMRAID just to be sure, and dd'd the first 512 bytes of SDA7 to bootsect.lnx.  AGAIN I wound up with a blank file.   

So I am going to ask again.... how do I  start the Linux I have installed so many times?  Where is the bootloader?   And how do I point NTLDR to it?  Doesn't the "results.txt" file I posted here give you any clues as to where the Linux bootloader is?  Why is the first 512 bytes of SDA7 blank?  If GRUB2 is not going to do this for me, is there any way to delete it, and install GRUB?  (That's what we had working on the SCSI Array.)

Sorry if you think I am being uncooperative.  I'm just sick of trying things that don't work.

JC

---

### Post by Shadow Wolfington on 2011-02-21
I have a similar problem. My computer will load grub, but it only gives me the option to boot Ubuntu or do a memory test. It won't let me get to my Vista partition. I am completely new to Linux and this problem has been bothering me.

---

### Post by oldfred on 2011-02-22
@Shadow Wolfington Welcome to the forums, but please do not hijack thread. Your issues are not like this thread. Start a new thread and post the boot_info script as posted above.

If your dd'd files is all 00s then you did not install grub2 to the partition or you dd'd the wrong sector. Yes that is how some users who fight the new grub2 boot loader have booted. I used to see it more with old grub which installed to the partition without complaint. I have installed both old grub & grub2 to a partition, but grub2 requires a force command. It used to install without the force as part of the initial install.

If you have removed RAID metadata script should tell a whole lot more & if grub2 was installed to the partition. 

Rerun script so we can see what is where.

If you understand how windows (& dos) boot, it may help. While this link is primarily about Vista it applies to all windows, and any system booting with MBR (msdos).

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

We have installed lilo's boot loader to boot windows as that is easy to install from Linux. Windows (or lilo) code in the MBR only looks for a boot flag (active partition) and jumps to the code in that partition to continue to boot. Grub bypasses the MBR and jumps to the partition's boot to boot windows.

I also have see where someone installed grub to a partition, moved boot  flag to that partition and still used the windows boot loader to boot grub. Then from grub, they booted windows or Ubuntu. At first I did not understand how it could even work.

---

### Post by Engineeringtech on 2011-02-22
Not tntirely the same problem. I suspect in your case, you used the standard installer.  It did not detect your Windows installation, but  installed Grub (actually Grub2) to the default location, the MBR.  That disabled your Windows boot.  Some of the guys on this forum can supposeldy tell you how to fix that.  

I began with the "alternate install CD" to get the option to install Grub elsewhere.  This installer also did not detect my OS's (DOS and Windows XP).  However, the installer gave me the option to install Grub to an alternate location, so as to avoid damaging my DOS and Windows boot.  I installed Grub (probably was Grub2) to the root directory of the Linux install partition. However, I am still waiting (and hoping) someone on this forum will tell me how to boot Linux from that location.  

In my case I had the added complication that my drives had leftover information from my attempts to setup a RAID array.  So I had to get rid of this "meta data".

I hope you get your problem solved.  I for one am tired of running endless installations and installed.  I want to use Linux, and right now, I can't get it to boot.

I am wondering now if it would be best that I ditch Ubuntu altogether.

JC

---

### Post by oldfred on 2011-02-22
I have not used the alternate install CD. It may not include the grub osprober, which is then easy to install and will find your windows & dos installs.

---

### Post by Engineeringtech on 2011-02-22
Oldfred,

I'm trying, but I understood very little of your post #23.  I don't know what the "force" command is, and how to use it.  

I switched to the alternate install CD because the installer on the Live CD never found any hard disk or partitions to install to.  (GPARTED could see the drive and partitions.)   

As for the alternate installer... Are you telling me it's defective or won't do what I want it to do?   Every time I ran through the install process I had every indication of success.  No error messages.  Why would the installer tell me it did not find any other OS's if OSPROBER had not run?

I was given a choice to place grub on the MBR or any partition I wanted.  If Grub2 can't be used from anywhere but the MBR, why does the installer give that option?  I was shown some sample paths, and then asked to enter a path.  I entered "/dev/sda7", the same partition I selected as the install partition.  Can't I assume Grub was placed in the install partition?   

If you have a way to install GRUB2 properly, and a way to chainload it from NTLDR, then let me know.  I'm not going to install it to the MBR  and risk screwing up my double boot. I just don't have a lot of confidence at this point that I will be able to recover DOS and Windows.  

I'll run the bootscript again and get you the results.txt file tomorrow.  Haven't been feeling well.  


Thank you for your time.

---

### Post by Engineeringtech on 2011-02-22
Ok Oldfred, 

I've run the bootscript again.   Here is the Results.txt file.  If it leads you to any solution to booting Ubuntu, I'm all ears.  

If Grub2 won't boot from the install partition, then can I easily remove it and install Grub Legacy?

JC

---

### Post by oldfred on 2011-02-23
Boot script now shows everything like it should. You did not install grub2 to the partition as it would show it.

Your XP says it is in sda2, but that is now your extended partition??? But all the normal XP boot files are in sda1. From the liveCd can you still see your XP files?  If XP is really in sda1 then you will have to fix this:
multi(0)disk(0)rdisk(0)[COLOR=Red]partition(2)[/COLOR]\WINDOWS="XP Pro" /fastdetect

It looks like you copied some FAT partitions to sda5 & sda6. But it looks like that is your dos partition as it originally started at sector 63 which would be sda1.
> sda5: _________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
#to make sure you have osprober:
sudo apt-get install os-prober
sudo update-grub

You only have to install grub to the MBR and you will be able to boot and with osprober find all other bootable systems, but if XP is not there, then it will of course not boot that.

If concerned, the above will just install grub2 to the MBR. It is easy to restore a windows boot loader. The boot loader in the MBR for windows is the same for all versions and just looks for the active partition(boot flag) and jumps to that to boot.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You can also restore a windows type bootloader - lilo from the Ubuntu liveCD. It uses the same logic, find boot flagged partition and jump to code in the partition.
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR, not the lilo boot code that goes into the partition as we still want windows code in the partition.

---

### Post by Engineeringtech on 2011-02-23
OLDFRED,

Again, I don't understand a bunch of stuff in your post.  

When I partitioned the drive in preparation for the installations, I set up a 500 MB FAT16 primary partition for DOS (SDA1).  I then created an extended partition which I subdivided for my other OS's.   I made a 100GB FAT32 partition for Windows, a 8 GB FAT32 partition for the Windows Swapfile, a 100GB XT4 partition for Ubuntu (SDA7), a 2GB Linux swap partition, a data partition, and the Mac HFS partition.

Like any dual DOS / Windows install I ever did before, I installed DOS, then Windows.  When you do it this way, the bootfiles for Windows wind up on the primary partition.   I installed DOS to the 500 MB FAT16 partition (SDA1).  Then Windows to the 100GB FAT32 partition. 

If I am reading the result file correctly, it shows Ubuntu on SDA7 where I asked the installer to put it.  It also shows boot files at /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img of the same partition.

But you told me that Grub was not installed?  Where WAS it installed?  

And are you talking about the Grub2 equivalents of "Stage1" and "Stage2"?  When I built the short lived triple booted on the SCSI RAID array (DOS, XP, and Ubuntu 9.04) , the 512 bytes I DD'd to the primary partition and saved as "bootsect.lnx" was, in effect, the "Stage1" file, wasn't it?  Is there no equivalent in Grub2?

---

### Post by oldfred on 2011-02-23
When I say grub is into installed I should have said the grub2 boot loader was not installed to the MBR or the PBR. The grub2 software is installed in the Ubuntu partition.

Windows can only boot thru primary partitions. It would be better to install XP in a primary, but they way you have done it, I guess works. Because the script only looks for boot files, it only sees the XP boot files in sda1, your DOS partition. If you install XP to a primary it can then easily be repaired to directly boot, rather than go thru the dos partition.  Now it is also better to have XP in a NTFS partition. 

Back with 9.10 I originally installed grub2 to the PBR and chainbooted from old grub legacy in the MBR. Boot script shows this, which your does not.
```
    File system:       ext4
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sdc7 and 
                       looks at sector 633297617 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdc and 
                       looks on partition #7 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

```

But grub2 is so good at finding other systems and booting them, that I converted to grub2 and have not looked back.

Install the grub2 boot loader to the MBR and you will see how well it works if the os-prober is installed. If for any reason it does not set it up, I can give you a boot stanza to let it to boot. That assumes it still boots.

---

### Post by Engineeringtech on 2011-02-23
Thank you.  I am still digesting your comments.  Give me a few days.  Been busy at work, and having some health problems.

JC

---

### Post by oldfred on 2011-02-24
It takes less than 5 minutes to boot liveCd and copy & paste grub2 install commands from post above.  If sfter a while using it, you do not like it, then another five minutes to install lilo or boot with windows XP disk and reinstall the windows boot loader.

---

### Post by Engineeringtech on 2011-02-24
[COLOR="Red"]> **oldfred said:**
> Boot script now shows everything like it should. You did not install grub2 to the partition as it would show it.

Your XP says it is in sda2, but that is now your extended partition??? But all the normal XP boot files are in sda1. From the liveCd can you still see your XP files?  If XP is really in sda1 then you will have to fix this:
multi(0)disk(0)rdisk(0)[COLOR=Red]partition(2)[/COLOR]\WINDOWS="XP Pro" /fastdetect

It looks like you copied some FAT partitions to sda5 & sda6. But it looks like that is your dos partition as it originally started at sector 63 which would be sda1.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
#to make sure you have osprober:
sudo apt-get install os-prober
sudo update-grub

You only have to install grub to the MBR and you will be able to boot and with osprober find all other bootable systems, but if XP is not there, then it will of course not boot that.

If concerned, the above will just install grub2 to the MBR. It is easy to restore a windows boot loader. The boot loader in the MBR for windows is the same for all versions and just looks for the active partition(boot flag) and jumps to that to boot.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You can also restore a windows type bootloader - lilo from the Ubuntu liveCD. It uses the same logic, find boot flagged partition and jump to code in the partition.
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR, not the lilo boot code that goes into the partition as we still want windows code in the partition.[/COLOR]

Fred, I'm afraid you really lost me with your post. For instance, I don't know why I should "fix Windows". I've said repeatedly that my DOS and Windows boot just fine from the NTLDR menu.   The Windows installation is in the extended partition, and the boot files are in the primary boot partition where one normally puts them for a Microsoft dual boot.  

I DO NOT undertand your comment about Sector 63. 

You're counting on the code below to install GRUB2 to the MBR, right?

[COLOR="#ff0000"]"sudo mount /dev/sda5 /mnt"
"sudo grub-install --root-directory=/mnt/ /dev/sda"[/COLOR]

And you're counting on OS-prober finding and re-establishing my DOS and Windows boots after I can finally get to the Ubuntu desktop?  I don't have any confidence in that, because OS-Prober ran from the install disk, and didn't find either OS. 

Until I have confidence in what I am doing, I'm not going to make any changes.  

Thanks for being so patient and understanding with me.  Please understand that I have had so much grief with this system, that I just don't want to spend anymore time in front of it, unless to use it for my CAD and engineering work.  I'll let you know what I do.

Jim C.

---

### Post by oldfred on 2011-02-24
I do not think I was saying to fix windows, but if necessary you can easily reinstall the windows boot loader.

The boot script showed that the extended partitions have a mismatch. It may work in your case, but is may be a problem for others or later for you. Generally that is a fixboot command in windows, but windows does not like to be installed in a logical partition, so a fixBoot in windows may not even work. 

Some versions of Ubuntu do not install the osprober. You can easily install it and then it will find your windows. With old grub we often had to create a boot stanza to copy into grub's menu.lst and only have had to do that once or twice and even then once system was updated it found the windows partitions automatically.

os-prober has worked every time for me. And many users posting here have had it work for them. I do not understand your reluctance to try it. I do think because you installed from the text based install CD that it may not have to os-prober installed by default.

I just saw Herman's post #34 in this thread. he had it work with win98.
[http://ubuntuforums.org/showthread.php?t=1585598&page=4](http://ubuntuforums.org/showthread.php?t=1585598&page=4)

---

### Post by Engineeringtech on 2011-02-26
**What a disaster!**  Two years ago when I built my hardware my goal was a RAID 1 array configured to triple boot DOS, XP, and Ubuntu for my engineering work.  I started out trying to do this with a SCSI RAID array (hardware failed days after I installed Ubuntu 9.04).   I ditched the SCSI hardware and tried to do this on the motherboard's Intel ICH10R FakeRAID, with SATA drives.  I was told my motherboard was bad, so I ditched it and got another.  After weeks of trying to get the fakeRAID to work properly, I was told to go back to hardware RAID.  I bought a Highpoint RAID controller.  But the drivers never worked, and Highpoint never responded to my pleas for help.  I wasted months and months trying to get the triple boot to work on RAID.  So I finally decided to relax my expectations, ditch the RAID, and use a single drive.  Surely I could create a triple boot on one drive!   I  pulled the RAID card, sent it back to the distributor, hooked a single drive to the Intel SATA ports, disabled fakeRAID in the BIOS, and partitioned the drive for DOS, Windows, XP, Linuxs and and my DATA.  **I was able to install and configure DOS, and XP and had a WORKING dual boot I when I opened this thread over a week ago.  ****NOW I HAVE NOTHING!**

I tried to add Ubuntu the way I had been taught last year, when I first created the triple boot on the SCSI hardware (DOS, XP & Ubuntu 9.04).   I installed 10.10  to the XT4 partition, (presumably successfully, because there were no error messages.)  Then responding to the installer prompts, I supposedly placed GRUB at the root of the install partition.  (That didn't generate error messages either.)   Finally,, following my written notes, I DD'd the first 512 bytes of the partition (stage 1?) to a file that The Windows NTLDR could use to chainload Ubuntu.    Result?  NOTHING.  Zeroes in the file.  Where is "stage 1"?  No one here would tell me.  I could not chainload Linux.   I reformatted and reinstalled.  Same results.

I was told then that the problem was old RAID "meta data" on the disk.  So I removed that.    Repeated the format and install procedure.  Still nothing in the first 512 bytes of the partition.  Where was GRUB installed?  Per advice here, I ran bootscripts to see what was going on.  OLDFRED and others reviewed the results file and told me GRUB, Linux, and Windows were not where I thought they were.   However, both GPARTED, and my partitioning tools disagreed with the script results.  WHICH AM I SUPPOSED TO BELIEVE?  I was told to ignore the fact that the installer was not finding my other installed OS's and install GRUB to the MBR anyway.   OLD FRED said it would be easy to fix Windows.

Well, I started this thread saying that I did not want to give control of the whole system to GRUB, and I MEANT THAT.  I didn't want to use the GRUB bootloader to load DOS and Windows.  After months and months of time and plenty of $$ I finally had a working DOS and Windows boot.  I didn't want to risk messing up NTLOADER.  No one was interested in helping me get GRUB2 to chainload from  NTLDR, so I had to look for other ideas.

I couldn't help but think the whole problem was related to the use of GRUB2 in Ubuntu 10.10, vs. Grub Legacy in 9.04.  So yesterday I went looking for a new version of of Linux that still installed Grub Legacy.  I downloaded Fedora 14.   So I reformatted my Ubuntu XT4 partition and Linux swap partition (SDA7 and SDA8) to prepare them for Fedora.    I booted the Fedora 14 Live CD, and when I got to the desktop, opened a terminal window.  I ran GPARTED.  There was my DOS primary partition, Windows partition, Windows swap partition, clean XT4 partition (SDA7), Linux Swap partition (SDA8), NTFS data partition, and my small HFS partition.  **Just where I thought they were.  **

I started up the Fedora installer, and I asked it to confirm the partitioning before installing.  Instead of a 100GB XT4 partition and 2GB Linux swap partition at SDA7 and SDA8, it reported a ONE HUNDRED AND SIX GB XT4 partition and a 500MB XT4 partition at SDA10 and SDA9!  No Swap partition.  Well, I thought maybe the installer doesn't count the partitions the same as GPARTED and my partitioning software.  And the option I had selected for the install stated that it would not overwrite my existing VFAT and FAT32 partitions (DOS and Windows).   So I decided to let the installer do it's thing.  I feared that like Ubuntu, the Fedora installer would not detect my other OS's and would overwrite the MBR.  But OLDFRED said it was easy to fix my DOS and Windows boot.  **So I proceeded with the installation, and NOW I have no DOS, XP, OR FEDORA.  My machine boots to a command line, "GRUB".**  

So Linux wizzes...  So someone please tell me now how to get my DOS and Windows boots back.    [B]

There is something drastically wrong with the Ubuntu and Fedora installers if they don't agree with each other, or with GPARTED, about the partitioning map.[/B]   
An OS installer should ASK where it should install, using understandable language, or graphically.  It should ASK where to install a bootloader.  And if it sees Windows partitions it should ALERT the operator that it might write over an existing installation, and an allow an opportunity to abort the installation. 

I'm thorougly disgusted with Linux right now.  Can you blame me?  I've been trying to get this system to triple boot for 3 years.  My CAD software won't run on Linux.   If anyone out there can tell me how to restore my NTLDR dual boot, please tell me.  As for Linux, I'm not sure it will ever work on this system.  Too many bugs! 

JC

---

### Post by oldfred on 2011-02-26
If you installed grub2 and the os-prober you would not be in this situation. I do not understand why you are so anti-grub. Most users here are dual booting with grub2 and have no issues. A few have some issues and we have work arounds for most of them

Now you have added even more complexity with Fedora. I know nothing about Fedora.

If you still want help post a new boot script. It will show what is where if anything is still there. If you have erased things, do not write into the drive. Testdisk can recover it only if the drive has not been overwritten.

Incidentally grub has nothing to do with the ntldr. All grub or grub2 do is pass the boot to the windows partition, just like the windows boot loader in the MBR does. If you had looked at my post #23 you would understand how MBR(msdos) computers boot.

---

### Post by Engineeringtech on 2011-02-27
> **oldfred said:**
> If you installed grub2 and the os-prober you would not be in this situation. I do not understand why you are so anti-grub. Most users here are dual booting with grub2 and have no issues. A few have some issues and we have work arounds for most of them

Now you have added even more complexity with Fedora. I know nothing about Fedora.

If you still want help post a new boot script. It will show what is where if anything is still there. If you have erased things, do not write into the drive. Testdisk can recover it only if the drive has not been overwritten.

Incidentally grub has nothing to do with the ntldr. All grub or grub2 do is pass the boot to the windows partition, just like the windows boot loader in the MBR does. If you had looked at my post #23 you would understand how MBR(msdos) computers boot.


Very easy to blame this on me, a Linux initiate.  A week and a half ago, when I started this soon to be 5 page thread, I had a working dual boot (DOS & Windows) and wanted to know how to chainload Ubuntu from NTLDR.  I had installed 10.10 following a procedure that worked with 9.04 on SCSI hardware.   I repeatedly asked why the procedure, which involves installing Grub at the root of the install partition, rather than the MBR, didn't work for 10.10.  NO ONE answered my question. 

You and others in this support community wanted me to install GRUB to the MBR and possibly risk screwing up my DOS and Windows boot.   You told me that GRUB was wonderful and could handle all my boot requirements.  The installer would detect my DOS and Windows installations.  

However that was untrue.  I ran the 10.10  installer a total of 4 times, and each time on a freshly formatted partition.  Both before and after I successfully removed the RAID meta data that you said was interfering with the installation.  Each time, the installer detected no DOS or Windows installations, and WARNED me about installing to the MBR.   Now when the tools do not support what the experts say, WHOM WOULD YOU BELIEVE?

I discovered on my own, that 10.10 used GRUB2, instead of the Grub Legacy used in 9.04.  So I posed the question ,  "What's different about Grub2 that this established procedure for chainloading Ubuntu off NTLDR, doesn't work?"  And I DIDN'T get an answer.  **You kept telling me to install GRUB to the MBR and if anything happened to my DOS and Windows boot, it was EASY to restore them.**  

So after making no progress in a week and a half, and hearing my questions ignored again and again, I made  a  logical decision.  I went looking for a current version of Linux that used GRUB Legacy.   I installed it, but unfortunately,  just like Ubuntu, it failed to detect my DOS and Windows installations.  It installed GRUB to the MBR, without any warning, without allowing me to cancel the install.   However,  this is what YOU wanted, wasn't it? Grub in the MBR.

So where is Linux?  And where is DOS and Windows?  Am I to conclude that Linux is unable to coexist with two other OS's?   You're telling me it can, but I'm NOT SEEING IT!   Because now I have NO OS WHATSOEVER. 

 It's convenient for you to now say I did not follow your instructions.  But you were not helping me to do what I wanted to do, and your instructions likely would have taken me to the same result.   Were you lying when you said you could easily recover DOS and Windows boots should the writing of GRUB to the MBR overwrite the MBR?  

Finally, you call me "ANTI-GRUB".  Why are you "ANTI-DOS and Windows"?  What have you got against my using NTLDR to boot DOS and Windows?   I TOLD you what I wanted to do on the first page of this post.  (Chainload Ubuntu GRUB off  NTLDR).  I ASKED why 10.10 wasn't installing  the way 9.04 did two years ago.   No answer.   Just the fixation on installing GRUB to the MBR.

No, I am NOT "ANTI-GRUB".  But I also didn't start this thread as an academic exercise.  I started this thread so I could add Linux to my system, and USE IT in my work.   If this is what the Ubuntu community has to offer a first time user, then I'm not sure I want any part of it.

JC

P.S.  I went into this with an open mind.  I thanked you for every single post you made. Tried most of your suggestions.  I had every hope that you would eventually get my system working.  However, your insistence on taking me down a path I was didn't want to go, would worry anyone.  Again, you said you knew how to fix this!

---

### Post by oldfred on 2011-02-27
If you just installed grub2 to the MBR you would be booting everything days ago.

You can boot Ubuntu with grub legacy. But you have to do everything manually where grub2 automates it.

You also have a very non-standard install of windows. Windows is intended to be installed to a primary partition and works best from that. Yes, your boot DOS and use it to boot your windows will work and yes you can use old grub to boot. But you are making life difficult when it does not have to be. You installed the version of Ubuntu for more advanced users and wondered why it does not have the os-prober. It is easy to install.

When grub2 first came out many resisted it, including me. Since then I am a convert and it has been greatly improved.

Right now I am in Natty and do not have my links to my data set up. But will post some old info on converting back to grub legacy in a few minutes.

---

### Post by oldfred on 2011-02-27
You have to chroot into your install and completely uninstall both grub & grub2 (grub-pc) then just reinstall grub (grub legacy). if you reinstall the bootloader portion to your partition I think you may get what you want.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by Engineeringtech on 2011-02-27
> **oldfred said:**
> If you just installed grub2 to the MBR you would be booting everything days ago.  

You can boot Ubuntu with grub legacy. But you have to do everything manually where grub2 automates it.

You also have a very non-standard install of windows. Windows is intended to be installed to a primary partition and works best from that. Yes, your boot DOS and use it to boot your windows will work and yes you can use old grub to boot. But you are making life difficult when it does not have to be. You installed the version of Ubuntu for more advanced users and wondered why it does not have the os-prober. It is easy to install.

When grub2 first came out many resisted it, including me. Since then I am a convert and it has been greatly improved.

Right now I am in Natty and do not have my links to my data set up. But will post some old info on converting back to grub legacy in a few minutes.


Sorry, but that's a big assumption!  If I had let the Ubuntu installer place GRUB in the MRB days ago, It's a good bet I'd be right where I am now.    GRUB is GRUB whether it is in Fedora or Ubuntu or Redhat, isn't it?  

I setup my DOS and Windows dual boot the only good way I know how to do  it.  Virtual DOS doesn't handle hardware and peripherals well.  And  running DOS programs from within Windows doesn't work the same either.

I never told you, but I DID begin with a standard Ubuntu install disk.  It didn't detect my hard drive, so I switched to the alternate install disk because it DID detect my drive. 

Furthermore, I researched this, and I knew the alternate installer  would allow me to place GRUB anywhere where I wanted.   I WOULD"VE allowed GRUB to do it's thing in the MBR, if OS-PROBER had found my other OS's.   OS-PROBER DID run from the alternate install CD, but it DID NOT find my other OS's!   And as a result, the installer  WARNED ME about installing to the MBR.  If I have a "resistance" to Grub2, that's why!  The installer SUGGESTED sample alternate paths to install grub, and I picked the root  of the Linux install directory, as everyone suggests you chainload GRUB from the NT bootloader.    But there was never anything in the first 512 bytes of the install partition for NTLDR to work with.

My first priority with this system is to get back to where I was, not spend the next two weeks trying to get Ubuntu (or Fedora) to work.  So if you were being truthful when you said I could get my DOS and Windows boot back, then please tell me how. 

Sorry if I don't sound appreciative of your efforts, but the fact is this has been a disaster for me.  If I had to do it all over, I would never have picked up a linux disk or come to this forum.

---

### Post by Engineeringtech on 2011-02-27
> **oldfred said:**
> You have to chroot into your install and completely uninstall both grub & grub2 (grub-pc) then just reinstall grub (grub legacy). if you reinstall the bootloader portion to your partition I think you may get what you want.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)


Does any  of this fix my DOS, Windows boot?  If so, would you elaborate further before I go following other threads? I have no idea what CHROOT is.

I shouldn't have BOTH GRUB legacy and GRUB2 in the MBR.  Probably just GRUB legacy.  I never directed either Ubuntu or Fedora to install to the MBR, but Fedora did it anyway, and Fedora supposedly uses GRUB Legacy.

---

### Post by oldfred on 2011-02-27
I thought all the other Linux gave you a choice on where to install grub. But I have not installed them (yet).

Ubuntu only gives you a choice on where to install if you do manual partitioning and it installs grub2 by default. 

Chroot is using the kernel from the liveCD and CHanging ROOT to use the rest of the system from your install that does not boot. You then can do just about anything to update your system that way. If you prefer and do not have much configured and have saved your data, a new install would be quicker but I do not think there is a way to install old grub from the new install anyway. The actual quickest way would be to use the liveCD version, let it install grub2 to MBR, then after booting uninstall grub2 and install grub to your partition. You then install lilo as below to boot your windows.

What is your windows problem. I thought you just could not see it from the os-prober that you did not have.

If you want to test that your windows still boots.

Restore basic windows boot loader - universe enabled
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```May show error messages about the rest of lilo missing, ignore, we just want MBR

Lilo is an old boot loader that has its own boot code (which we so not want). But lilo works just like windows from the MBR. It looks for the partition with the boot flag (active partition in windows) and jumps to that partition to boot. This is exactly like the windows boot loader, but lilo will also jump to a logical partition where windows will not. You can then try with the boot flag on your DOS partition or even try putting your boot flag on the windows boot partition sda5.

To set boot flag you can use gparted, Disk Utility or command line. In gparted click on partition, right click on partition flags and set boot flag.

set boot flag on for sda[COLOR=Red]1[/COLOR] (off on others)
```
sudo sfdisk -A1 /dev/sda


```Change to 5 if you want to try directly booting windows. 

Use this to see if flag is set and which partition is which in case you have moved things.
```
sudo fdisk -lu
```

---

### Post by Engineeringtech on 2011-02-28
OLDFRED--

Thank you.  I'm afraid you've lost me with most of this.  I need time to digest this.  I'm dealing with some difficult health problems that the doctors haven't been able to diagnose or treat, and that means I am not always able to sit at a computer.  So if you would, please give me a while.

JC

---

### Post by Engineeringtech on 2011-03-09
Oldfred,

Have you still got your ears on?  Or did I wear you out with all my questions? 

I figured out how to fix my DOS and XP dual boot with my Windows installer CD.  I was very relieved to get DOS and Windows back, but still wanting a working Linux install.

Since I now had Fedora 14 on my drive, I went over to their forum to see if they could help me get it to boot.  They directed me to re-install Grub Legacy from the Fedora Live CD.   I tried two different methods they suggested.  Neither one worked.  Then they asked me to see if I could boot Fedora using SuperGrub.  Not only did SuperGrub fail to boot the Fedora installation, it wouldn't boot my DOS or Window installations.  I tried to re-install Grub, using the SuperGrub tools, but that didn't work either.

So to recap, my DOS and Windows installations still boot and run perfectly. I've put clean installations of Ubuntu 10.10 and Fedora 14 on the drive, and neither release detected my DOS or Windows OS's.  Neither booted when I placed Grub2 or Grub Legacy on the MBR .  So what next??

I decided to reformat the Linux partition and reinstall Ubuntu 10.10, again from the alternate install CD.  Only this time, I'd skip the Grub2 installation.  I'd use my Ubuntu 9.04 Live CD, to install Grub Legacy in the root of the install partition, and try to chainload it from NTLDR.    After all, you said Ubuntu 10.10 would boot from  Grub Legacy, didn't you?  And last year I'd successfully chainloaded Ubuntu 9.04 from NTLDR, before my old SCSI hardware failed.

So I did this and then used the "DD command to create "bootsect.lnx". (Which would allow me to chainload linux from the NTLDR.)   For the first time in weeks, this file is non-zero. (The file was always empty when I installed Grub2.)  Now when I try to boot into Linux, I get a "GRUB>" prompt.

I am having a tough time believing the Linux community cannot come up with a solution to this.  I have a single Western Digital 500 MB hard drive, connected to a SATA port.   The drive has been partitioned correctly, and stripped of the RAID meta data that used to be on it.  The DOS and Windows boot is done correctly, and works reliably.  

Any ideas?  Please don't tell me to install Grub2 to the MBR, or to reinstall Ubuntu.  If I reformat and reinstall Ubuntu any more, I am likely to wear out the drive.  And putting GRUB in the MBR has accomplished nothing.  

JC

---

### Post by oldfred on 2011-03-10
Grub legacy is still part of Ubuntu, but I do not know how to install it from the installer.

I thought I had posted this before:
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

You would have to chroot into your install and remove grub & grub2 (grub-pc)and install just grub adn grub common.

You can use drs305's instructions, but reinstall grub not grub-pc.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)
kansasnoob- full chroot one line version with &&----
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Old grub was very poor at finding other installs. Grub2's osprober, if installed is excellant at finding other installs. You may have to manually add boot stanza's  to grub's menu.lst for your DOS & windows. Grub legacy also does not complain about being installed to the Ubuntu root partition so you can chainload to it. With 9.04 and before I used old grub and chainloading all the time. I still have my grub only boot partition to chainload other installs, but I think everything is now obsolete in that partition as I have reinstalled just about everything since and let grub2 find all my installs.

---

### Post by Engineeringtech on 2011-03-10
Thank you.  But let me clarify something again.  OS-Prober ran from both the Ubuntu Alternate Install disk and the Fedora install disk, and never found my other OS's.  And Grub2 refused to boot Ubuntu or Fedora for me, even when it was placed in the MBR.  

So I haven't seen the wonders of grub!

---

### Post by oldfred on 2011-03-10
With os-prober installed with grub2:

```
fred@fred-LT-A105:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-27-generic
Found initrd image: /boot/initrd.img-2.6.35-27-generic
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows XP Media Center Edition on /dev/sda1
done
fred@fred-LT-A105:~$ 

```

With grub legacy I have had to post many boot stanza and have a long list in my files. We have posted a few boot stanzas with grub2 but many times after some updates it starts working and they did not need boot stanza.

---

### Post by Engineeringtech on 2011-03-11
Oldfred,
I appreciate your efforts, but I've been trying to get Ubuntu to boot on my machine for over three weeks. Rather than expound on how wonderful Grub and Os-prober are, why don't you focus your attention on getting my system working so we we can both quit this thread and move onto other things?  Please don't tell me the solution involves junking DOS, Windows and NTLDR. Because at this point those are the only things that HAVE worked for me.  

You've told me several times I need to uninstall both Grub2 and Grub Legacy and reinstall one of them.  Now I don't know why that would do anything, because I have installed and reinstalled Ubuntu 10.10 and Fedora 14 many times on clean partitions. One uses Grub2 and the other Grub Legacy.  I've let Grub2 and then Grub Legacy go exactly where the installer wanted to put it (MBR), and it still didn't result in a boot screen that would get me into Linux. The best I have managed is a "GRUB>" prompt.

But let's assume the installer have not done the OS-prober and Grub installations correctly, and I need to uninstall and reinstall Grub2 (or Grub Legacy) manually.   I will try to get that done soon.  I can't print from this old, overheating laptop, and have no wireless or wired internet access in the room where the target machine is.  So I'll have to wait till I can get to work to print the instructions.   I still work a 40 hour week and dealing with health problems.  Plus we've had much flooding here in NY last week and over the past two days.  Last night I spent 8 straight hours on the pumps, or lugging and dumping buckets of water. So please give me time to digest your posts.  

I am on serious burnout here and am reaching the point where I want to toss my expensive hardware off the roof, and kiss off computers for good.

---

### Post by Engineeringtech on 2011-03-12
This is crazy!  Why should uninstalling Grub Legacy and manually reinstalling Grub2 fix the boot problem?  Are you implying that the installer never placed GRUB 2 on the right partition? And if so, why did the Fedora installer (which uses Grub Legacy) fail in the exact same way?  (failing to detect my other OS's, and failing to boot)    Can't I boot up the live CD and look for the Grub files?   What should I look for?  
   
Maybe I followed the wrong links, but the threads I found directed me in uninstalling Grub2, not Grub legacy. 

While we're on the subject, exactly what does an uninstall do? Are certain files and folders  deleted? If that is the case, don't I have to tell it where to find the files and folders that are to be removed?    Does an uninstall rip "grub" out of a Linux equivalent of the Windows  registry?  Or is just that first 512 bytes of the partition removed? 

What does a Grub installation do? Does it place the Grub folder and files  I saw in the the partition, or are theyt always there following the installation of the OS?  How would I know if I had a properly configured Grub installation?  

How does the Linux system start up?  Is the Kernel "executed"?  Does Grub find  the "kernel" and create a link to it?  Is that what "stage 1" is?

Isn't there a way for me to manually start up my installation from the "GRUB>" prompt I'm seeing when I try to startup?  SuperGrub wasn't able to boot the installation.   It reported that "fstab" was missing.  What's that about?

Too many unanswered questions, and too much groping around blindly.  This is not like any troubleshooting I have done in Windows or DOS. Very frustrating after 3 1/2 weeks of this.

---

### Post by oldfred on 2011-03-12
I said, follow the instructions for uninstalling both grub & grub2 and reinstall grub. You need to uninstall both to make it work correctly.

Old grub often did not find other installs, so that Fedora's old grub did not work is normal. We often even with windows had to give users menu.lst entries.

That you installed with the alternative installer, which then I assume does not have the osprober, it also makes sense that a grub update would not find your other systems.

A uninstall removes the files. You still have to overwrite the MBR with what ever boot loader you want. 

If you are missing fstab you do not have a good install. In your case it would be a lot quick to just download a good liveCD version, burn at slowest speed to a CD and reinstall. If you use manual install you can choose to reuse the partitions you now have. Check reformat box and it housecleans and restalls a new clean copy.

 GRUB 2  has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

The install works a lot better if you have a wired connection for the install. It need to find drivers that may not be on the liveCD and download them. If you do not have Internet and install you need to have a plain vanilla system. Otherwise it is more difficult to add drivers.

---

### Post by Engineeringtech on 2011-03-13
Fred,

> **oldfred said:**
> I said, follow the instructions for uninstalling both grub & grub2 and reinstall grub. You need to uninstall both to make it work correctly.  [COLOR=Red]An where exactly is the link for doing that?  The only link I found from you, directs me in the  removal and re-installation of Grub 2.[/COLOR]

Old grub often did not find other installs, so that Fedora's old grub did not work is normal. We often even with windows had to give users menu.lst entries.  [COLOR=Red]NEW GRUB (Ubuntu 10.10 installer) failed THREE TIMES before I even tried OLD Grub (Fedora installer).[/COLOR]

That you installed with the alternative installer, which then I assume does not have the osprober, it also makes sense that a grub update would not find your other systems. [COLOR=Red]YOU'RE ASSUMING WRONG!  As I have told you repeatedly.. OS-Prober ran from the alternate install CD  on three separate occasions, and found NOTHING. [/COLOR]

A uninstall removes the files. You still have to overwrite the MBR with what ever boot loader you want. 

If you are missing fstab you do not have a good install. [COLOR=#000000]AND WHY NOT?  I ran the installation four times without any error messages.  I also booted to a 10.04 Live CD and tried to install from it.  (IT didn't find the windows installations either.)[/COLOR] In your case it would be a lot quicker to just download a good liveCD version, burn at slowest speed to a CD and reinstall. [COLOR=#000000][COLOR=Red]THERE'S NOTHING WRONG WITH THE INSTALLERS I BURNED[/COLOR].[/COLOR] If you use manual install you can choose to reuse the partitions you now have. Check reformat box and it housecleans and restalls a new clean copy. [COLOR=#000000]I'm tired of doing reformats and re-installs.  All I'm doing is wearing out my previously new hard drive.[/COLOR]

 GRUB 2  has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

[COLOR=Red]Pretty sure I never found this file structure after ANY of my installs.  I did find a GRUB folder under /boot.  What is that? [/COLOR]

The install works a lot better if you have a wired connection for the install. [COLOR=#000000]I never got any error messages about missing drivers.  During the install, I bypassed the network configuration because I have no wired connection to the internet, and no chance whatsoever of getting one in the room.[/COLOR]It need to find drivers that may not be on the liveCD and download them. If you do not have Internet and install you need to have a plain vanilla system. [COLOR=Red]How "plain vanilla" does it have to be?  I have a hard drive a DVD writer and what was, (two years ago), a popular P45 motherboard.[/COLOR]Otherwise it is more difficult to add drivers.

---

### Post by oldfred on 2011-03-13
Post #41 except as I said reinstall grub not grub-pc. But you have to do this while on line  or it will uninstall grub and then not install anything. Then you will have to install from CD.

Package names do not always match names we use.
grub-common is for both grub & grub2
grub-pc is grub2
grub is grub

link said this:
[COLOR=DarkRed]apt-get install grub-common grub-pc[/COLOR]
I said do this instead:
[COLOR=DarkRed]apt-get install grub-common grub

[COLOR=Black]Do you have any Linux installed, if so post this.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

[/COLOR] 
[/COLOR]

---

### Post by Engineeringtech on 2011-03-14
> **oldfred said:**
> Post #41 except as I said reinstall grub not grub-pc. But you have to do this while on line  or it will uninstall grub and then not install anything. Then you will have to install from CD.

Package names do not always match names we use.
grub-common is for both grub & grub2
grub-pc is grub2
grub is grub

link said this:
[COLOR=DarkRed]apt-get install grub-common grub-pc[/COLOR]
I said do this instead:
[COLOR=DarkRed]apt-get install grub-common grub

[COLOR=Black]Do you have any Linux installed, if so post this.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

[/COLOR] 
[/COLOR]

[COLOR="Blue"]I'm afraid you lost me again Oldfred. And post #41 didn't help either. I have to do the uninstall while online?  I can't get a hardwired internet connection to the target machine.  And I'm sure if I can't figure out the installation, I can't figure out how to configure a wireless connection complete with special drivers, from a terminal window.

I haven't had a chance to re-run the bootscript, but I will.  

Last night before I read this, I ran an experiment of my own.  I booted from the alternate install cd and selected "repair" to see what I could accomplish.  Somehow I wound up being asked where I wanted to install, and whether I wanted to reformat.  The hell with it.... I reformatted and reinstalled just as I have done five times before.  As before OS Prober failed to find my other OS's.  Preferring not to screw up my DOS and Windows boot again, I deferred from installing Grub in the MBR.  However, instead of installing to the root of the install partition (/dev/sda9), I put a blank floppy in the drive and entered /dev/fd0 for the install path.  Got an immediate error message. Something about a missing file.  Menu.lst or Fstab  (I can't remember.)  Does this tell you anything? (I've never had any error messages in the Grub installation.)

I hit "esc" to get out of the error message, and traveled backwards in the Grub install routine. I tried to install "grub" again. This time it SPECIFICALLY told me it was NOW going to try to install GRUB2, and that GRUB2 might not work! I thought you told me Ubuntu 10.10 always installs Grub Legacy as the default.  Have I been installing Grub Legacy all this time?  

I proceeded with the Grub2 install, and tried to put it on the floppy.  This failed with the same error message.

Has this Alternate Install CD ever worked for anyone?  I only started using it, because the standard install CD didn't recognize my hard drive. [/COLOR]

---

### Post by Hedgehog1 on 2011-03-15
**Engineeringtech**, **oldfred**,

You know when you are driving by an accident site on the highway?  You don't really want to look, but your curiosity just gets the better of you and you have to look?  Following this thread has been a very similar experience for me.  My curiosity just gets the better of me and have to read the next post.

What unpredictable thing will **Engineeringtech** do this time instead of following the simple and sage advice offered by **oldfred**?

Each time I think I have a top ten list made up, and then **Engineeringtech** offers up a new action, and my list is upset again.

Loading grub on a non-bootable floppy was not something I could ever have predicted.  **Engineeringtech**, my hat (well, baseball cap) is off to you on your plot twist.  Bravo!

But I am most impressed with **oldfred**'s ongoing patience.  You, sir, have the patience of Job (this assumes Job had internet access).

I will continue to watch for the next posts; someday, I hope to see **Engineeringtech** either follow **oldfred's** kindly given instructions **OR** stop and ask **oldfred**: Is there a better way to run three (or more) OSs on my box without triple booting?  

Of course, that would change the course of the posts from angry (but awesome) quotes like: [COLOR="RoyalBlue"]'Has this Alternate Install CD ever worked for anyone?'[/COLOR] *(you have found our secret! We all really use Win7 and lie about running Ubuntu!)* to more reasonable inquires like: [COLOR="RoyalBlue"]'How do folks on the forum run multiple OS's, all at the same time, and not need to reboot to do it?'[/COLOR]

But then, like the ending of the movie '**The Truman Show**', I would be forced to find a new channel to watch.  However, if the trade is that **Engineeringtech** would become a 'Brother Ubuntian', it is a sacrifice I am very willing to make.


***The 'Very Entertained' Hedge***

:KS

---

### Post by oldfred on 2011-03-15
Ubuntu 9.04 was the last to install grub legacy (0.97) by default. But Ubuntu still includes grub and and some users who have upgraded from 8.04 or done multiple upgrades may still have it.

It would have helped to know you did not have Internet access. Updates, reinstall and many of our standard processes assume Internet. You can set Cd as source in System, Administration, Update Manager - software sources. 

I have not maintained a off-line system but some have recommended:
aptoncd 
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)

Users often use the Alternate install when they have video issues, RAID or other server based installs. It does not install quite the same default packages, but again assumes you will update from the Internet the added packages you want.

Can you run a LiveCD? If not there is no way to repair your system.

I have not used Supergrub for a while but they have updated to have versions for grub, grub2 & a system rescue version. I would try one of them.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

---

### Post by Hakunka-Matata on 2011-03-15
RE: post #54 --->  **Bravo**  Bold.

---

### Post by Engineeringtech on 2011-03-15
Hedgehog,

Now nice! You've kept quiet all this time, reading my posts while I've followed Oldfred's suggestions, which unfortunately, haven't been successful.  And you have nothing to offer until now, when you redicule me for taking some initiative by trying somethings myself!  Is that how you help Linux novices?  If you'd paid close attention to my posts, you'd see that I HAVE tried MOST of Oldfred's suggestions.  (At least the steps I understand....  )

Now I DID ask Oldfred to honor my request to let me chainload Grub from the NTLDR.   I had reasons to ask that.  One being that installing Grub or Grub2 to the MBR HASN'T resulted in a bootable system.  But ultimately, this computer is for ME, not Oldfred, and not YOU.   If Ubuntu hasn't the flexibility to do what I was told it could do, then maybe you and everyone else here should have just told me that from the start.

Have I been unappreciative of Oldfred's efforts? NO!  I also realize he volunteers his time.   Perhaps I vented some of my frustration.  Remember, it has been 4 weeks, and I still haven't seen Linux run outside of the Live CD.   I can't blame Oldfred for that though.  The problem is this thread is so lengthy and involved.  Who can follow it?

YES, I asked, "Has this 10.10 alternate install CD worked for anyone?  Maybe that was a bad choice of words.  But I didn't say that to pan the Ubuntu community.  I was sincerely asking the question, "Does the 10.10 Alternate Install CD work?"   For all I know, no one uses it.   Now as I said before, I started with the standard installer, and it didn't even detect my drives, so I moved to the alternate install CD. 

Hedgehog, if you have something positive to offer towards getting this to work, then you should have just offered it.

---

### Post by Engineeringtech on 2011-03-15
Oldfred,

It seems from recent comments by others, that I've overstayed my welcome here.   Sorry if I was a bad student or showed you any sign of disrespect.  It may not seem like it, but I did appreciate your attempts to help me.  I just haven't had the success I hoped to have, and I'm very frustrated by that. 

So I think I'll just call it quits, at least as far as this thread goes.  Maybe I'll figure this out myself eventually, or I'll just use DOS and XP and forget about Linux. 

Should I find a solution, I'll try to let you know, so at least you get some closure on all your efforts.

Thank you, and bye!

Jim C.

P.S.   Just for the record, I transitioned from the LiveCD installer to the Alternate Install CD when I was trying to get Ubuntu to work on the FakeRAID setup.   The LiveCD wouldn't didn't detect the RAID array, and even after I ditched the array, and deleted the RAID Meta Data, the LiveCD didn't detect my drive.  It was only much later, after I booted with the Fedora LiveCD and reformatted the partitions, that the Ubuntu LiveCD started seeing my hard drive.   So maybe I have to spend more time with the Ubuntu  Live CD.

---

### Post by Hedgehog1 on 2011-03-15
> **Engineeringtech said:**
> 
Thank you, and bye!

Jim C.


Jim,

I don't want you to leave.  I do want to be open to alternate solutions to getting what you need out of your computer.

There are ways to run an unlimited number of operating systems on your PC.  You can do this with a Windows host, or a Linux disto as a host.

**Oldfred** has tried very hard to help you do it the hard way you are absolutely set on doing.  If you look at the views of this thread (it is a little over 1,600 views as I type this) you can see others stopped posting and just watched.  **Olfred** kept soldering on (he is a great guy - PLEASE don't stop talking to him because of me!).

If you are willing to be calm, and be open to new ideas, you could be running DOS, multiple Windows versions, multiple Linux distros and even OSX as virtual machines, all with a single host OS and no dual booting required.

If you are game to play fair, so am I.  It is **YOUR** PC.  It is also **YOUR CHOICE** if you want your PC to **LIMP** along, or to **DANCE**

***The Hedge***

:KS

---

### Post by Hakunka-Matata on 2011-03-16
Once again I second Hedgehog1, as I did in post #56.  @Engineeringtech: I believe Hedgehog1 speaks for us all when he says, "I don't want you to leave".  We all want to see you succeed.  My reason for seconding post #54 was to show respect and support for the indefatigable oldfred, it was not to belittle you.  Although I might add it would be nice to see a little more respect for those that freely offer help.  We all make mistakes from time to time.  One of my recurring mistakes is not having learned yet to keep my own mouth SHUT.

Hang in there, and get that system ready to 'SHIP'

---

### Post by oldfred on 2011-03-16
We have had a lot of users who for whatever reason have RAID metadata on their drive which then causes the liveCd to not work as it does not include the RAID drivers. The alternate installer often then works since it has the extra drivers.

IF you have the liveCD working, you need to do a full standared install from that, then if you have problems post a new copy of the boot info script as that gives us many clues about why things are not working. 

The other issue many are having including me, is video issues. If only one system it may seem like a boot issue, but it has booted and then found video issue and stopped. I have to add a nomodeset parameter to get it to boot. LiveCD works (now) older versions need parameter even for liveCD. But first boot needs special settings.

---

### Post by Engineeringtech on 2011-06-02
Oldfred,
 
I promised you I would report back if I ever got my system working. I did, just 20 minutes ago. Unfortunately, I can't tell you exactly what the fix was. I worked for a while with the people at LinuxQuestions.org. Tried some ideas of my own. You can read my last post there if you're interested. Maybe you will figure it out.  I want to thank you and the other people here who tried to help me. I'm sorry I wasn't a better student. But I had a long drawn out and painful history with this computer.
 
 
My last post at the other forum:
[http://www.linuxquestions.org/questions/linux-newbie-8/26-months-trying-to-get-triple-boot-to-work-linux-remains-the-holdout-875266/](http://www.linuxquestions.org/questions/linux-newbie-8/26-months-trying-to-get-triple-boot-to-work-linux-remains-the-holdout-875266/)
 
 
 
 
6/10  I allowed Ubuntu to do a simple security update, and now my desktop no longer boots Ubuntu, Windows or DOS.  No boot menu.   Tried to reinstall Grub from a LiveCD mount, and it doesn't detect any of my installations.  That's it for me.  I invested a massive amount of time in this system, and have concluded that Ubuntu just won't run on some hardware.

---

