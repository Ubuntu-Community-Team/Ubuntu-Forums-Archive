---
title: "installing ubuntu by installer for windows"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by randompunk on 2011-07-28
Hi Everyone, 

I have used WUBI to install ubuntu to try it out and it is dual booting with Windows 7.

When I restart my laptop and choose to boot Ubuntu from the dual boot menu, it loads up and shows the desktop with the following error whilst installing: 

No root file system is defined. Please correct this from the partitioning menu...

However, when I click to go into system settings then gparted I get another error:

Failed to run /usr/sbin/gparted as user root
Unable to copy the users Xauthorization file

I am totally new at this and was just intrigued to how Ubuntu runs.

I don't want to install it just yet until I have trialed it a little bit and when I have a system available that I can install it on.

Many thanks in advance for your help.

Lee

---

### Post by bcbc on 2011-07-28
Usually the no root filesystem issue is caused by an unsupported raid setup or a mix of MBR and GPT partition tables or some other partition problem that Ubuntu is sensitive to (and not windows).

Please post the results from the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").  That might show the problem. (you need an ubuntu cd/usb to do this - boot in 'live' mode i.e. boot from the cd/usb and select "Try it" without installing).

---

### Post by Typhaon on 2011-08-04
Hello,

I'm having the same issue as the OP.  Installing via Wubi gets the same error message.  I have no problems booting from a USB drive I made though.  Here's a copy of the bootinfoscript that was created. Ignore the date; that was done a few minutes ago, and I hadn't noticed that the USB boot hadn't updated time and date.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/mapper/pdc_bcgeahiicg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 60868 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

pdc_bcgeahiicg1: _______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

pdc_bcgeahiicg2: _______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

pdc_bcgeahiicg2/Wubi: __________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''

pdc_bcgeahiicg3: _______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,929,457,663 1,929,250,816   7 NTFS / exFAT / HPFS
/dev/sda3       1,929,457,664 1,953,122,303    23,664,640   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    15,633,407    15,633,376   c W95 FAT32 (LBA)


Drive: pdc_bcgeahiicg _____________________________________________________________________

Disk /dev/mapper/pdc_bcgeahiicg: 1000.0 GB, 999999995904 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/pdc_bcgeahiicg1   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/pdc_bcgeahiicg2            206,848 1,929,457,663 1,929,250,816   7 NTFS / exFAT / HPFS
/dev/mapper/pdc_bcgeahiicg3      1,929,457,664 1,953,122,303    23,664,640   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1EE61361E613388B                       ntfs       SYSTEM
/dev/sda2        5EF61617F615F04F                       ntfs       HP
/dev/sda3        1688AFA188AF7E3D                       ntfs       FACTORY_IMAGE
/dev/sdb1        1EF9-2612                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr0         /media/HOW_I_MET_YOUR_MOTHER_S1_D1 udf        (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,umask=0077,dmode=0500)


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
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on pdc_bcgeahiicg2/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

/home/ubuntu/Downloads/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by bcbc on 2011-08-04
> **Typhaon said:**
> Hello,

I'm having the same issue as the OP.  Installing via Wubi gets the same error message.  I have no problems booting from a USB drive I made though.  Here's a copy of the bootinfoscript that was created. Ignore the date; that was done a few minutes ago, and I hadn't noticed that the USB boot hadn't updated time and date.


Hi, and welcome to the forums :)
Don't worry about that date - it's the release date for version 0.60 of the bootinfoscript ;)

What sort of raid are you running? It looks like there is a problem reading it - so that's likely your problem.

