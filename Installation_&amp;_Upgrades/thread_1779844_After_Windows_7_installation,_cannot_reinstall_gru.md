---
title: "After Windows 7 installation, cannot reinstall grub."
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by hitchhiker4242 on 2011-06-11
After installing Windows 7 on my laptop, which was already running Natty, I am having issues reinstalling grub. I tried to do this using the method from this tutorial: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows). However, when I enter: 

```
sudo grub-install --boot-directory=/media/71a8cf97-40d7-415f-b4bb-30446fbb372d/boot/dev/sda3
```all I get is the following output: 

```
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.

```I also tried using --root-directory instead of --boot-directory, and I tried --recheck on both of them without any luck. Assistance anyone?

---

### Post by YesWeCan on 2011-06-11
Hi there. Well, your install command is missing the install device. This may be because you missed out a space. Also, it looks like you want to install to a partition /dev/sda3. Is that what you really want to do? Normally you install to the device itself /dev/sda.

```
sudo grub-install --boot-directory=/media/71a8cf97-40d7-415f-b4bb-30446fbb372d/boot /dev/sda
```

There are scenarios where you might want to install to sda3, such as if you want to use Window's boot-loader to boot Ubuntu using, for example, EasyBCD. You haven't mentioned this so I assume you probably want to use Grub to boot both Windows and Ubuntu.

---

### Post by wildmanne39 on 2011-06-11
> **hitchhiker4242 said:**
> After installing Windows 7 on my laptop, which was already running Natty, I am having issues reinstalling grub. I tried to do this using the method from this tutorial: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows). However, when I enter: 

```
sudo grub-install --boot-directory=/media/71a8cf97-40d7-415f-b4bb-30446fbb372d/boot/dev/sda3
```all I get is the following output: 

```
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.

```I also tried using --root-directory instead of --boot-directory, and I tried --recheck on both of them without any luck. Assistance anyone?
Hi, I went and read that guide carefully and there is a difference in your code and theres at the end your code should have a space between boot and /dev/sda

---

### Post by hitchhiker4242 on 2011-06-11
Wow, what stupid mistakes haha. Unfortunately this still doesn't work. I added the space and used /dev/sda, but I still got the same output as above. Only now instead of saying "install_device not specified" at the top it says "Unrecognized option `--boot-directory=/media/71a8cf97-40d7-415f-b4bb-30446fbb372d/boot'". I tried the --root variation and it went through, but now when I boot up I get a grub command line and can't boot Windows or Ubuntu.

---

### Post by Quackers on 2011-06-11
If you are booted into the live cd desktop you need to first mount your Ubuntu root partition ```
sudo mount /dev/sdXY /mnt
``` replacing /dev/sdXY with your Ubuntu root partition (ie /dev/sda5), check which is yours.
Then run ```
sudo grub-install --root-directory=/mnt /dev/sdX
``` replacing /dev/sdX with your bootable hard drive designation (eg /dev/sda).

Or alternatively ```
sudo grub-install --boot-directory=/mnt /dev/sdX
``` if you are using the latest version of grub (but the first one should still work with that afaik).

---

### Post by hitchhiker4242 on 2011-06-11
> If you are booted into the live cd desktop you need to first mount your Ubuntu root partition  	Code:
 	sudo mount /dev/sdXY /mnt 
 replacing /dev/sdXY with your Ubuntu root partition (ie /dev/sda5), check which is yours.
Then run  	Code:
 	sudo grub-install --root-directory=/mnt /dev/sdX 
 replacing /dev/sdX with your bootable hard drive designation (eg /dev/sda).

Or alternatively  	Code:
 	sudo grub-install --boot-directory=/mnt /dev/sdX 
 if you are using the latest version of grub (but the first one should still work with that afaik).

I've tried this method as well, but it yields the same results as the other way. "--boot-directory" is an unrecognized option. I'm using a Natty live cd right now, which presumably has the latest version of grub, but apparently not. Using "--root-directory" it says that installation was successful, but then when I boot from my hard drive all I get is a grub command line from which I can't get into any OS.

---

### Post by Quackers on 2011-06-11
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by linuxinstalledfromhdd on 2011-06-11
This is more or less just an observation here.. Just a suggestion for next time....   Wipe the hdd drive completely.  Install Windows first, and then install Ubuntu last.    And if you really need windows on your computer after you have already installed Ubuntu first, try using something like this:

[http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/](http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/)

You guys make everything so completely complicated for yourselves, and I don't understand why, when all you really needed to do was some data migration with an external hard drive or something. And then follow the order of operation to work with the existing Ubuntu automatic partitioning during a fresh install.

---

