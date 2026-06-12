---
title: "Grub does not see Fedora"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by Awes0meSauce on 2011-06-07
So close yet so far! OK, so the game plan was to multi boot Windows 7, Fedora 15, and Ubuntu 11.04. I attempted this before, and even got help from the this forum, but was still not able to get it all working. I have Windows 7 install on my first HDD. I just installed Fedora 15 on my second HDD a few hours ago. And just finished installing Ubuntu 11.04 on my third HDD a few minutes ago. Fedora installed fine and was able to see Windows 7. But when I installed Ubuntu, it again could see Windows but not see Fedora. I was hoping that by re-installing Fedora and Ubuntu, in that order, that Grub2 would overwrite Grub and be able to see both Windows and Fedora but no such luck. I again have ran the boot info script and here are my results this time:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
    the same hard drive for core.img. core.img is at this location and uses an
    embedded config file:
   
    ---------------------------------------------------------------------------
    search.fs_uuid 737daf8a-01ac-41ea-b731-8ae0dae72b75 root
    set
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub Legacy0.97-71.fc15 is installed in the MBR of /dev/sdb and looks at
    sector 30242 on boot drive #1 for the stage2 file.  A stage2 file is at
    this location on /dev/sdb.  Stage2 looks on partition #1 for
    /grub/grub.conf..
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of
    the same hard drive for core.img. core.img is at this location and looks
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System: 
    Boot files:        /grub/menu.lst /grub/grub.conf

sdb2: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files:       

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     1,026,047     1,024,000  83 Linux
/dev/sdb2           1,026,048   488,396,799   487,370,752  8e Linux LVM


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   593,531,893   593,531,831   b W95 FAT32
/dev/sdc2         593,532,926   976,771,071   383,238,146   5 Extended
/dev/sdc5         968,388,608   976,771,071     8,382,464  82 Linux swap / Solaris
/dev/sdc6         593,532,928   960,002,047   366,469,120  83 Linux
/dev/sdc7         960,004,096   968,382,463     8,378,368  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        CA447E3E447E2CF7                       ntfs      
/dev/sdb1        5349b4f2-1a1f-4be3-ad1b-5b49a49e2e94   ext4      
/dev/sdb2        t10ptO-1sTD-qRrh-iosA-fWdW-TPHY-37aMoH LVM2_member
/dev/sdc1        190B-2494                              vfat       STORAGE
/dev/sdc5        c0c69589-cd3c-4bc6-9f70-316d5035568c   swap      
/dev/sdc6        737daf8a-01ac-41ea-b731-8ae0dae72b75   ext4      
/dev/sdc7        6c83d44b-7eb6-403d-9b95-151b14e0a89b   swap      

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdc6        /                        ext4       (rw,errors=remount-ro,commit=0)


============================= sdb1/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd1,0)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_blackmesa-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=2
timeout=-1
splashimage=(hd1,0)/grub/splash.xpm.gz
#hiddenmenu
title Fedora (2.6.38.7-30.fc15.i686)
    root (hd1,0)
    kernel /vmlinuz-2.6.38.7-30.fc15.i686 ro root=/dev/mapper/vg_blackmesa-lv_root rd_LVM_LV=vg_blackmesa/lv_root rd_LVM_LV=vg_blackmesa/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.38.7-30.fc15.i686.img
title Fedora (2.6.38.6-26.rc1.fc15.i686)
    root (hd1,0)
    kernel /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=/dev/mapper/vg_blackmesa-lv_root rd_LVM_LV=vg_blackmesa/lv_root rd_LVM_LV=vg_blackmesa/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
title Windows 7
    rootnoverify (hd0,0)
    chainloader +1
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.016117096 = 0.017305600    grub/grub.conf                                 1
   0.016117096 = 0.017305600    grub/menu.lst                                  1
   0.014535904 = 0.015607808    grub/stage2                                    1
   0.031785011 = 0.034128896    initramfs-2.6.38.6-26.rc1.fc15.i686.img        2
   0.051061630 = 0.054827008    initramfs-2.6.38.7-30.fc15.i686.img            2
   0.012580872 = 0.013508608    vmlinuz-2.6.38.6-26.rc1.fc15.i686              1
   0.035770416 = 0.038408192    vmlinuz-2.6.38.7-30.fc15.i686                  1