To be honest - I know very little about raids, but here is an interesting article that covers some of the problems Ubuntu has with fakeraids: [http://www.advogato.org/person/robertc/diary.html?start=158](http://www.advogato.org/person/robertc/diary.html?start=158)

---

### Post by Typhaon on 2011-08-04
I didn't even realize I was running a RAID setup.  This is an HP HPE-112y with only one hard drive, and I haven't added another since I bought it.  Sure enough, though, looking on the BIOS settings the SATA controller type is set to RAID (vs. IDE and AHCI).  Under the RAID option ROM, though, it only says it's "raid ready" and doesn't say it's currently set up in any particular RAID configuration.  I tried to set the BIOS to AHCI and reboot Ubuntu, but I still got the same message.  So, I was going to reboot into Windows and uninstall/reinstall Wubi to see if that fixed things, but Windows won't boot with it set to AHCI and the startup recovery software wouldn't fix it.  Does that mean I'm screwed unless I start fresh and reinstall Windows?

---

### Post by bcbc on 2011-08-04
> **Typhaon said:**
> I didn't even realize I was running a RAID setup.  This is an HP HPE-112y with only one hard drive, and I haven't added another since I bought it.  Sure enough, though, looking on the BIOS settings the SATA controller type is set to RAID (vs. IDE and AHCI).  Under the RAID option ROM, though, it only says it's "raid ready" and doesn't say it's currently set up in any particular RAID configuration.  I tried to set the BIOS to AHCI and reboot Ubuntu, but I still got the same message.  So, I was going to reboot into Windows and uninstall/reinstall Wubi to see if that fixed things, but Windows won't boot with it set to AHCI and the startup recovery software wouldn't fix it.  Does that mean I'm screwed unless I start fresh and reinstall Windows?
Just set back the BIOS to what it was and windows should boot. I hope you haven't let the recovery software do anything. (It's best to let someone who knows something about raids help you before trying random things ;) ). I've seen threads in the past recommend deleting raid metadata - that is present on 'raid ready' computers. That seems to be what is going on here. But you shouldn't have to reinstall windows to do this.

Maybe check with HP as well to figure out what's going on?

---

### Post by Typhaon on 2011-08-04
> **bcbc said:**
> Just set back the BIOS to what it was and windows should boot. I hope you haven't let the recovery software do anything. (It's best to let someone who knows something about raids help you before trying random things ;) ). I've seen threads in the past recommend deleting raid metadata - that is present on 'raid ready' computers. That seems to be what is going on here. But you shouldn't have to reinstall windows to do this.

Maybe check with HP as well to figure out what's going on?

Ha, thanks. :-)  Windows boots with it set to RAID again even after using that startup repair program.  I'll look and see if I can find another thread about about that.  I'll also see about checking with HP, but as my warranty expired five months ago, I'm not sure how eager they'll be to talk to me. :-P  Thanks for the assistance; now I at least know what I'm looking for solve this. :-)

---

### Post by Typhaon on 2011-08-04
Update: I managed to get Windows to boot up with the BIOS set to AHCI now, so it's no longer set to a RAID in BIOS.  However, after reinstalling Ubuntu, I still get the same problem.  I assume there's something I need to do with how the filesystem recognizes the drive as well.  Where should I go from here?

---

### Post by bcbc on 2011-08-04
> **Typhaon said:**
> Update: I managed to get Windows to boot up with the BIOS set to AHCI now, so it's no longer set to a RAID in BIOS.  However, after reinstalling Ubuntu, I still get the same problem.  I assume there's something I need to do with how the filesystem recognizes the drive as well.  Where should I go from here?
My advice is to create a new thread - state clearly in the title what the issue is, and include the bootinfoscript.

---

### Post by Typhaon on 2011-08-04
Haha!  I figured out what the issue was!  You were right, the RAID metadata needed to be removed.  Took a bit of searching, but I managed to find a way to do it through the LiveCD and DMRAID.  Couldn't find a way to do it in Windows though.  Anyway, Ubuntu is installed now, my Windows install is still intact, and I'm working like a charm. :-)

---

### Post by bcbc on 2011-08-04
> **Typhaon said:**
> Haha!  I figured out what the issue was!  You were right, the RAID metadata needed to be removed.  Took a bit of searching, but I managed to find a way to do it through the LiveCD and DMRAID.  Couldn't find a way to do it in Windows though.  Anyway, Ubuntu is installed now, my Windows install is still intact, and I'm working like a charm. :-)

Cool! Good job.

---

### Post by YannBuntu on 2011-08-08
Hello
> **Typhaon said:**
> Haha!  I figured out what the issue was!  You were right, the RAID metadata needed to be removed.  Took a bit of searching, but I managed to find a way to do it through the LiveCD and DMRAID.  

Please could you give more details? where were the metadata, and which files have you removed ?

---

