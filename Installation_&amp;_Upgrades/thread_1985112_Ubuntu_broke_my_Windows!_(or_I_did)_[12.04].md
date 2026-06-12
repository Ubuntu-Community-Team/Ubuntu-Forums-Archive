---
title: "Ubuntu broke my Windows! (or I did) [12.04]"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by Inorien on 2012-05-22
Hey all, first post woo.

I tried to install Ubuntu on my Toshiba Satellite P750 (I believe that is the model number). The laptop uses 64bit and came preloaded with Windows 7. 
After a quick google search I was referred to a page on lifehacker on a beginners install guide for Linux - great! I chose Ubuntu, came to the site and downloaded it before burning it to a disk and throwing it in the laptop (I did the downloading on my Desktop computer, by the way) and booting from CD. 
First problem: It didn't boot from CD and went straight to Windows.
Not so much of a hassle, I have a new coaster now and I decided to try the USB method using a 4GB stick. I used the USB Install tool to get Ubuntu onto my USB stick after reformatting to Fat32, then plugged it into the laptop to give it a try.
Oh miracle! It boots into Ubuntu from the USB and gives me the option to try it out, which I gladly accept. I play around in the shiny new OS for a while before deciding I want to install Ubuntu on a partition - I run the Installer that was on the Desktop to install Ubuntu 12.04 and walked through the installation process to install Ubuntu alongside the existing Windows partition on the hard drive, and left it going after setting up my user account.

All seems to be going fine up to this point - the system reboots and I'm escorted into my brand new Ubuntu environment. At this point I start hitting little snags like the Wi-fi not working - apparently it's been switched off in Windows (some sudo command or other returned a "DISABLED" next to the adapter). TO WINDOWS!, I decided, oblivious to the doom that awaited.
I shut down the laptop and hit the power button to bring it back, to be greeted by GRUB (note that the USB pendrive was still plugged in). I choose to boot Windows 7 (/dev/sda2, interestingly /dev/sda1 aswell) and it starts to crank up the old Windows machine - and disaster strikes.
As the swirling coloured balls of light fly towards me, the screen freezes before flashing a BSoD (for literally a split-second, theres no way I could see the error message), and the system restarts. Damn, I think. Looks like I borked it already. Noticing the USB stick was still plugged in, I took it out and manually restarted the system - I get the Toshiba splash, followed immediately by the Windows loading animation, then the bluescreen at the same stage. There was no GRUB, nor was there any option for what OS I wanted to boot into. This is really bad - the system cannot boot without the USB pendrive, and even then, it can only load Ubuntu. However, I can see my files from my Windows partition from within Ubuntu.

IN SHORT: I can no longer load Windows without a bluescreen during the boot, with or without the USB pendrive. The only way to get action out of my laptop is by plugging in the pendrive, getting GRUB, then choosing Ubuntu. The system continues to operate fine when I unplug the USB pendrive, and I can access my personal files on my Windows partition from within Ubuntu.

Help please! I don't know much about the inner, dark workings of Ubuntu, and even less about partitioning drives (I sure look stupid now in hindsight). I want to be able to boot into Windows!

Many thanks for any and all help
-Inorien

---

### Post by wilee-nilee on 2012-05-22
Download this script in Ubuntu and run the command, paste all the text from the results.txt to a reply. When you open the reply hit the # in the reply panel and paste that text between the code tags.

Do you have a recovery or install disc for the windows, you probably need a chkdsk /f/r run at the least. 

This can be setup from a f8 prompt often as well.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by jadtech on 2012-05-22
after you  install ubuntu along side window  this shrinks the windows volume  you many times need to run chkdsk this will sort things out windows hates moving over  so to speak .. 

you might need win recovery disk to fix the MBR if windows still wont boot how ever many time if if you can hit f8 which ever your machine requres and do a chkdsk then recovery can usually be found as a selection there..

---