=========================== sdc6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdc,msdos6)'
search --no-floppy --fs-uuid --set=root 737daf8a-01ac-41ea-b731-8ae0dae72b75
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos6)'
search --no-floppy --fs-uuid --set=root 737daf8a-01ac-41ea-b731-8ae0dae72b75
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
    set root='(/dev/sdc,msdos6)'
    search --no-floppy --fs-uuid --set=root 737daf8a-01ac-41ea-b731-8ae0dae72b75
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=737daf8a-01ac-41ea-b731-8ae0dae72b75 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos6)'
    search --no-floppy --fs-uuid --set=root 737daf8a-01ac-41ea-b731-8ae0dae72b75
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=737daf8a-01ac-41ea-b731-8ae0dae72b75 ro single
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
    set root='(/dev/sdc,msdos6)'
    search --no-floppy --fs-uuid --set=root 737daf8a-01ac-41ea-b731-8ae0dae72b75
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos6)'
    search --no-floppy --fs-uuid --set=root 737daf8a-01ac-41ea-b731-8ae0dae72b75
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root CA447E3E447E2CF7
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

=============================== sdc6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc7 during installation
UUID=6c83d44b-7eb6-403d-9b95-151b14e0a89b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 455.153095245 = 488.716914688  boot/grub/core.img                             1
 327.243598938 = 351.375138816  boot/grub/grub.cfg                             1
 285.397972107 = 306.443739136  boot/initrd.img-2.6.38-8-generic               2
 455.151371002 = 488.715063296  boot/vmlinuz-2.6.38-8-generic                  1
 285.397972107 = 306.443739136  initrd.img                                     2
 455.151371002 = 488.715063296  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2

