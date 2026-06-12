---
title: "Error in dual boot Win 7 with Ubuntu 11.04"
date: 2011-09-17
forum: Installation &amp; Upgrades
---

### Post by psyche842 on 2011-09-17
Hi

I'm really new in using Ubuntu and I already had Windows 7 installed in my machine and followed exactly how it's stated in this link on how to install ubuntu 11.04 and dual boot with Windows 7.

[http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/)

Everything were been done as how it is stated but now when I select Ubuntu under windows 7 boot up screen, I get the prompt which is shown in the attached.

[IMG]http://i241.photobucket.com/albums/ff196/psyche842/17092011302.jpg[/IMG]

I'm attaching the result sheet of bootscript as well.

```
                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 472568020 of the same hard drive 
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
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 32776 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   168,142,847   167,936,000   7 NTFS / exFAT / HPFS
/dev/sda3         168,142,848   472,311,807   304,168,960   7 NTFS / exFAT / HPFS
/dev/sda4         472,313,854   976,771,071   504,457,218   f W95 Extended (LBA)
/dev/sda5         556,283,904   976,771,071   420,487,168   7 NTFS / exFAT / HPFS
/dev/sda6         472,313,856   472,797,183       483,328  83 Linux
/dev/sda7         472,799,232   476,702,719     3,903,488  82 Linux swap / Solaris
/dev/sda8         476,704,768   496,234,495    19,529,728  83 Linux
/dev/sda9         496,236,544   556,281,855    60,045,312  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8039 MB, 8039300608 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15701759 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    15,701,758    15,701,696   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       765d2f71-0645-4e4b-a3a0-983af39e034d   ext2       casper-rw
/dev/sda1        5292867592865CFB                       ntfs       System Reserved
/dev/sda2        EC1C8C241C8BE7C2                       ntfs       Win 7
/dev/sda3        74726C39726C026A                       ntfs       Docs n Progs
/dev/sda5        2AEECF7FEECF4235                       ntfs       Setups
/dev/sda6        9eaff6a6-da7f-4b57-9b4e-956afa139670   ext2       
/dev/sda7        0843853c-a5a7-4483-b675-8ab6024426fc   swap       
/dev/sda8        5a848c0c-497d-480a-9d91-361469866264   ext4       
/dev/sda9        6b6392c9-832e-40f7-8980-3635603f5f7c   ext4       
/dev/sdb1        6E62-5C97                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
; This boot.ini was automatically generated by NeoSmart Technologies' BootGrabber.exe
; Use EasyBCD from http://neosmart.net/dl.php?id=1 to manage your bootloader

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Windows XP on D:\" /fastdetect
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

============================= sda6/grub/grub.cfg: ==============================

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
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 5a848c0c-497d-480a-9d91-361469866264
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 9eaff6a6-da7f-4b57-9b4e-956afa139670
set locale_dir=($root)/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 9eaff6a6-da7f-4b57-9b4e-956afa139670
    linux    /vmlinuz-2.6.38-11-generic-pae root=UUID=5a848c0c-497d-480a-9d91-361469866264 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 9eaff6a6-da7f-4b57-9b4e-956afa139670
    echo    'Loading Linux 2.6.38-11-generic-pae ...'
    linux    /vmlinuz-2.6.38-11-generic-pae root=UUID=5a848c0c-497d-480a-9d91-361469866264 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-11-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 9eaff6a6-da7f-4b57-9b4e-956afa139670
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 9eaff6a6-da7f-4b57-9b4e-956afa139670
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5292867592865CFB
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

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

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 225.338016510 = 241.954852864  grub/core.img                                  2
 225.341466904 = 241.958557696  grub/grub.cfg                                  1
 225.249118805 = 241.859399680  initrd.img-2.6.38-11-generic-pae              54
 225.235306740 = 241.844569088  vmlinuz-2.6.38-11-generic-pae                 21

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=5a848c0c-497d-480a-9d91-361469866264 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda6 during installation
UUID=9eaff6a6-da7f-4b57-9b4e-956afa139670 /boot           ext2    defaults        0       2
# /home was on /dev/sda9 during installation
UUID=6b6392c9-832e-40f7-8980-3635603f5f7c /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=0843853c-a5a7-4483-b675-8ab6024426fc none            swap    sw              0       0
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

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

 
```Can you please advice me on how to overcome this issue and I prefer to have the boot selection screen by Win 7 than Ubunutu.

Much appreciated.

---

### Post by Mark Phelps on 2011-09-17
OK, if you REALLY want to have Win7 control the boot choices, since you appear to have installed Ubuntu into its own partition, the first thing you will need to do is replace the MBR you overwrote when you installed Ubuntu.

To do that, you need to boot into Win7 and use the Backup Feature to create and burn a Win7 Repair CD.  You will need that in order to restore the original MBR you had when Win7 was the only OS on the PC.

You will then need to, inside Win7, download and install EasyBCD from the NeoSmart Technology forums.

---

### Post by oldfred on 2011-09-17
Welcome to the forums.

I do not know EasyBCD, you may have to go to their forums for the best help. Some here do use EasyBCD and may know details.
[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

You have installed grub or parts of grub to several partitions which may confuse EasyBCD. You made the /boot partition sda6 which is not how the instructions read and installed grub2's boot loader to sda6.

You have this in sda1 which will confuse Windows and in sda5 which is a NTFS partition.
/boot/grub/core.img

You have to delete the /boot folder in sda1, but also have to be careful not to delete /Boot that has the essential BCD file. Windows is not case sensitive so it sees that as the same folder and gets confused.
Boot Problems:/boot/grub/core.img On Windows
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

Not sure if those fixes will resolve all your issues but they are a start.

---

