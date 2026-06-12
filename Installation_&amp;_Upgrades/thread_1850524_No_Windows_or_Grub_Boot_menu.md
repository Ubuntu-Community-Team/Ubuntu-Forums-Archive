---
title: "No Windows or Grub Boot menu?"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by jordinf on 2011-09-26
When I start my machine ubuntu auto boots and I can force windows to boot with the start up manager but then I cant get ubuntu to boot again.......

How do I get a windows or grub startup screen?

I have installed it on a separate partion on the same drive as windows.

I have also tried to hold down or press Shift and still no boot menu at startup I fear if I use the startup manager to boot to windows I will not be able to force ubuntu to boot again at startup.

Also there is no "menu.lst" in boot/grub/

any ideas?

---

### Post by garvinrick4 on 2011-09-26
I do not use startup manager but boot into Ubuntu and run:  (kind of surprised if it show in the GUI tool it does not show in grub, let me know if anymore trouble after this below)
```
sudo update-grub
```That should put Windows in as a menu entry in grub2 (grub-pc)
There is no menu.list in grub2 that is in grub legacy not used by Ubuntu anymore
since 9.04 version.
From now on you can see boot menu entrys with in terminal
```
grep menuentry /boot/grub/grub.cfg
```if you choose.

If only one Operating system in config file (made by update-grub command) grub2 defaults
to not showing grub menu entrys and should be able to see it by holding down shift key during boot.

Link below to bookmark and read as your time permits
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

---

### Post by jordinf on 2011-09-26
Its not so much about putting it as a entry there is no entry at all my computer just boots from ubuntu I never get to select anything and i tried running the grub update.

I installed ubuntu by just clicking custom on the installation and selecting my new partion and installing it inside \   instead of installing it inside \boot or \home or installing beside windows. Did i do it wrong?

I tried 
grep menuentry /boot/grub/grub/cfg


and it says not valid command

---

### Post by garvinrick4 on 2011-09-26
> **jordinf said:**
> Its not so much about putting it as a entry there is no entry at all my computer just boots from ubuntu I never get to select anything and i tried running the grub update.

I installed ubuntu by just clicking custom on the installation and selecting my new partion and installing it inside \   instead of installing it inside \boot or \home or installing beside windows. Did i do it wrong?

I tried 
grep menuentry /boot/grub/grub/cfg


and it says not valid command Sorry had a typo I fixed it . intstead or / my mistake.

##If you want your boot info to be diagnosed have to run this script and post to your thread is long so after pasting to your message box highlight whole thing and  hit the # sign in upper right of message box and will put in nice box to  read from.
Download this script to[COLOR=Red] Desktop[/COLOR] and then run the code I give you below and will put the results in RESULTS file on your desktop.
Open with archive manager and extract script after download.
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") 
Now open a terminal and:
  	 	 	 	 	 	

 	```
sudo bash ~/Desktop/boot_info_script.sh
```

---

### Post by jordinf on 2011-09-26
deleted

---

