---
title: "&quot;unknown file system grub resuce &gt; &quot; when Boot from External Harddisk"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by iamsuperuser on 2011-08-08
Greetings guys !!!

I'm very very very very new to Ubuntu and also this forum :)

I'm having a problem of booting Ubuntu 11.04 from my external hard disk.

I've gone an installation consists of following steps
1) Partitiioned free space from my Ext HD - 15gb for ubuntu , 1gb for swap

2) Boot using USB pendrive to install Ubuntu. File system = Ext 4. Boot Loader at /dev/sdc

3) Restart computer and unplug my USB Pendrive

4) Select USB Boot from bios.

5) Hit "Unknown File system Grub Rescue >"


I've been googling and digging around forums and tried some approaches but they din work out for me.

Result of fdisk 
-----------------------------------------------------------------------------------------------
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19325   155227038+   7  HPFS/NTFS
/dev/sda2           19327       19457     1052257+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 16.0 GB, 16013852672 bytes
78 heads, 13 sectors/track, 30845 cylinders
Units = cylinders of 1014 * 512 = 519168 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf5ce7a77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           8       30846    15634496    c  W95 FAT32 (LBA)

Disk /dev/sdc: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4512236f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              73       58804   471764790    7  HPFS/NTFS
/dev/sdc2   *       58854       60589    13944420   83  Linux
/dev/sdc3               1          72      576513    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sdc4           60590       60716     1017856   82  Linux swap / Solaris
/dev/sdc5               1          72      576512   82  Linux swap / Solaris

Partition table entries are not in disk order

-----------------------------------------------------------------------------------------------
I'm looking forward to do development in Ubuntu environment :(

Seriously hopes that someone out there are able to help !!!! GREATLY APPRECIATE !!

---

### Post by iamsuperuser on 2011-08-09
Guys, any idea ?? :(

---

### Post by slc1185 on 2011-08-09
I don't believe we're having quite the same issue...but the outcome is definitely the same:

--------------------------------------------------------------------------------------------------------
 I was trying to clean up my Dell Inspiron 1545 (getting rid  of my Kubuntu and Windows partition, reinstalling Windows). I was using  GParted to do the job and had just finished wiping Windows and Kubuntu  and reformatting. Was ready to exit and reinstall Windows when curiosity  got the best of me and I started wondering what would happen if I  deleted the 100mb system reserved partition. Well, that was a bad idea.

I can no longer access BIOS, I can't boot off of my Windows7 install.  disc, most of these actions result in a terminal-like environment:

error: no such partition.
grub rescue>
-------------------------------------------------------------------------------------------------------

I'm new to the Ubuntu Forums website and was hoping to see what kind of answers people give you for your problem...

---

### Post by Quackers on 2011-08-09
Welcome to UF
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

### Post by iamsuperuser on 2011-08-10
Hi Quaker ! First of all I would really really wanted to thank you for your kind help !! Appreciate that a lot !!
Below is the content of my result.txt Please have a look. Or mebe you can point out which section is considered important coz I really don't understand the content..

----------------------------------------------------------------------------------------------------------------------------------
**                                                                               RESULT.TXT**
----------------------------------------------------------------------------------------------------------------------------------
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30560 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdc2 
                       and looks at sector 951339181 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos2)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   310,456,124   310,454,077   7 NTFS / exFAT / HPFS
/dev/sda2         310,472,190   312,576,704     2,104,515   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.0 GB, 16013852672 bytes
78 heads, 13 sectors/track, 30845 cylinders, total 31277056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064    31,277,055    31,268,992   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders, total 975400960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1           1,156,680   944,686,259   943,529,580   7 NTFS / exFAT / HPFS
/dev/sdc2    *    945,473,445   973,362,284    27,888,840  83 Linux
/dev/sdc4         973,363,200   975,398,911     2,035,712  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        3C1F-3C73                              vfat       PENDRIVE
/dev/sdc1        325220A852207331                       ntfs       chzeehau-hd
/dev/sdc2        9ee0ba34-f0e5-469e-946a-ef9bb5bc7465   ext3       
/dev/sdc4        e5f35f81-acf1-40fc-9c3b-27d64d2a971b   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/chzeehau-hd       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc2        /media/9ee0ba34-f0e5-469e-946a-ef9bb5bc7465 ext3       (rw,nosuid,nodev,uhelper=udisks)


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

