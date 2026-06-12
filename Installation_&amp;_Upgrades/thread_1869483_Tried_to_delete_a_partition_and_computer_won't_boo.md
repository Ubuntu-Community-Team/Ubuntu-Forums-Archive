---
title: "Tried to delete a partition and computer won't boot"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by Lennatron on 2011-10-25
Hi all,

I had Ubuntu 10.10 installed and I decided to remove and install a different version because it would freeze a lot. I have Windows 7 on my computer also by the way. So I went into Windows 7 and downloaded a partition manager and I deleted a 58GB NTFS file system partition because I thought it was Ubuntu 10.10. So it removed and I restarted my computer. The computer came back on and it says error: File system not found (Or something to that effect)

Under that it says Grub rescue and a flashing white line to enter commands. It shows this right after the Dell logo comes up and no boot menu shows like it use to.

Is there anything I can do to boot into Windows again?

Thanks in advance,
Lenny

---

### Post by critin on 2011-10-25
Run the Dell rescue disk or restore partition if you still have one.  Mine (HP)  shows in the bio screen when it starts up.  Grub was deleted or corrupted when the partition was deleted.  

I don't have Windows7, but my XP has a disk manager that does all that stuff.

Will the downloaded partition manager show you the disk as it is now, like in GParted?  Can you still see the windows partition?  You may have to reinstall windows unless the partition can be undeleted or restored.  There are programs to rescue partitions but I'm not familiar with them.  Sounds like you deleted windows.

Edit:  Don't run or restore windows until you find out if it can be restored or all your personal programs/files will be lost.  Until you find for sure that windows was indeed deleted.

---

### Post by Lennatron on 2011-10-26
> **critin said:**
> Run the Dell rescue disk or restore partition if you still have one.  Mine (HP)  shows in the bio screen when it starts up.  Grub was deleted or corrupted when the partition was deleted.  

I don't have Windows7, but my XP has a disk manager that does all that stuff.

Will the downloaded partition manager show you the disk as it is now, like in GParted?  Can you still see the windows partition?  You may have to reinstall windows unless the partition can be undeleted or restored.  There are programs to rescue partitions but I'm not familiar with them.  Sounds like you deleted windows.

Edit:  Don't run or restore windows until you find out if it can be restored or all your personal programs/files will be lost.  Until you find for sure that windows was indeed deleted.

I can't use the partition manager I downloaded because I can't see the Windows partition. No boot menu shows up.

Is the Dell Rescue disc an actual disk that you insert into your computer? I have a lot of Dell discs.

I don't think I deleted Windows because I have a 500GB hard drive and I allowed Ubuntu to use about 40 or 60GB of it and the partition I deleted was 58GB. Windows was the OS on the computer when I bought it and I later installed Ubuntu 10.10 onto the computer alongside Windows.

---

### Post by nothingspecial on 2011-10-26
Ubuntu will not have been on an ntfs partition.

But windows may have been.

Follow the instructions here

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Paste the results in a new post back here.

---

### Post by critin on 2011-10-26
> **nothingspecial said:**
> Ubuntu will not have been on an ntfs partition.

But windows may have been.

Follow the instructions here

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Paste the results in a new post back here.


nothingspecial, can this script be installed into a live cd/flash and used from there, such as boot-repair can?  The poster cannot boot.
Thanks,

---

### Post by T0NYisME on 2011-10-26
I actually done the same thing that you've done and got the same outcome, I was also dual booting with win7-which is why I now take GREAT care when messing with partitions. Anyway what worked for me was to insert the ubuntu live cd and it restored the missing files for me. I'll try and find the link for you that I used to do it..

---

### Post by Mark Phelps on 2011-10-26
Win7 already HAS a partition manager -- known as the Disk Management utility.  What did you download and install to use, instead?

If you installed Win7 yourself on your 500GB drive, and you set the partition to around 60GB when you installed it -- it's likely you DID erase the Win7 OS partition.

