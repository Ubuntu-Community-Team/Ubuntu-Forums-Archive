---
title: "&quot;No root file system defined&quot;"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by Alex455 on 2011-06-28
All right, round two.  I got Ubuntu 10.10 to install on the other computer, now I'm working on this one.  I went through the same processes as I had last time, but I got a different error, it says that no root system is defined. (Shown in the image)  The partitioning menu (I'm assuming it's the screen above "Boot loader") doesn't offer me any options, and the drop-down arrow won't let me select anything other than /dev/sda.

[http://i53.tinypic.com/25u14q9.png](http://i53.tinypic.com/25u14q9.png)

I'm installing from the same flash drive containing the info I'd gotten from Unetbootin, the same one as in this thread: [http://ubuntuforums.org/showthread.php?t=1788706](http://ubuntuforums.org/showthread.php?t=1788706) (Though I'm installing it on a different computer, the installation on the one mentioned in that thread was completed.)

Here's the RESULTS.txt:

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Acer PQService MBR is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdf.
 => Acer PQService MBR is installed in the MBR of /dev/mapper/nvidia_fadaaaai.

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

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 1473688 of /dev/sdf1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /ldlinux.sys

nvidia_fadaaaai1: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /boot/BCD

nvidia_fadaaaai2: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    30,732,344    30,732,282  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     30,734,336 1,250,260,991 1,219,526,656   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 2056 MB, 2056257536 bytes
16 heads, 32 sectors/track, 7844 cylinders, total 4016128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *             32     4,016,127     4,016,096   e W95 FAT16 (LBA)


Drive: nvidia_fadaaaai _____________________________________________________________________

Disk /dev/mapper/nvidia_fadaaaai: 640.1 GB, 640135004160 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/nvidia_fadaaaai1                 63    30,732,344    30,732,282  27 Hidden NTFS (Recovery Environment)
/dev/mapper/nvidia_fadaaaai2   *     30,734,336 1,250,260,991 1,219,526,656   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        02341CAA341CA329                       ntfs       PQSERVICE
/dev/sda2        342ECC5A2ECC16B0                       ntfs       OS
/dev/sdf1        6B89-3230                              vfat       TravelDrive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdf1/boot/grub/grub.cfg: ===========================

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

============================== sdf1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry6 
menu label Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry7 
menu label Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash -- 
 
label ubnentry8 
menu label Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash -- 
 
--------------------------------------------------------------------------------

=================== sdf1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdf1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdf1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)


---

### Post by zvacet on 2011-06-29
You have to dedicate some free space to your Ubuntu installation and format it as ext4 and mount point should be / root.When you do that continue with install.

---

### Post by Alex455 on 2011-06-29
Thanks for your reply, Zvacet.  I wanted to just run a clean install over Vista, deleting it in the process, but I suppose I can just delete that partition after I have Ubuntu installed.

And hell, I suppose I can keep about 20GB or so of a Vista partition just in case.  Why not?

---

### Post by mörgæs on 2011-06-29
Yes, if you want to get rid of Windows, you just choose 'use entire disk for Ubuntu' while installing.

---

### Post by Alex455 on 2011-06-29
[http://i52.tinypic.com/n695hw.png](http://i52.tinypic.com/n695hw.png)

I shrank sda2 by about 20GB to install Ubuntu onto, but I'm still running into the same problems.

---

### Post by zvacet on 2011-06-29
See [this.]("http://www.ubuntu.com/download/ubuntu/download")When you get to the stage to allocate space choose **something else**.That will give you option to mark your partition (20GB) as /root and format it as ext4.

---

### Post by Alex455 on 2011-06-29
Excuse me if I'm missing something, but it never shows me the options in [http://tinyurl.com/3rsqptn](http://tinyurl.com/3rsqptn).  When I click "Install Ubuntu 10.10 it brings me to [this]("http://www.ubuntu.com/sites/www.ubuntu.com/files/active/natty/01-welcome.jpg") screen then [this]("http://www.ubuntu.com/sites/www.ubuntu.com/files/active/natty/03-preparing-to-install-ubuntu.jpg") screen then I see [this]("http://i53.tinypic.com/25u14q9.png") screen that I linked in the first post.  I didn't see an option in GParted to mark the partition I'd made as /root, though it did give me the option to format as ext4.  My apologies if I'm missing something, because it seems like I am, but I'm at a loss here.

---