### Post by Inorien on 2012-05-23
Thanks for the fast reply, wilee-nilee. I ran the script, heres the contents of RESULTS.txt:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 55922e26-cce3-4a44-8788-dbc92710ae51 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 30478 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2           3,074,048   702,409,632   699,335,585   7 NTFS / exFAT / HPFS
/dev/sda3         702,410,750 1,219,160,063   516,749,314   5 Extended
/dev/sda5         702,410,752 1,202,573,311   500,162,560  83 Linux
/dev/sda6       1,202,575,360 1,219,160,063    16,584,704  82 Linux swap / Solaris
/dev/sda4       1,219,160,064 1,250,263,039    31,102,976  17 Hidden NTFS / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064     7,831,551     7,823,488   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        580093C10093A492                       ntfs       System
/dev/sda2        1658B92B58B90A8F                       ntfs       TI30798100A
/dev/sda4        C686DEBC86DEABE5                       ntfs       HDDRECOVERY
/dev/sda5        55922e26-cce3-4a44-8788-dbc92710ae51   ext4       
/dev/sda6        00b1225f-16ef-4ab2-83c3-c0ce2a22eee0   swap       
/dev/sdb1        1B05-2936                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 55922e26-cce3-4a44-8788-dbc92710ae51
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 55922e26-cce3-4a44-8788-dbc92710ae51
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
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
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 55922e26-cce3-4a44-8788-dbc92710ae51
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=55922e26-cce3-4a44-8788-dbc92710ae51 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 55922e26-cce3-4a44-8788-dbc92710ae51
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=55922e26-cce3-4a44-8788-dbc92710ae51 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 55922e26-cce3-4a44-8788-dbc92710ae51
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=55922e26-cce3-4a44-8788-dbc92710ae51 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 55922e26-cce3-4a44-8788-dbc92710ae51
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=55922e26-cce3-4a44-8788-dbc92710ae51 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 55922e26-cce3-4a44-8788-dbc92710ae51
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 55922e26-cce3-4a44-8788-dbc92710ae51
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 580093C10093A492
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 1658B92B58B90A8F
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root C686DEBC86DEABE5
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=55922e26-cce3-4a44-8788-dbc92710ae51 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=00b1225f-16ef-4ab2-83c3-c0ce2a22eee0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/initrd.img-3.2.0-24-generic               1
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

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
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e0 cf 1d 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 e0  cf 1d 00 18 fd 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/nick/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```I believe  I have the recovery disks, I'll try to get a chkdsk going now. Thanks for the help so far, guys

-Inorien

On second thought this probably belongs in the Beginner Support forums...


[UPDATE]!: I tried to run a chkdsk /f/r on the Windows partition (Powered on, GRUB, booted windows loader from sda1) and was given "The type of the file system is NTFS. Cannot lock the current drive. Windows cannot run disk checking on this volume because it is write protected." I can however run an ordinary chkdsk command and it returns "Windows has checked the file system and found no problems. [some information on KB use]... Failed to transfer logged messages to the event log with status 50."

---

### Post by wilee-nilee on 2012-05-23
So hard to say here really, grub could be loaded to the mbr for the ubuntu desktop with opening a terminal there and running.

```
sudo grub-install /dev/sda
```Then

```
sudo update-grub
```You would then have the grub menu without the usb flash plugged in, but this does not fix the windows set up. I see a full recovery set up on the HD, so lets call this a bump at the moment to get you back on the threads showing so others can take a look here and we can get some ideas.

Worse case here you can pull out what needs to be saved in windows and run a recovery probably.

Hard to say exactly what happened here, when I advise people to install I suggest that any windows partition be shrunk with the windows 7 virtual disk manager, this will do this on a live running set up then a reboot to make sure windows is all good.

This leaves a  unallocated space for Ubuntu to be installed in and rarely is there a problem.

I would not run the commands yet to load grub to the mbr yet, that is pretty easy in general, you can get to ubuntu now, I'm not sure you have a windows disc that will load its bootloader to the mbr at this point if needed.

---

### Post by Inorien on 2012-05-23
Thanks for the reply wilee-nilee

I ran the commands in Terminal (sudo: install-grub: command not found ; I had to use grub-install and that somehow worked) then update-grub, and it looks like it did something good.

I powered down the system and removed the USB pendrive, and it took me to grub just fine. Out of interest I tried launching Windows - and it worked! Successfully booted into Win7 on sda1. Hooray! 

The next challenge is making my Wi-fi work. If I'm not mistaken this is the real bloodbath problem for a lot of new users. I mentioned  in my original post that some command within Terminal returned my wireless card (Atheros AR9002WB-1NG Wireless Network Adapter) as being DISABLED - which a Google search revealed meant the hardware switch was off, or it was disabled in Windows. Well, my laptop doesn't have a hardware switch for the wireless card, and now I can boot into Windows, the only direction is forward. 
The Wireless adapter is Enabled under Windows Network Connections. However, upon booting into Ubuntu, it still reports that the network switch is off. Any idea what could be causing this one?

Many thanks for the help so  far
-Inorien

---

### Post by wilee-nilee on 2012-05-23
> **Inorien said:**
> Thanks for the reply wilee-nilee

I ran the commands in Terminal (sudo: install-grub: command not found ; I had to use grub-install and that somehow worked) then update-grub, and it looks like it did something good.

I powered down the system and removed the USB pendrive, and it took me to grub just fine. Out of interest I tried launching Windows - and it worked! Successfully booted into Win7 on sda1. Hooray! 

The next challenge is making my Wi-fi work. If I'm not mistaken this is the real bloodbath problem for a lot of new users. I mentioned  in my original post that some command within Terminal returned my wireless card (Atheros AR9002WB-1NG Wireless Network Adapter) as being DISABLED - which a Google search revealed meant the hardware switch was off, or it was disabled in Windows. Well, my laptop doesn't have a hardware switch for the wireless card, and now I can boot into Windows, the only direction is forward. 
The Wireless adapter is Enabled under Windows Network Connections. However, upon booting into Ubuntu, it still reports that the network switch is off. Any idea what could be causing this one?

Many thanks for the help so  far
-Inorien

Doh I had just gotten up, and reversed the command, but you figured it out anyway. Just proof of your tenacity and my need for coffee, glad it is working. :)

---

