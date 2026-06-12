---
title: "GRUB ERROR: Win7+Win2008server+Ubuntu10.04.1LTS+swap"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by proci on 2010-09-27
Hi Ubuntu users,
 
After installing Win7Enterprise + Win2008ServDatacenter + Ubuntu9.04 + swap, everything worked perfectly. Any Operating System runs fine. Grub did its job.
 
I decided to install Ubuntu 10.04.1 LTS + swap on the Ubuntu 9.04 + swap, turning the ext3 partition to a ext4 partition. The installation finished without errors, everything looked fine. At the end, the message saying that the installation finished, and my computer reboots. Then chaos appears. 
 
When my computer restarted, the exact message it gives after checking that there is no bootable CD is:
 
Verifying DMI Pool Data ..........
Boot from ATAPI CD-ROM: Failure ...
Boot from ATAPI CD-ROM: Failure ...
 
**error: out of disk.**
**grub rescue>**
 
Weird message "error: out of disk." And Grub starts with the prompt in rescue mode.

Gparted from the Ubuntu 9.10 LiveCD shows:
 
Screen capture:
[http://ubuntuforums.org/attachment.php?attachmentid=170646&stc=1&d=1285606759](http://ubuntuforums.org/attachment.php?attachmentid=170646&stc=1&d=1285606759)
 
Text (hardly formatted):
[FONT=Courier New]PARTITION FILE SYSTEM LABEL SIZE USED FLAGS[/FONT]
[FONT=Courier New]unallocated UNALLOCATED - 1MB - -[/FONT]
[FONT=Courier New]/dev/sda1/ NTFS RESERVED SYSTEM 100MB 33MB BOOT[/FONT]
[FONT=Courier New]/dev/sda2/ NTFS - 78GB 6GB -[/FONT]
[FONT=Courier New]/dev/sda3/ NTFS - 29GB 7GB -[/FONT]
[FONT=Courier New]/dev/sda4/ EXTENDED - 80GB - -[/FONT]
[FONT=Courier New]/dev/sda5/ EXT4 - 78GB 4GB -[/FONT]
[FONT=Courier New]unallocated UNALLOCATED - 1MB - -[/FONT]
[FONT=Courier New]/dev/sda6/ LINUX-SWAP - 1.5GB - -[/FONT]
 
It seems that this GRUB2 inside the new Ubuntu is not very refined.
 
Could anyone help me, please?
Thanks for your help in advance.
 
proci.

---

### Post by psusi on 2010-09-27
Please download and run the boot info script from the livecd and post the information it provides.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by proci on 2010-09-28
> **psusi said:**
> Please download and run the boot info script from the livecd and post the information it provides.
 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
 
Thanks psusi for your help. The RESULTS.txt file created by boot_info_script055.sh has the following content:
 
 
 
Boot Info Script 0.55 dated February 15th, 2010 
============================= Boot Info Summary: ==============================
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
partition #5 for /boot/grub.
sda1: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: /bootmgr /Boot/BCD
sda2: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /Windows/System32/winload.exe
sda3: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files/dirs: /Windows/System32/winload.exe
sda4: _________________________________________________________________________
File system: Extended Partition
Boot sector type: -
Boot sector info: 
sda5: _________________________________________________________________________
File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 10.04.1 LTS
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda6: _________________________________________________________________________
File system: swap
Boot sector type: -
Boot sector info: 
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disco /dev/sda: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros, 390721968 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
TamaÃ±o de sector (lÃ³gico / fÃsico): 512 bytes / 512 bytes
Partition Boot Start End Size Id System
/dev/sda1 * 2,048 206,847 204,800 7 HPFS/NTFS
/dev/sda2 206,848 163,842,047 163,635,200 7 HPFS/NTFS
/dev/sda3 163,842,048 225,282,047 61,440,000 7 HPFS/NTFS
/dev/sda4 225,284,094 390,721,535 165,437,442 5 Extended
/dev/sda5 225,284,096 387,391,487 162,107,392 83 Linux
/dev/sda6 387,393,536 390,721,535 3,328,000 82 Linux swap / Solaris
&#12288;
blkid -c /dev/null: ____________________________________________________________
Device UUID TYPE LABEL 
/dev/loop0 squashfs 
/dev/ramzswap0 swap 
/dev/sda1 5AACEB56ACEB2AE9 ntfs Reservado para el sistema 
/dev/sda2 3E7875C578757D09 ntfs 
/dev/sda3 109CDFC89CDFA70E ntfs 
/dev/sda4: PTTYPE="dos" 
/dev/sda5 c3a2e8c7-6a71-473a-83d7-11a54e3e4d5e ext4 
/dev/sda6 158c45d6-c0bc-49ba-8fdd-4dc997b8156d swap 
/dev/sda: PTTYPE="dos" 
============================ "mount | grep ^/dev output: ===========================
Device Mount_Point Type Options
aufs / aufs (rw)
/dev/sr1 /cdrom iso9660 (ro,noatime)
/dev/loop0 /rofs squashfs (ro,noatime)
&#12288;
=========================== sda5/boot/grub/grub.cfg: ===========================
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
set saved_entry=${prev_saved_entry}
save_env saved_entry
set prev_saved_entry=
save_env prev_saved_entry
set boot_once=true
fi
function savedefault {
if [ -z ${boot_once} ]; then
saved_entry=${chosen}
save_env saved_entry
fi
}
function recordfail {
set recordfail=1
if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c3a2e8c7-6a71-473a-83d7-11a54e3e4d5e
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
insmod gfxterm
insmod vbe
if terminal_output gfxterm ; then true ; else
# For backward compatibility with versions of terminal.mod that don't
# understand terminal_output
terminal gfxterm
fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c3a2e8c7-6a71-473a-83d7-11a54e3e4d5e
set locale_dir=($root)/boot/grub/locale
set lang=es
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, con Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c3a2e8c7-6a71-473a-83d7-11a54e3e4d5e
linux /boot/vmlinuz-2.6.32-24-generic root=UUID=c3a2e8c7-6a71-473a-83d7-11a54e3e4d5e ro quiet splash
initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-24-generic (modo recuperaciÃ³n)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c3a2e8c7-6a71-473a-83d7-11a54e3e4d5e
echo 'Cargando Linux 2.6.32-24-generic ...'
linux /boot/vmlinuz-2.6.32-24-generic root=UUID=c3a2e8c7-6a71-473a-83d7-11a54e3e4d5e ro single 
echo 'Cargando el disco RAM inicial...'
initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c3a2e8c7-6a71-473a-83d7-11a54e3e4d5e
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c3a2e8c7-6a71-473a-83d7-11a54e3e4d5e
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 5aaceb56aceb2ae9
chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
=============================== sda5/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
/dev/sda5 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=158c45d6-c0bc-49ba-8fdd-4dc997b8156d none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
=================== sda5: Location of files loaded by Grub: ===================
&#12288;
177.7GB: boot/grub/core.img
158.5GB: boot/grub/grub.cfg
177.7GB: boot/initrd.img-2.6.32-24-generic
177.7GB: boot/vmlinuz-2.6.32-24-generic
177.7GB: initrd.img
177.7GB: vmlinuz

---