=========================== sdc2/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdc,msdos2)'
search --no-floppy --fs-uuid --set=root 9ee0ba34-f0e5-469e-946a-ef9bb5bc7465
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos2)'
search --no-floppy --fs-uuid --set=root 9ee0ba34-f0e5-469e-946a-ef9bb5bc7465
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 9ee0ba34-f0e5-469e-946a-ef9bb5bc7465
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9ee0ba34-f0e5-469e-946a-ef9bb5bc7465 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 9ee0ba34-f0e5-469e-946a-ef9bb5bc7465
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9ee0ba34-f0e5-469e-946a-ef9bb5bc7465 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 9ee0ba34-f0e5-469e-946a-ef9bb5bc7465
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 9ee0ba34-f0e5-469e-946a-ef9bb5bc7465
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sdc2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc2       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdc4 during installation
UUID=e5f35f81-acf1-40fc-9c3b-27d64d2a971b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 453.633898258 = 487.085689344  boot/grub/core.img                             1
 453.704161167 = 487.161133568  boot/grub/grub.cfg                             1
 453.631494999 = 487.083108864  boot/initrd.img-2.6.38-8-generic               6
 453.617655277 = 487.068248576  boot/vmlinuz-2.6.38-8-generic                  3
 453.631494999 = 487.083108864  initrd.img                                     6
 453.617655277 = 487.068248576  vmlinuz                                        3

=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
unlzma: Decoder error


```

---

### Post by Quackers on 2011-08-11
Sorry iamsuperuser, I missed your reply.

Ok, in your computer's bios which drive is set to boot first?
Normally it should be something like this
USB flash drive
Internal cd drive
Internal hard drive (HDD)

In your case you should change it to this (or similar)
USB flash drive
Internal cd drive
External or USB HDD
Internal HDD (your installed hard drive)

Note
This is so the external hard drive (when it's plugged in) boots before your internal hard drive.
You should also check in your bios to see if there is a setting for "large drives" or LBA. If so please enable that.

I would also point out that your sda drive is not showing mountable partitions. What's on that drive?

---

### Post by iamsuperuser on 2011-08-11
Hi Quackers, Thanks for the quick reply !

I'm aware of the boot sequence. I'm booted using Ubuntu live in USB pendrive. 
My internal Harddisk not usable. that's y i desperately need to boot from ext HD.

Is there any problem with my boot partition in my ext HD?

---

### Post by Quackers on 2011-08-11
I don't see anything wrong.
If your USB HDD is set to boot before your internal hard drive in your bios then it all looks fine.
The only thing I notice is that all your grub files are late in the disc. Some bioses have a maximum read capability of 137GB and will therefore not find boot files which are on the disc after that limit.
If that is the case in your system, your bios will report that all connected drives are 137GB in size (iirc) and there is likely to be a "large drives" or "LBA" switch, or similar, to enable the reading of larger drives.
Sometimes it is necessary to update the bios to get this option, but this is only with quite old systems.

If you are sure that your 500GB drive is set to boot before your 160GB drive in the bios you can try re-installing grub to the mbr of the drive, but I'm not sure how successful that will be.
The commands are as follows for your system using the terminal in the live cd/usb desktop.
```
sudo mount /dev/sdc2 /mnt  
sudo grub-install --root-directory=/mnt /dev/sdc
``` This should report as successful with no errors. If it does, reboot and try again.

Sadly I have to go out now and will be out most of the night. Hopefully others will see your predicament and give assistance, if necessary.
I will look back later.
Good luck to you :-)

---

### Post by iamsuperuser on 2011-08-14
Quackers, sadly to tell you that I'm still getting the same error. :(
I hate my Western Digital Ext Hard drive... I notice that there's a virtual cd-rom in the ext hd partition. does it matter?

---