If you run any kind of Dell restore program, it's likely to either erase your entire drive and reinstall Win7 from scratch, or fail because it finds other partitions on the drive that it does not understand.

And, while there is a Boot Repair CD image out there you can download, it won't do you any real good if you actually erased your Win7 OS partition.

---

### Post by nothingspecial on 2011-10-27
> **critin said:**
> nothingspecial, can this script be installed into a live cd/flash and used from there, such as boot-repair can?  The poster cannot boot.
Thanks,

Yep.

---

### Post by Lennatron on 2011-10-29
I have the results of the Boot Info Script. I attached it to this post. and pasted them below:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 32776 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    30,800,324    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3          30,800,325   849,480,432   818,680,108   7 NTFS / exFAT / HPFS
/dev/sda4         968,719,500   976,771,071     8,051,572   f W95 Extended (LBA)
/dev/sda5         968,720,384   976,771,071     8,050,688  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8015 MB, 8015282176 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15654848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    15,647,309    15,647,247   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        CEE854D4E854BD01                       ntfs       RECOVERY
/dev/sda3        A8AC56EFAC56B810                       ntfs       OS
/dev/sda5        806216f8-a880-4493-902b-cbf37185e4c7   swap       
/dev/sdb1        4E36-0B93                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  36 ff ff ff 89 5c 24 14  39 5c 24 28 0f 86 aa 00  |6....\$.9\$(....|
00000010  00 00 89 5c 24 24 38 5c  24 13 74 05 53 8b cf eb  |...\$$8\$.t.S...|
00000020  62 89 5c 24 20 89 5c 24  1c 39 5c 24 18 76 46 8b  |b.\$ .\$.9\$.vF.|
00000030  7c 24 24 8b 46 10 8b 04  07 8b 40 04 6a 0c 8d 4c  ||$$.F.....@.j..L|
00000040  24 50 51 50 ff 15 d0 1c  00 10 3b c3 0f 84 e8 fe  |$PQP......;.....|
00000050  ff ff 8b 44 24 58 39 44  24 20 7d 04 89 44 24 20  |...D$X9D$ }..D$ |
00000060  ff 44 24 1c 8b 44 24 1c  83 c7 04 3b 44 24 18 72  |.D$..D$....;D$.r|
00000070  c2 8b 7c 24 30 8b 44 24  20 3b 44 24 48 8b cf 7f  |..|$0.D$ ;D$H...|
00000080  0e 6a 01 ff 74 24 18 56  e8 1c fe ff ff eb 10 53  |.j..t$.V.......S|
00000090  ff 74 24 18 56 e8 0f fe  ff ff c6 44 24 13 01 8b  |.t$.V......D$...|
000000a0  44 24 18 ff 44 24 14 c1  e0 02 01 44 24 24 8b 44  |D$..D$.....D$$.D|
000000b0  24 14 3b 44 24 28 0f 82  5a ff ff ff 88 5c 24 68  |$.;D$(..Z....\$h|
000000c0  8b 74 24 34 3b f3 74 05  e8 cf fd f7 ff 83 4c 24  |.t$4;.t.......L$|
000000d0  68 ff 8b 74 24 2c 3b f3  74 05 e8 bd fd f7 ff 8b  |h..t$,;.t.......|
000000e0  4c 24 60 64 89 0d 00 00  00 00 59 5f 5e 5b 8b e5  |L$`d......Y_^[..|
000000f0  5d c2 04 00 cc cc cc cc  cc 6a 10 b8 ba 1c 21 10  |]........j....!.|
00000100  e8 52 a5 10 00 8b 55 0c  33 db 3b d3 75 0a b8 03  |.R....U.3.;.u...|
00000110  40 00 80 e9 a8 00 00 00  8b 4d 10 3b cb 74 ef 8b  |@........M.;.t..|
00000120  45 1c 3b c3 74 e8 89 5d  fc 8b 35 54 1d 00 10 3b  |E.;.t..]..5T...;|
00000130  0e 0f 85 84 00 00 00 89  5d 10 c6 45 fc 01 8d 78  |........]..E...x|
00000140  0c e8 5c 00 fb ff 8b f0  85 f6 74 1f 8b 06 8b ce  |..\.......t.....|
00000150  ff 90 84 00 00 00 8b 0d  74 1a 00 10 ff 31 8b 10  |........t....1..|
00000160  8b c8 ff 52 1c 84 c0 74  11 8b de 85 db 75 0f 68  |...R...t.....u.h|
00000170  ff ff 00 80 ff 15 a4 1e  00 10 8b d6 eb c3 53 e8  |..............S.|
00000180  d9 fb ff ff 8b 4d 0c 57  e8 5a fd ff ff c6 45 fc  |.....M.W.Z....E.|
00000190  00 8b 75 10 85 f6 74 05  e8 ff fc f7 ff 33 c0 eb  |..u...t......3..|
000001a0  1f 8b 45 e8 8d 4d e4 89  45 0c ff 15 a0 1e 00 10  |..E..M..E.......|
000001b0  b8 b6 9b 0f 10 c3 8b 45  0c eb 05 b8 01 40 00 fe  |.......E.....@..|
000001c0  ff ff 82 fe ff ff 74 03  00 00 00 d8 7a 00 00 00  |......t.....z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by Lennatron on 2011-10-29
> **Mark Phelps said:**
> Win7 already HAS a partition manager -- known as the Disk Management utility.  What did you download and install to use, instead?

If you installed Win7 yourself on your 500GB drive, and you set the partition to around 60GB when you installed it -- it's likely you DID erase the Win7 OS partition.

If you run any kind of Dell restore program, it's likely to either erase your entire drive and reinstall Win7 from scratch, or fail because it finds other partitions on the drive that it does not understand.

And, while there is a Boot Repair CD image out there you can download, it won't do you any real good if you actually erased your Win7 OS partition.


Windows 7 came on my computer when I got my Dell Studio 1555. I later decided to install Ubuntu on it also which I allowed about 60GB. Windows should have around 420GB since the actual size of a hardrive advertised as 500GB is really about 481GB.

---

### Post by oldfred on 2011-10-29
If you just want to boot windows. You can use Windows repairCD/USB or from Ubuntu install lilo's boot loader which will also boot to the Windows partition.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

It looks like the extended partition was shrunk to include just swap. Grub is looking to boot from sda5 which is now swap. But you have space between sda3 & sda4(the extended). If you want to reinstall Ubuntu you will have to expand the sda4 extended into the unallocated and create a new / (root) partition for Ubuntu. Or you can just delete sda4 the extended and the auto install should create a new extended with both / & swap.

---

### Post by Lennatron on 2011-10-29
> **oldfred said:**
> If you just want to boot windows. You can use Windows repairCD/USB or from Ubuntu install lilo's boot loader which will also boot to the Windows partition.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

It looks like the extended partition was shrunk to include just swap. Grub is looking to boot from sda5 which is now swap. But you have space between sda3 & sda4(the extended). If you want to reinstall Ubuntu you will have to expand the sda4 extended into the unallocated and create a new / (root) partition for Ubuntu. Or you can just delete sda4 the extended and the auto install should create a new extended with both / & swap.

Hi,

I am I suppose to be going into synaptics and settings by booting into Ubuntu with the bootable disk I made with my flash drive? I searched for Synaptics in Ubuntu and it couldn't find it. I then went into to the system settings and I can't find synaptics. The bootable disk I made is of Ubuntu 11.10.

---

### Post by westie457 on 2011-10-29
> sda2: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files: /bootmgr /Boot/BCD

sda3: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files: /Windows/System32/winload.exe

sda4: __________________________________________________ ________________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info: 

This looks like you deleted the Ubuntu partition as you wanted and Grub is still in the MBR. At the moment to get things working you can reinstall Ubuntu to its own partition like it was or you can get a Windows install disk or a Windows recovery disk and run the option to repair your computer.

If you let the automatic repair to run and check the Windows files and file system it will eventually report that the OS has booted correctly. Try to reboot again, it quite probably will not start. Do not panic. Repeat the repair procedure again and instead of automatic repair drop to a Command Prompt, type in and run these commands one at a time pressing Enter each time ```
bootrec.exe /fixmbr

bootrec.exe /fixboot

bootrec.exe /rebuildbcd
```

* there is a space between the .exe and the/

If not sure wait for someone else to respond.

Good luck.

---

### Post by critin on 2011-10-29
> The bootable disk I made is of Ubuntu 11.10.

Do you have, or can you get use of another computer to download and burn a copy of 11.04?  It has Synaptics.  I also recommend you use 11.04 as 11.10 isn't stable yet.  For new users it's quite a challenge. IMO

---

### Post by oldfred on 2011-10-29
Yes in 11.10 they stopped installing synaptic by default. It was one of the first things I installed. But I am still using Maverick as my standard system as I am not able to upgrade very often (spouse issues on too many updates).

You can add to liveCD, but on every reboot will have to re-add it ad CD does not save it.
```

sudo apt-get install synaptic
```

---

### Post by Hakunka-Matata on 2011-10-29
> **critin said:**
> Do you have, or can you get use of another computer to download and burn a copy of 11.04?  It has Synaptics.  I also recommend you use 11.04 as 11.10 isn't stable yet.  For new users it's quite a challenge. IMO

I respectfully disagree with the assessment above.  

**11.10 i386 Desktop **is working just fine thank you, for me at least.  

I do prefer using the Gnome-Shell gdm.

synaptic can be easily installed:
```
sudo apt-get install synaptic
```

---

### Post by critin on 2011-10-30
> **nothingspecial said:**
> Yep.

Thank you!

---

### Post by critin on 2011-10-30
> **Hakunka-Matata said:**
> I respectfully disagree with the assessment above.  

**11.10 i386 Desktop **is working just fine thank you, for me at least.  

I do prefer using the Gnome-Shell gdm.

synaptic can be easily installed:
```
sudo apt-get install synaptic
```

11.10 works for me also, though I have to use 2D.
I'm speaking to general users who need things just to work without having to add this and that through the terminal.  Without having to search for code to make something work and it still won't.  11.10 is not a simple os for a user who knows little about the system.  I would encourage these users to use an earlier version so they could learn with enjoyment, not frustration.  But, that's only my opinion.  I appreciate yours.  :D   I'm enjoying my journey through linux; ubuntu especially.

---

### Post by Lennatron on 2011-10-31
> **oldfred said:**
> If you just want to boot windows. You can use Windows repairCD/USB or from Ubuntu install lilo's boot loader which will also boot to the Windows partition.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

It looks like the extended partition was shrunk to include just swap. Grub is looking to boot from sda5 which is now swap. But you have space between sda3 & sda4(the extended). If you want to reinstall Ubuntu you will have to expand the sda4 extended into the unallocated and create a new / (root) partition for Ubuntu. Or you can just delete sda4 the extended and the auto install should create a new extended with both / & swap.


I can now boot into Windows 7! Thank you so much for all of your help :)

I would also like to thank everyone who has posted on this thread for I appreciate anything you had to contribute to my issue.

Now I have only one question. When I turn on my computer I have a choice to boot Windows 7 and there are no other choices. Is there a way to make it boot Windows 7 without asking me first? I don't know it asks since the only choice is Windows 7.

I went to msconfig (Microsoft Configuration) and Windows 7 is the only item listed and it says it the current default OS.

Thanks

---

### Post by critin on 2011-10-31
>  Is there a way to make it boot Windows 7 without asking me first?It does go ahead and boot automatically if you don't choose doesn't it?  

I believe if you check msconfig it will let you edit the time to give the os to boot.  If you set it to 0 it should boot immediately since it's default.

Of course this is probably the lazy, easy way out, and someone can tell you how to get rid of this screen.  I can't.  Mine gives me the choice of Windows and Windows recovery with 10 seconds to decide--I want them both there for obvious reasons.  lol

---

