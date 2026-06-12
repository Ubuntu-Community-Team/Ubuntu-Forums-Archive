---
title: "dual boot problem (win7 and ubuntu 11.04)"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by gulonder on 2011-07-09
Hi everyone. I'm actually new here and this is my first post, I will be very glad if you guys could help. I am also quite a newbie having ubuntu experience for maybe 18 hours now. I checked the forum a bit and couldn't see a thread already posted which can solve my problem. But I might have overlooked or maybe I didn't even get that it was the solution of my problem. I apologize if any of that is the case.

I wanted to install ubuntu 11.04 alongside win7 on my notebook (with no optical drive). I created 2 primary partitions (one for win7[ntfs] one for ubuntu[ext4]) and 2 logical partitions (one for swap one for general use for storage[ntfs]) by running ubuntu from my USB Flash disk and using gparted. First, I installed win7 without having any problem, then ubuntu also without having any (apparent) problem (I installed boot loader on MBR: the default setting). After the ubuntu installation is over, I was instructed to restart my computer as usual and win7 started without asking me which OS to boot. When I run ubuntu from my Flash disk and run gparted and selected the boot drive as the partition on which ubuntu was installed, I got the error saying "missing operating system". I suppose GRUB is misconfigured and that is causing the problem because nothing went wrong during the installation processes. I have no idea how to configure GRUB by running ubuntu from my Flash disk. BTW win7 is working just fine. I would be very thankful if you could help.

---

### Post by oldfred on 2011-07-09
Welcome to the forums.

If sounds like grub installed its boot loader to the wrong place. It should be in the MBR of the sda drive. But if you are still booting windows then windows boot loader must be there. Boot flag is only used by windows (and lilo) but not by grub. So leave the boot flag on the windows boot partition and make sure windows boots. 

Have you made a repair CD from windows. You should always have a repair Cd or liveCd/USB of the current version of every operating system you have.

Make your own Windows recoveryCD:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

If grub installed to the external flash drive, does it still boot, or can you get the liveUSB to work?

So we can tell where everything is at download this from liveUSB:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by gulonder on 2011-07-09
> If sounds like grub installed its boot loader to the wrong place. It should be in the MBR of the sda drive. But if you are still booting windows then windows boot loader must be there. To be more specific I installed the boot loader on /dev/sda which was also the default setting. /dev/sda1 is where windows 7 is installed. /dev/sda2 is the mount point. sda5 is swap and sda6 is basically empty.

> Boot flag is only used by windows (and lilo) but not by grub. So leave the boot flag on the windows boot partition and make sure windows boots. OK. I put the flag back at sda1.

> If grub installed to the external flash drive, does it still boot, or can you get the liveUSB to work?I have no idea if grub is installed to anywhere but liveUSB boots and works perfectly so as win7.

I deeply thank meierfra & Gert Hulselmans.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 8200 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   409,602,047   409,600,000   7 NTFS / exFAT / HPFS
/dev/sda2         409,602,048   614,402,047   204,800,000  83 Linux
/dev/sda3         614,404,094 1,465,147,391   850,743,298   5 Extended
/dev/sda5         614,404,096   626,692,095    12,288,000  82 Linux swap / Solaris
/dev/sda6         626,694,144 1,465,147,391   838,453,248   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2055 MB, 2055021056 bytes
255 heads, 63 sectors/track, 249 cylinders, total 4013713 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     4,013,712     4,013,650   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7724673B4792297A                       ntfs       
/dev/sda2        41e84ecd-a71d-4013-a9c0-0ac18bc80f13   ext4       
/dev/sda5        fa5a17a8-88dc-48d2-b6ae-90a1be4dd0a3   swap       
/dev/sda6        25F0170F6E52B2E2                       ntfs       
/dev/sdb1        7462-B095                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=41e84ecd-a71d-4013-a9c0-0ac18bc80f13 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fa5a17a8-88dc-48d2-b6ae-90a1be4dd0a3 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 265.446285248 = 285.020778496  boot/vmlinuz-2.6.38-8-generic                  1
 265.446285248 = 285.020778496  vmlinuz                                        1

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

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```Thank you VERY much for helping.

---

### Post by oldfred on 2011-07-09
You only have part of the boot files and are missing grub's files in your sda2 / (root) partition. I suggest manual reinstall to the same partitions, so you do not create new partitions. Did you check that the install CD/USB is complete?

You only have vmlinuz file, not grub nor initrd.
```
 130.081863403 = 139.674337280  boot/grub/core.img                             1
 124.212078094 = 133.371703296  boot/grub/grub.cfg                             1
 125.711738586 = 134.981951488  boot/initrd.img-2.6.38-7-generic               2
 130.080078125 = 139.672420352  boot/vmlinuz-2.6.38-7-generic                  1
 125.711738586 = 134.981951488  initrd.img                                     2
 130.080078125 = 139.672420352  vmlinuz                                        1

```

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by gulonder on 2011-07-16
I have worked it out. I was trying to install Ubuntu in a customized fashion by choosing explicitly in which partition to install the OS and which partition to be used as swap (via choosing "Something else" in "Allocate drive space" window which comes up during installation process). The partitions were already created via GParted before the installation. I guess, this causes some trouble to GRUB and looks like necessary files are either missing or installed to somewhere else. So, what I did was leaving non-allocated space in HDD for Ubuntu and choosing the default settings during installation process (via choosing "Install Ubuntu alongside Windows 7" in "Allocate drive space" window). I also heard that for some specific partition settings, GRUB installation can fail and you have to manually install the necessary files for booting. But still, thank you very much for your help and time.

P.S. I think it's better not to tag this as SOLVED because the problem would still be there if I installed Ubuntu again with the initial settings I have mentioned.

---

