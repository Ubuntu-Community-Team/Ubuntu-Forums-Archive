---
title: "Can't boot after upgrade from 10.04 to 10.10"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by surement on 2011-09-14
I did the upgrade from within Ubuntu by using the update manager. I'm using grub, and can still boot into Windows. I'm currently running Ubuntu from a USB live stick. Here is the output from boot_info_script.sh:

```

                                    Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda5 and looks at sector 172505636 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. According to the info in the boot 
                       sector, sda5 starts at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda6 and looks at sector 172473156 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. According to the info in the boot 
                       sector, sda6 starts at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 1904447 of /dev/sdc for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   145,966,589   145,966,527   7 NTFS / exFAT / HPFS
/dev/sda2         145,966,590   976,768,064   830,801,475   f W95 Extended (LBA)
/dev/sda5         210,933,513   919,239,299   708,305,787   7 NTFS / exFAT / HPFS
/dev/sda6         919,239,363   976,768,064    57,528,702   7 NTFS / exFAT / HPFS
/dev/sda7         145,966,716   210,933,449    64,966,734  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 3,840,820,199 3,840,820,137   7 NTFS / exFAT / HPFS
/dev/sdb2       3,840,820,200 3,902,252,759    61,432,560   5 Extended
/dev/sdb5       3,840,820,263 3,902,252,759    61,432,497   7 NTFS / exFAT / HPFS
/dev/sdb3       3,902,252,760 3,907,024,064     4,771,305  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A854D89C54D86E96                       ntfs       DRV1_VOL1
/dev/sda5        B268D9A368D9669F                       ntfs       DRV1_VOL2
/dev/sda6        E044DACB44DAA396                       ntfs       SAUVEGARDE
/dev/sda7        f1f92960-e4be-460c-9cfe-7db9a64a937a   ext3       Main
/dev/sdb1        2E947E77947E417F                       ntfs       2TB Main
/dev/sdb3        f9ad499c-8d65-4a6f-a8ba-00fdadd56396   swap       
/dev/sdb5        4EF5DAF47D18ED02                       ntfs       
/dev/sdc         64C4-8B83                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\windows 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\windows="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn /noguiboot 
--------------------------------------------------------------------------------

=========================== sda7/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set f1f92960-e4be-460c-9cfe-7db9a64a937a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set f1f92960-e4be-460c-9cfe-7db9a64a937a
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set f1f92960-e4be-460c-9cfe-7db9a64a937a
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=f1f92960-e4be-460c-9cfe-7db9a64a937a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set f1f92960-e4be-460c-9cfe-7db9a64a937a
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=f1f92960-e4be-460c-9cfe-7db9a64a937a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-11-rt' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set f1f92960-e4be-460c-9cfe-7db9a64a937a
    linux    /boot/vmlinuz-2.6.31-11-rt root=UUID=f1f92960-e4be-460c-9cfe-7db9a64a937a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-11-rt
}
menuentry 'Ubuntu, with Linux 2.6.31-11-rt (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set f1f92960-e4be-460c-9cfe-7db9a64a937a
    echo    'Loading Linux 2.6.31-11-rt ...'
    linux    /boot/vmlinuz-2.6.31-11-rt root=UUID=f1f92960-e4be-460c-9cfe-7db9a64a937a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-11-rt
}
menuentry 'Ubuntu, with Linux 2.6.31-9-rt' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set f1f92960-e4be-460c-9cfe-7db9a64a937a
    linux    /boot/vmlinuz-2.6.31-9-rt root=UUID=f1f92960-e4be-460c-9cfe-7db9a64a937a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-9-rt
}
menuentry 'Ubuntu, with Linux 2.6.31-9-rt (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set f1f92960-e4be-460c-9cfe-7db9a64a937a
    echo    'Loading Linux 2.6.31-9-rt ...'
    linux    /boot/vmlinuz-2.6.31-9-rt root=UUID=f1f92960-e4be-460c-9cfe-7db9a64a937a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-9-rt
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set f1f92960-e4be-460c-9cfe-7db9a64a937a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set f1f92960-e4be-460c-9cfe-7db9a64a937a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set A854D89C54D86E96
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=f1f92960-e4be-460c-9cfe-7db9a64a937a / ext3 errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=34c1f1cb-8bd0-4fc8-a25a-a119beec7e46 none swap sw 0 0
# /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_CA.UTF-8 0 0
/dev/sda5 /media/sda5 ntfs-3g defaults,locale=en_CA.UTF-8 0 0
/dev/sda6 /media/sda6 ntfs-3g defaults,locale=en_CA.UTF-8 0 0
/dev/sdb1 /media/sdb1 ntfs-3g defaults,locale=en_CA.UTF-8 0 0
# /dev/sdd1 /media/sdd1 vfat defaults,rw 0 0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  82.329618454 = 88.400754688   boot/grub/core.img                             2
  82.295076370 = 88.363665408   boot/grub/grub.cfg                             1
  82.276247025 = 88.343447552   boot/initrd.img-2.6.31-11-rt                   9
  82.351869583 = 88.424646656   boot/initrd.img-2.6.31-9-rt                    3
  82.295068741 = 88.363657216   boot/initrd.img-2.6.35-30-generic              5
  82.301427841 = 88.370485248   boot/vmlinuz-2.6.31-11-rt                      3
  82.238866806 = 88.303310848   boot/vmlinuz-2.6.31-9-rt                       2
  82.320405960 = 88.390862848   boot/vmlinuz-2.6.35-30-generic                 3
  82.295068741 = 88.363657216   initrd.img                                     5
  82.276247025 = 88.343447552   initrd.img.old                                 9
  82.320405960 = 88.390862848   vmlinuz                                        3
  82.301427841 = 88.370485248   vmlinuz.old                                    3

=========================== sdc/boot/grub/grub.cfg: ============================

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

========================== sdc/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

==================== sdc: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================== sdc: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

=============== sdc: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by kagz on 2011-09-14
since i can c u have ubuntu in the grub menu..please give the output when u select to boot from ubuntu...

---

### Post by surement on 2011-09-14
The screen goes black, then it says "Ubuntu" with 4 or 5 dots under it like it's loading, and then the screen just goes black (more of a pinkish black) and stays that way.

---

### Post by Basher101 on 2011-09-14
This looks more like a backlight issue. Do you have a flash light? try lighting your screen with it and see if that "pinkish" black is only your interface without backlight (you will be able to see some colors witht he flashlight) please confirm this.

---

### Post by coffeecat on 2011-09-14
I can see very little wrong with your boot script output, certainly nothing that obviously would prevent you from booting.

Your /etc/fstab references a now non-existent swap partition on sda, and the swap partition on sdb will not be mounted because there is no /etc/fstab line for it. At worst you would get an error message on bootup which you could bypass.

The other thing about your /etc/fstab is that four NTFS partitions are referenced with device names rather than UUIDs, but if there was a problem with this you would get an error message on bootup.

You're not really telling us much saying that you can't boot. What happens? Where does it get stuck? Do you get an error message? 

One thing you could try is to highlight the Ubuntu entry in the grub menu, press 'e' to edit the stanza and then remove "quiet splash" from the linux line. Then ctrl-X to boot and see what the text output shows just before the process gets stuck. That may give a clue.

Have you tried booting into one of the old kernels?

**EDIT**: I was typing as you posted so you've given us some more information now. Try removing quiet splash after you've tried Basher101's suggestion.

---

### Post by surement on 2011-09-14
Flashlight thing did nothing, the backlight is on, as opposed to when the screen is completely black. I loaded kernel 2.6.31-11 and I can boot, but the update manager is telling me to run a partial upgrade.

---

### Post by Basher101 on 2011-09-14
So its not a backlight problem...well since i do not use 10.10 i don't know where to search for the problem. Video Drivers maybe? Or rather, _*what*_ updates does the manager want you to install?

---

### Post by surement on 2011-09-14
It won't tell me unless I run a partial upgrade

---

### Post by Basher101 on 2011-09-14
Then i am sorry to say - i got nothin..
Maybe someone who had similar problems and solved them could help you.

-Regards

---

### Post by coffeecat on 2011-09-14
Open Synaptic Manager, click on Reload, then mark all upgrades and then apply. Don't OK the last, but see what or if it wants to install. If it's a long list, we can try this from the terminal to get more information.

---

### Post by Basher101 on 2011-09-14
Haven't though of synaptic...maybe cuz its midnight and i need sleep. I will go off then, good luck at solving this.

---

### Post by coffeecat on 2011-09-14
> **Basher101 said:**
> Haven't though of synaptic...maybe cuz its midnight and i need sleep. I will go off then, good luck at solving this.

Sleep well! :) I'm going to have to log off soon.

---

### Post by surement on 2011-09-14
There are 59 items; how do I do this from the terminal?

---

### Post by coffeecat on 2011-09-14
> **surement said:**
> There are 59 items; how do I do this from the terminal?

That's a lot. It sounds as though you had an incomplete upgrade for some reason. The kernel that is working is the 10.04 one, so it looks as though you might have some sort of hybrid system.

Before telling you how to do it from the terminal, let's check a few things. From a terminal:

```
cat /etc/lsb-release
```

If that tells you that you are running Maverick then that doesn't get us anywhere. If it says Lucid then definitely you have an incomplete upgrade.

Next, navigate to /etc/apt in a file browser. Right-click on sources.list and open in gedit. It will be read-only so you can't do any damage. Ignore all the lines beginning with a '#'. Do all the others have "maverick" in the line. If any have "lucid", then there's some repairing to do.

From the terminal, you would normally first do:

```
sudo apt-get update
```

But you've done that with the Synaptic reload. Now:

```
sudo apt-get -s dist-upgrade
```

The -s option does a simulation only. It tells you what it would do but doesn't go ahead. Highlight the output, right-click -> copy and paste that into your post.

---

### Post by surement on 2011-09-14
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  fglrx
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common cups-ppdc libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1
11 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Remv fglrx [2:8.780-0ubuntu2]
Inst libcups2 [1.4.4-6ubuntu2.3] (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Inst libcupscgi1 [1.4.4-6ubuntu2.3] (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Inst libcupsdriver1 [1.4.4-6ubuntu2.3] (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Inst libcupsimage2 [1.4.4-6ubuntu2.3] (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Inst libcupsmime1 [1.4.4-6ubuntu2.3] (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Inst libcupsppdc1 [1.4.4-6ubuntu2.3] (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Inst cups-common [1.4.4-6ubuntu2.3] (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [all])
Inst cups-bsd [1.4.4-6ubuntu2.3] (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64]) []
Inst cups-client [1.4.4-6ubuntu2.3] (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Inst cups-ppdc [1.4.4-6ubuntu2.3] (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Inst cups [1.4.4-6ubuntu2.3] (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Conf libcups2 (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Conf libcupscgi1 (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Conf libcupsdriver1 (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Conf libcupsimage2 (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Conf libcupsmime1 (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Conf libcupsppdc1 (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Conf cups-common (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [all])
Conf cups-client (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Conf cups-bsd (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Conf cups-ppdc (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])
Conf cups (1.4.4-6ubuntu2.4 Ubuntu:10.10/maverick-updates [amd64])

---

### Post by coffeecat on 2011-09-14
Bingo! I *think* I can see the problem:
> 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  [COLOR="Red"]fglrx[/COLOR]
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common cups-ppdc libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1
11 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.

... and so on.



All the cups stuff is probably a normal Maverick upgrade and is probably safe. But the fglrx driver could be the problem. You've possibly still got the old Lucid fglrx driver which is why you don't get the desktop with the Maverick kernel. Possibly.

If you let apt-get uninstall fglrx, you may be left with bits behind. My suggestion would be to completely uninstall the fglrx driver, see if you can boot into the Maverick kernel and then complete any possible upgrades. And only then consider re-installing the fglrx driver. I'll leave you with this link to read:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

It's probably best to do the "Problem: Need to fully remove -fglrx and reinstall -ati from scratch" section.

I have to log off now - very late here. I'll look in on this thread in the morning. If you want to delay until then, that's fine, but I will be back.

Good luck!

**EDIT**: for the record, post the output of:

```
lspci | grep VGA
```

... so that we can see exactly which graphics chipset you have.

---

### Post by surement on 2011-09-14
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]

---

### Post by surement on 2011-09-14
Ok I got it to work with a combination of your link to Radeon driver troubleshooting and [http://ubuntuforums.org/showthread.php?t=842114](http://ubuntuforums.org/showthread.php?t=842114)

Thank you so much, I would never have figured it out on my own!

---

### Post by socialsearch on 2011-09-15
i dont think that its a backlight problem.

---

### Post by coffeecat on 2011-09-15
> **surement said:**
> Ok I got it to work with a combination of your link to Radeon driver troubleshooting and [http://ubuntuforums.org/showthread.php?t=842114](http://ubuntuforums.org/showthread.php?t=842114)

Thank you so much, I would never have figured it out on my own!

That's a good find and I'm glad it worked.

Now that you're in a successfully upgraded Maverick (I hope!) using the open source ATI driver, you might want to see how you get on with that video driver before considering re-installing the proprietary fglrx one. I don't have experience of your particular Radeon HD 4850 card, but I have two machines with earlier 4*** series GPUs and the open source driver is more the adequate for my needs. See how you get on. My brief experiences of the fglrx driver have not been happy and it looks as though you've encountered another problem that it causes.

Good luck!

---