00000000  0a 02 dc 02 f1 f1 d3 bc  bc bc f1 f1 d3 d3 bc bc  |................|
00000010  bc d3 d3 b2 bc bc f1 0d  0d 0d 0d e2 0d 0d f1 f1  |................|
00000020  dc dc dc dc dc dc dc dc  dc dc f1 f1 dc bc dc f1  |................|
00000030  f1 dc dc f1 dc dc dc 02  02 02 dc f1 02 02 02 a9  |................|
00000040  0a dc dc 02 f1 dc f1 f1  dc de dc dc dc 02 dc bc  |................|
00000050  bc f1 bc bc bc dc 02 02  0a 0a 02 dc f8 c0 dc 02  |................|
00000060  02 02 02 dc 02 02 02 02  02 dc dc dc dc dc f1 f1  |................|
00000070  dc dc 0d 0d 0d f1 0d bc  0d b2 b2 b2 b2 b2 33 c7  |..............3.|
00000080  c7 b2 b2 21 01 b2 c7 c7  c7 c7 0d bc c7 c7 b2 b2  |...!............|
00000090  f8 b2 c7 c7 b2 b2 21 21  21 21 21 21 b2 c7 01 c7  |......!!!!!!....|
000000a0  c7 c7 21 b2 21 09 09 09  21 21 21 21 21 21 21 09  |..!.!...!!!!!!!.|
000000b0  09 09 09 09 db 09 09 db  b6 c0 c8 db db db db db  |................|
000000c0  b9 b6 b9 db db 09 db db  b6 c8 bf c1 bf b9 b6 db  |................|
000000d0  fd fd b9 15 15 fd b6 09  fc 9f 21 21 09 01 21 09  |..........!!..!.|
000000e0  09 09 09 db 09 f8 db db  db db 09 db db db db 09  |................|
000000f0  09 09 db db db db 09 09  09 21 21 b2 21 21 21 21  |.........!!.!!!!|
00000100  21 b2 21 f8 f8 b2 b2 09  21 b2 21 f8 09 eb eb da  |!.!.....!.!.....|
00000110  ee da ec ec c0 eb eb f8  f8 f8 eb f8 eb da da da  |................|
00000120  ee ee c0 ec ec da db eb  f8 21 21 b2 b2 f8 f8 f8  |.........!!.....|
00000130  f8 f8 f8 f8 f8 21 21 b2  21 f8 f8 09 f8 eb da ec  |.....!!.!.......|
00000140  ec da ec ec ec ec 03 ec  ec ec ec cb a3 f7 a3 a3  |................|
00000150  a3 a3 f7 a3 aa a3 f7 f7  a3 a8 a3 a3 df f7 f7 f7  |................|
00000160  e9 f7 df 04 04 08 04 04  04 04 04 04 f7 04 df 04  |................|
00000170  04 04 04 f9 f7 df 04 04  04 04 04 04 04 04 04 0c  |................|
00000180  0c 0c 0e 0c 0c 0e 0e 0c  0e 0e 04 0c 04 04 f7 a8  |................|
00000190  a8 a8 a8 a8 a3 a3 a2 cc  eb c0 cb a3 e5 e5 e5 df  |................|
000001a0  f7 a3 69 ec db 21 c7 bc  dc 0d 21 01 c3 a1 f2 53  |..i..!....!....S|
000001b0  c6 31 57 c6 f2 34 c3 4d  c6 31 53 53 cf cf 00 fe  |.1W..4.M.1SS....|
000001c0  ff ff 82 fe ff ff 02 d8  57 16 00 e8 7f 00 00 fe  |........W.......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 e0 d7 15 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```After the install, I ran ```
sudo update-grub
``` and still could not boot into Fedora. Could someone please help me fix Grub so that it shows, and can boot all three? Thanks.

---

### Post by syoung27 on 2011-06-07
i noticed you have LVM, are you familiar with this?
i just removed Fedora 15 for Ubuntu 11.04 and am stuck with a stolen chunk of HDD.
sorry this isn't an answer but you're in similiar operating systems

---

### Post by oldfred on 2011-06-08
Do you see the os-prober processing the partitions. It normally finds the other installs grub.cfg, menu.lst or grub.conf and copies/reformats to grub2 the boot entry.

You can add a chainload entry to 40_custom. Entry may vary depending on whether you boot sda or sdc. 

gksudo gedit /etc/grub.d/40_custom
sudo update-grub

Entry:

menuentry "Fedora on sdb (from sdc) Chainboot" {
set root=(hd2)
chainloader +1
}

If booting from sda it may be hd1. Grub finds boot drive as hd0, then in order from sda, sdb, sdc. I sometimes have had to experiment with the number by using e on grub menu to edit number an see if it boots.

I have not tried a chain load with the new style using devices like set root='(/dev/sdc,msdos6)'

You may also be able to add full entries to 40_custom.
HowTo: add Fedora 15 to Maverick Grub 2
[http://ubuntuforums.org/showthread.php?t=1714170](http://ubuntuforums.org/showthread.php?t=1714170)
 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)

You should also install your grub2 boot loader to sdc. From Ubuntu:

sudo grub-install /dev/sdc

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by Awes0meSauce on 2011-06-08
> **syoung27 said:**
> i noticed you have LVM, are you familiar with this?
i just removed Fedora 15 for Ubuntu 11.04 and am stuck with a stolen chunk of HDD.
sorry this isn't an answer but you're in similiar operating systems
Not a clue! I just know Fedora set that up when I installed, gave some options for it, but I left everything default. 
> **oldfred said:**
> Do you see the os-prober processing the partitions. It normally finds the other installs grub.cfg, menu.lst or grub.conf and copies/reformats to grub2 the boot entry.

You can add a chainload entry to 40_custom. Entry may vary depending on whether you boot sda or sdc. 

gksudo gedit /etc/grub.d/40_custom
sudo update-grub

Entry:

menuentry "Fedora on sdb (from sdc) Chainboot" {
set root=(hd2)
chainloader +1
}

If booting from sda it may be hd1. Grub finds boot drive as hd0, then in order from sda, sdb, sdc. I sometimes have had to experiment with the number by using e on grub menu to edit number an see if it boots.

I have not tried a chain load with the new style using devices like set root='(/dev/sdc,msdos6)'

You may also be able to add full entries to 40_custom.
HowTo: add Fedora 15 to Maverick Grub 2
[http://ubuntuforums.org/showthread.php?t=1714170](http://ubuntuforums.org/showthread.php?t=1714170)
 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)

You should also install your grub2 boot loader to sdc. From Ubuntu:

sudo grub-install /dev/sdc

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc
Thank you, I'm eager to try this. Wish me luck!

---

### Post by Awes0meSauce on 2011-06-08
I tried [oldfred]("http://ubuntuforums.org/member.php?u=852711"). The entry did show up in Grub but when I selected it, it gave me:
```
error: unknown file system

grub rescue >
```Alright, so I want to start over. I want to delete all the Grubs installed. I want a fresh start. Is there any way to do this so that I can still boot into Windows but everything else is gone? Thank you so much.

---

### Post by drs305 on 2011-06-08
Your Windows boot files look okay. If you are currently running Ubuntu or are on the LiveCD this should point your MBR back to your Windows bootloader:
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Just run those two commands. You will get a message about needing to configure lilo, but just ignore it. Once you have run these two commands when you next boot you should see the normal Windows boot options.

Grub will still remain in the sdb and sdc MBR's so don't let your BIOS boot from either of those first, at least until you install another OS and Grub to them.

---

### Post by Awes0meSauce on 2011-06-08
Thanks **drs305**, it worked great. I guess this time I'll stick with a live CD until I understand a little more about Linux. Thank you everyone who helped me out. I'll get this one day.

---

### Post by Ni-el on 2011-06-08
Just a suggestion to make things easier?
Try Virtualbox (install from package manager). You can install and run any number of OS's within the main system without MBR's or partitions. You can run both at the same time and switch between them just like an application window. And if it doesn't work out just erase them and start over.

---

