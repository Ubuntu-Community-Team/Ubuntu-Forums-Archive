---
title: "Freeze during partition resize!"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by PloXyZeRO on 2011-07-18
**I'm terribly sorry, I posted this exact post in general help about 45 minutes ago. I realized that it would be more appropriate to post here. Sorry for the duplicate!**

-----------

Hi. I'm having a problem. This is my first time using Ubuntu, so I don't really know much about it. I tried installing it from a DVD earlier, but it wouldn't work. Then I tried on my flash drive, still didn't work. I realized that the downloaded iso (Ubuntu 11.04 64 bit) was only 411 MB instead of 698 MB. I then tried to download it again, and it was the correct size. 

I booted it off my flash drive, and tried to install. It asked how much of the HDD space I wanted to reserve for Ubuntu, I think. I can't quite remember, but I dragged it over to 30 GB. Now I realize that I don't actually need that much, oh well. I got an error, can't quite remember what it said, but then the same window came up again asking to resize the partition. There was only about 20 GB availiable this time (instead of the 320 before), I reserved 6 GB, and clicked continue. I checked back after like 3 hours and the window is white and frozen. 

Is there any way I can restart my laptop and correct the issue without messing anything up? I'm not really sure what I did wrong.

If it matters, I'm installing it on an Alienware M11x laptop.
I'm not quite sure, but I think the specs are
Nvidia GeForce 335M
320 GB HDD
i5 U520M processor @ 1.07 GHz (ranked over 3.0 GHz)
Windows 7 64-bit

If there's any other information you need, just ask and I'll try to tell you. PLEASE help! Thank you in advance

---

### Post by lmarmisa on 2011-07-18
Boot your laptop into an Ubuntu Live CD / USB and select Try Ubuntu.

Open Firefox and go to the page [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Follow the instructions of the page for downloading and running the Boot Info Script.

Finally post the results in this thread.

You will receive more help according these results.

Best regards,

Luis

---

### Post by PloXyZeRO on 2011-07-18
Okay thank you! I'll try that right away. The only way I can get it to reboot though is if I shut if off manually. I hope nothing bad happens!

---

### Post by PloXyZeRO on 2011-07-18
Here is the information that I got from that (Sorry, my date and time aren't correct)
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
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
    Boot files:        /Windows/System32/winload.exe /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 15262 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    18,922,939    18,841,020   7 NTFS / exFAT / HPFS
/dev/sda3          30,801,920   625,140,399   594,338,480   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2003 MB, 2003795968 bytes
32 heads, 63 sectors/track, 1941 cylinders, total 3913664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     3,913,055     3,912,993   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        30B4B895B4B85ED2                       ntfs       RECOVERY
/dev/sda3        1CD4BAC8D4BAA384                       ntfs       OS
/dev/sdb1        16FE-1152                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
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
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by lmarmisa on 2011-07-18
According to the results of Info Boot Script, you have installed Ubuntu using Wubi. 

This video shows an example about it (sorry, I dislike its music :( )

[http://www.youtube.com/watch?v=Fy1ISEJIv84](http://www.youtube.com/watch?v=Fy1ISEJIv84)

A specific NTFS partition was created for Ubuntu in that video. This step is optional. You can store the Ubuntu files and folders in the unit "C:" if you want.

This other video shows how to boot into Ubuntu using Wubi:

[http://www.youtube.com/watch?v=riVaNl5a9D0](http://www.youtube.com/watch?v=riVaNl5a9D0)

I am not sure if your Ubuntu Wubi installation was successful or not. Please, give us more information if you need help.

Best regards,

Luis

---

### Post by lmarmisa on 2011-07-18
Another video about Ubuntu and Wubi:

[http://www.youtube.com/watch?v=iW1V6TuZZmc](http://www.youtube.com/watch?v=iW1V6TuZZmc)

This video shows not only how to install and use it but also how to unistall Ubuntu with Wubi in the case you need to do that.

---