### Post by hitchhiker4242 on 2011-06-11
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.01 debian-20100714 ...........>...r>..........4...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1437648 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    84,092,927    83,886,080   7 NTFS / exFAT / HPFS
/dev/sda3          84,092,928   114,092,031    29,999,104  83 Linux
/dev/sda4         114,094,078   976,771,071   862,676,994   5 Extended
/dev/sda5         114,094,080   972,771,327   858,677,248  83 Linux
/dev/sda6         972,773,376   976,771,071     3,997,696  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2048 MB, 2048729600 bytes
64 heads, 62 sectors/track, 1008 cylinders, total 4001425 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,999,743     3,999,682   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       3a8fea6f-23c1-4601-b4d5-0b522f12ce23   ext3       
/dev/sda1        FABE07FCBE07B065                       ntfs       System Reserved
/dev/sda2        32EEDBABEEDB659F                       ntfs       
/dev/sda3        71a8cf97-40d7-415f-b4bb-30446fbb372d   ext4       
/dev/sda5        2fd79029-6b75-4e96-85e7-96753f7f4d99   ext4       
/dev/sda6        e5db3d2d-a501-43b5-9770-d2bb0a2cfadb   swap       
/dev/sdb1        E13C-C813                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 71a8cf97-40d7-415f-b4bb-30446fbb372d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 71a8cf97-40d7-415f-b4bb-30446fbb372d
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 71a8cf97-40d7-415f-b4bb-30446fbb372d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=71a8cf97-40d7-415f-b4bb-30446fbb372d ro acpi_backlight=vendor  quiet splash
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 71a8cf97-40d7-415f-b4bb-30446fbb372d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=71a8cf97-40d7-415f-b4bb-30446fbb372d ro single acpi_backlight=vendor
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 71a8cf97-40d7-415f-b4bb-30446fbb372d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 71a8cf97-40d7-415f-b4bb-30446fbb372d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=71a8cf97-40d7-415f-b4bb-30446fbb372d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=2fd79029-6b75-4e96-85e7-96753f7f4d99 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=e5db3d2d-a501-43b5-9770-d2bb0a2cfadb none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  52.234733582 = 56.086618112   boot/grub/core.img                             1
  48.429325104 = 52.000591872   boot/grub/grub.cfg                             1
  52.230823517 = 56.082419712   boot/grub/stage2                               1
  41.522953033 = 44.584931328   boot/initrd.img-2.6.35-28-generic              1
  48.153602600 = 51.704537088   boot/initrd.img-2.6.38-8-generic               2
  41.024414062 = 44.049629184   boot/vmlinuz-2.6.35-28-generic                 2
  47.329410553 = 50.819567616   boot/vmlinuz-2.6.38-8-generic                  1
  48.153602600 = 51.704537088   initrd.img                                     2
  41.522953033 = 44.584931328   initrd.img.old                                 1
  47.329410553 = 50.819567616   vmlinuz                                        1
  41.024414062 = 44.049629184   vmlinuz.old                                    2

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
ui gfxboot bootlogo
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

Unknown BootLoader on sda4