### Post by jordinf on 2011-09-26
```
             Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

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
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 1927964952 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 16400 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    25,167,871    25,165,824  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     25,167,872    25,372,671       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          25,372,672 1,812,209,663 1,786,836,992   7 NTFS / exFAT / HPFS
/dev/sda4       1,812,211,710 1,953,521,663   141,309,954   f W95 Extended (LBA)
/dev/sda5       1,812,211,712 1,953,521,663   141,309,952  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8103 MB, 8103395328 bytes
255 heads, 63 sectors/track, 985 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    15,826,943    15,826,881   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        E664486F64484491                       ntfs       PQSERVICE
/dev/sda2        469849029848F24B                       ntfs       SYSTEM RESERVED
/dev/sda3        B0A84A95A84A59CC                       ntfs       eMachines
/dev/sda5        e2c4487c-e61f-4469-b837-e72205c199bf   ext3       
/dev/sdb1        3C5A-1CF3                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root e2c4487c-e61f-4469-b837-e72205c199bf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root e2c4487c-e61f-4469-b837-e72205c199bf
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e2c4487c-e61f-4469-b837-e72205c199bf
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=e2c4487c-e61f-4469-b837-e72205c199bf ro  splash  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e2c4487c-e61f-4469-b837-e72205c199bf
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=e2c4487c-e61f-4469-b837-e72205c199bf ro single  splash
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e2c4487c-e61f-4469-b837-e72205c199bf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e2c4487c-e61f-4469-b837-e72205c199bf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root E664486F64484491
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 469849029848F24B
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext3    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 919.325355530 = 987.118084096  boot/grub/core.img                             1
 920.083889008 = 987.932553216  boot/grub/grub.cfg                             1
 920.064136505 = 987.911344128  boot/initrd.img-2.6.38-8-generic               7
 919.149734497 = 986.929512448  boot/vmlinuz-2.6.38-8-generic                  3
 920.064136505 = 987.911344128  initrd.img                                     7
 919.149734497 = 986.929512448  vmlinuz                                        3

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

sdc sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
/home/matthew/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

Hope this helps you I could sure use it.....Id love to be able to boot up windows and linux on demand even if I have to change a command line or use terminal or cmd to do it.

---

### Post by garvinrick4 on 2011-09-26
Do you have your Windows disk?

---

### Post by garvinrick4 on 2011-09-26
```
gedit /etc/default/grub
```Does yours say as per below like mine?
[COLOR=Red]GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
[/COLOR]
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by jordinf on 2011-09-27
I do not have my windows disk

I cant even check my file I used startupmanger in linux to boot windows 7 and now when i start my machine it boots windows 7 only no screen.

is there a way to boot linux from cmd or something i cant even see the portioned drive to check the files.

---

### Post by garvinrick4 on 2011-09-27
If GRUB 2 determines the *SHIFT* key is depressed during the  boot process, the menu will be displayed. This gives the user a method  of interrupting an automatic boot which would normally not display the  menu.

---

### Post by jordinf on 2011-09-27
Ive tried that nothing happens at all

---

### Post by Hakunka-Matata on 2011-09-27
> From post# 1:  Also there is no "menu.lst" in boot/grub/menu.lst is no longer used in Grub 2, the current version of grub being installed.  

Grub got installed to the Linux System partition, sda5, that's not where we usually want it.  To fix that lets run "Purge and Reinstall":  Grub, that is.

[https://help.ubuntu.com/community/Grub2#Purge_.26_Reinstall](https://help.ubuntu.com/community/Grub2#Purge_.26_Reinstall)

Replace all /dev/sdYY commands with /dev/sda5

Don't do step 5., you don't have a separate boot partition.

after you've purged and reinstalled, reboot, then run ```
sudo update-grub
```I'd copy and paste the commands, rather than typing them in.

---

### Post by garvinrick4 on 2011-09-27
I just have a feeling there is a setting wrong in /etc/default/grub because he has access to all installs
in startup manager so must be in config file (which is in boot script) and as menu entrys. So does that mean he has disabled
the grub menu entry screen. (Both Ubuntu and Linux where booting but choosen in GUI app). Is most likely moot at this point because OP would have to chroot and 
look at it in nano to repair and save . Would be just as easy to use the Live Cd to purge all things grub
and reninstall as to make a new /etc/default/grub, config file than learn to use nano as mentioned in previous post by Hakuna Mattata lets purge and reinstall (I can put grub in a partition instead
of sda and then install in sda where belongs and all still works fine, just looks obtrusive in boot script in sda5 showing grub installed there also Hakuna, give it a try when bored someday.)
[COLOR=Red]
[COLOR=Black]@jordinf[/COLOR]

Make sure internet works in live cd[/COLOR] (install cd using Try Ubuntu) copy and paste these one at a time in a terminal of live cd or live USB)

```

sudo mount /dev/sda5 /mnt
``````
sudo mount -o bind /dev /mnt/dev; sudo mount -o bind /dev/pts /mnt/dev/pts; sudo mount -o bind /proc /mnt/proc; sudo mount -o bind /sys /mnt/sys
``````
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
``````
sudo chroot /mnt
``````
apt-get purge grub grub-common grub-pc
``````
apt-get install grub-common grub-pc
```Use tab key, enter and arrows and put in sda
```
grub-install /dev/sda
``````
update-grub
``````
exit
``````
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys; sudo umount /mnt

``````
sudo reboot
```#There is a few extra commands just to make sure you install in sda and not sda5 or sda1 but in sda.
Any way this is going to give new grub and config files and should cure what ails you.

Link for you to save:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

