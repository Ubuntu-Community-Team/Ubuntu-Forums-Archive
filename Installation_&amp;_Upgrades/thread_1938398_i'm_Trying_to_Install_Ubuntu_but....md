---
title: "i'm Trying to Install Ubuntu but..."
date: 2012-03-09
forum: Installation &amp; Upgrades
---

### Post by Marco Virdia on 2012-03-09
I'm trying to  install ubuntu near windows but when i start the installation i can't go  on because it doesn't find room on the hard disk. 
  

When i run the installation, from both the cd or USB stick, Ubuntu  checks if there's the internet connection and if there's enough room on  the hard disk. 

Here's the problem: Ubuntu says that there's not enogh room on the hard  disk.
  

On the same hard disk i have Windows and it doesn't give me any  problem. I have all the room that Ubuntu may ask and a lot more,   evidently he can't see my hard disk.
  

I booted the live version of Gparted from CD, i checked the list of  hard drives and i saw that also Gparted doesn't manage to see my hard  disk.
  

I already formatted the whole hard disk, re-installed Windows and  tryed to install Ubuntu again but i still have the same problem.
  

What can i do to solve this problem?
  

few informations:

1) i used the disk gestion of windows 7 ultimate to format and make partitions
  

2) if i start wubi.exe from windows it opens a dialogue window:    pyrun.exe - disk not present    [a big X image] can not find the hard drive. Insert a disk into \Device\Harddisk1\DR1    [http://imageshack.us/photo/my-images/259/pyrun.jpg/](http://imageshack.us/photo/my-images/259/pyrun.jpg/)
  

if i press cancel or continue or whatever else it opens a new window  with \harddisk2\DR2, if i close also this new window it goes to  \harddisk3\DR3 and then to hardisk4\DR4
  

3) using the live version of ubuntu from the USB stick i went on the  terminal and told him to check the hard drives: he found only the USB  stick
  

I will be able to give you more informations on monday 12

---

### Post by bcbc on 2012-03-09
Please boot from the CD/USB, select "Try Ubuntu" and post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

There may be some issue with Ubuntu detecting your drive.

The wubi "no disk" error is completely unrelated though. That's bug [lpbug]365881[/lpbug], but even if you used the workaround you'd probably have the same issue if Ubuntu cannot see your hard drive.

---

### Post by Marco Virdia on 2012-03-13
I booted the boot_info and this is the result:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sde.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdf.

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.01 debian-20100714 ...........>...r>.......(+.4...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1427200 of /dev/sde1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sde1 starts at sector 
                       0. But according to the info from fdisk, sde1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 65544 of /dev/sdf1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sde _____________________________________________________________________

Disk /dev/sde: 1031 MB, 1031798784 bytes
32 heads, 62 sectors/track, 1015 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             62     2,013,759     2,013,698   c W95 FAT32 (LBA)


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 16.0 GB, 16013852672 bytes
78 heads, 14 sectors/track, 28641 cylinders, total 31277056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *          8,064    31,277,055    31,268,992   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sde1        3F7D-2B07                              vfat       
/dev/sdf1        860E-3118                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdf1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /media/Ubuntu 10.10 amd64 iso9660    (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


=========================== sde1/boot/grub/grub.cfg: ===========================

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

========================= sde1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sde1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sde1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sde1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

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

========================= sdf1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdf1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdf1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdf1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sda sdb sdc sdd no block devices found 

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```Tell me if you need more information
thanks for your time

---

### Post by bcbc on 2012-03-13
It doesn't show any hard drives. Just the 16GB pendrive and the 1GB usb stick? 

What drive is supposed to be there?

---

### Post by Marco Virdia on 2012-03-13
the device\sda must be a 500GB Hard Disk but as i told you ubuntu can't see it and i don't really know why :S

---

### Post by bcbc on 2012-03-13
In normal cases where ubuntu cannot see the drive, it 'sees' it physically but either cannot determine what's on it or finds partition table errors etc. It's pretty strange that it doesn't detect it physically at all.

What sort of drive is it? Specs/model #?

---