00000000  88 e5 44 7a 42 30 39 ce  61 6b d7 25 31 1a ec cd  |..DzB09.ak.%1...|
00000010  f6 0d 7f 40 e3 e4 49 84  a7 84 42 e9 d6 1d 49 95  |...@..I...B...I.|
00000020  48 b2 ed 8c 82 95 c8 8d  da 80 c8 dd 65 44 60 22  |H...........eD`"|
00000030  5b 05 21 ce 72 33 c5 2a  d4 4c 82 a3 02 88 ca eb  |[.!.r3.*.L......|
00000040  41 d4 64 c5 f6 ef 45 65  29 47 2b 0c 65 3f 53 82  |A.d...Ee)G+.e?S.|
00000050  60 4f 03 0b 64 5f 71 51  1c 44 83 19 b0 2b 64 4c  |`O..d_qQ.D...+dL|
00000060  16 cc f4 99 68 93 15 d9  ca 99 80 99 a6 c1 63 00  |....h.........c.|
00000070  49 fd be a8 6b fe c8 03  14 56 9b d6 a7 81 85 c1  |I...k....V......|
00000080  ee 42 40 56 15 24 0d 9f  7c e4 20 c4 2b be 53 5b  |.B@V.$..|. .+.S[|
00000090  14 d3 0e 39 be b2 f1 ea  3a 46 24 6d 09 42 fa 17  |...9....:F$m.B..|
000000a0  75 9a c8 9d bc 61 f4 2c  5b 57 43 b7 a4 2d 23 57  |u....a.,[WC..-#W|
000000b0  5b 62 de 37 b0 ee 0e 3a  f8 e4 ed 8a fa ae 27 07  |[b.7...:......'.|
000000c0  02 c1 e2 c7 0d d4 4c 24  f4 81 e7 33 3a 22 2b a3  |......L$...3:"+.|
000000d0  8a f0 83 3c 17 c2 2d 4a  66 6c ce f7 1f 4b 53 f1  |...<..-Jfl...KS.|
000000e0  6f 87 28 71 a1 3f 4c 18  a9 d9 5e 68 46 3f 8b d2  |o.(q.?L...^hF?..|
000000f0  9c 13 c9 4e 3b 47 3c 68  f4 ed 39 03 a1 99 84 00  |...N;G<h..9.....|
00000100  96 53 c2 79 5a 4e e3 9e  3d f7 9e a1 55 41 de 16  |.S.yZN..=...UA..|
00000110  e1 a5 b9 63 18 be 89 93  d9 1f c9 17 06 7e ae 1e  |...c.........~..|
00000120  3a 74 1b d7 2f 9d d7 13  40 73 89 e4 bf e5 af 66  |:t../...@s.....f|
00000130  b8 0e 19 66 6c 84 7c e2  0d df 51 86 b3 70 13 23  |...fl.|...Q..p.#|
00000140  be 0a 62 d5 22 83 bc 09  95 48 c9 e8 5b 90 da d3  |..b."....H..[...|
00000150  c7 48 ec ce c7 53 ee 42  72 40 4c 74 e1 59 f9 42  |.H...S.Br@Lt.Y.B|
00000160  74 e3 ee 1d 84 d3 6d 2b  da 21 47 e3 c8 2d 89 7c  |t.....m+.!G..-.||
00000170  df 20 d2 7e 23 98 c6 fb  5e 41 1f 99 4b 92 a7 56  |. .~#...^A..K..V|
00000180  21 83 d2 11 e0 2a ed b9  38 08 d5 41 1a b1 bd 82  |!....*..8..A....|
00000190  cb 44 ac 58 c7 25 78 04  61 d9 af 77 e3 ba 70 0e  |.D.X.%x.a..w..p.|
000001a0  f6 29 62 ff 6f 46 3c 67  98 1b 2e 52 ea 55 8b 5a  |.)b.oF<g...R.U.Z|
000001b0  98 09 04 b8 19 93 51 c0  18 b3 28 dd f6 68 00 fe  |......Q...(..h..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 60 2e 33 00 fe  |...........`.3..|
000001d0  ff ff 05 fe ff ff 02 60  2e 33 00 08 3d 00 00 00  |.......`.3..=...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by Quackers on 2011-06-11
Grub legacy is installed in the mbr of /dev/sda!!! How-so? No wonder things aren't going well. It should be grub2 not grub legacy.
I suggest you follow the CHROOT section of the guide below and purge grub and install grub2.
The partition you need to mount first is /dev/sda3 and grub should be installed to /dev/sda
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by hitchhiker4242 on 2011-06-11
> This is more or less just an observation here.. Just a suggestion for  next time....   Wipe the hdd drive completely.  Install Windows first,  and then install Ubuntu last.    And if you really need windows on your  computer after you have already installed Ubuntu first, try using  something like this:

[http://cinderbox.net ]("http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/")[http://cinderbox.net/2011/06/08/how-...vmware-player/]("http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/")[/2011/06/08/how-...vmware-player/]("http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/")

You guys make everything so completely complicated for yourselves, and I  don't understand why, when all you really needed to do was some data  migration with an external hard drive or something. And then follow the  order of operation to work with the existing Ubuntu automatic  partitioning during a fresh install.

I already had Ubuntu on my computer and it is all customized and tweaked exactly the way I like it. I don't want to have to do a fresh install and then do all of that over again, because it's quite a lot. I needed Windows so that I could run Pro Tools, which I'm sure wouldn't work at all in a virtual machine. The funny thing is that I've done all of this before without any problems. I've been running Ubuntu for over a year now, and have installed and uninstalled Windows in the past more or less without a hitch. I didn't think it would turn out complicated like this because in the past it was pretty simple.

---

### Post by YesWeCan on 2011-06-11
In addition to the chroot method,

A simple way to avoid any of these problems ever again is to install Grub2 to a different drive. For example, a 4GB USB stick, provided your PC can boot off USB.
Just make a fresh install of Ubuntu to the USB and boot off it. When in USB Ubuntu run 'sudo update-grub' and this will add both your Windows and HD Ubuntu to the Grub menu. Then you boot off the USB stick each time.

-----

Another thing you can do right away is to boot your Ubuntu from the legacy Grub prompt:
grub> root (hd0,3)
grub> kernel /vmlinuz root=/dev/sda3 ro
grub> initrd /initrd
grub> boot
Once booted you can do 'sudo apt-get install grub-pc' to upgrade to Grub2.

---

### Post by hitchhiker4242 on 2011-06-11
Thanks to everyone who replied for your patience. The chroot method finally worked for me.

---

### Post by Quackers on 2011-06-11
I'm very glad you got things sorted out :-)

---

