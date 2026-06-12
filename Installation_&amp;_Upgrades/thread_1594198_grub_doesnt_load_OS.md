---
title: "grub doesnt load OS"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by rubencouto on 2010-10-12
Hello!
 
I have a dual boot (windows XP and Ubuntu). I just upgraded from Ubuntu 10.04 to 10.10 and I cant get it to load. Every time it boots I'm stuck on the grub> prompt. I run ls and get the following: (memdisk) (loop0) (hd0) (hd0,msdos1)
I thing (hd0) is my linux disk, but when I do root=(hd0,1) and run "root" command I get a message "file system is ntfs". I've tried to run vmlinuz and initrd.img but it says the file is not found... So, I'm stuck!
I wouldn't like to install ubuntu back again because I dont want to loose all my documents (if I havn't already...). Do you guys have any suggestions? Is there a safe way to get linux to load back up?
:(

---

### Post by Hyvi on 2010-10-12
Hi
> I thing (hd0) is my linux disk, but when I do root=(hd0,1) and run "root" command I get a message "file system is ntfs". 
are you sure that (hd0) is your linux disk  ? if you  are not sure ,you can try every patition.

---

### Post by thelugnut on 2010-10-12
Why don't you run "gparted" and check how your partitions are laid out?

You can run this program from the livecd.

---

### Post by Obrousse on 2010-10-12
I have a quite similar problem. I have Ubuntu 9.10 on a HP z800 workstation and it works fine but when I try to install a more recent Ubuntu grub is not able to load OS.

I just tried with Ubuntu 10.10 (as I did with 10.04 before). Grub is loaded and proposes me several options: Ubuntu 10.10 std and recovery, memtest, and my "old" Ubuntu with a couple of kernels 9.10 2.6.31.22 (std and recovery) and 2.6.31.14 (std and recovery). Ubuntu 9.10 is still loading and works fine I didn't tied memtest as I don't need it to work but Ubuntu 10.10 is not loading... When I select it (as I did before with 10.04) I have the screen that goes into sleep mode, hard drive is working a little then stop without any visible message or screen back on and the computer is not rebooting (or even booting the OS) until I press the case power button.

Do you have any idea of what is wrong between my computer and the 2 last versions of Ubuntu?

Regards,
Olivier.

---

### Post by Rubi1200 on 2010-10-12
@ rubencouto and @ Obrousse 

Use a LiveCD and post the results of the boot-script linked at the bottom of my post.

It will help us determine what is going on and make offering solutions easier.

Thanks.

---

### Post by Obrousse on 2010-10-12
Hello, thank you Rubi1200 for your quick answer.

Here are the results of "boot_info_script055.sh" launched using the Ubuntu 10.10 liveCD.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     1,050,623     1,048,576   6 FAT16
/dev/sda2    *      1,050,624   148,510,719   147,460,096  83 Linux
/dev/sda3         148,520,925   312,576,704   164,055,780  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   522,618,879   522,616,832  83 Linux
/dev/sdb2         522,618,880   625,141,759   102,522,880  83 Linux


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 255 MB, 255459328 bytes
8 heads, 32 sectors/track, 1949 cylinders, total 498944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1                 101       498,943       498,843   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        904B-2B03                              vfat                                     
/dev/sda2        e2d7945f-8f9c-48b3-ada7-cfbb717c4925   ext4                                     
/dev/sda3        79e6c001-e3fe-457e-b93c-b1671cee1ada   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        365b5753-cdb5-4ac5-8086-253ea7e93640   ext4                                     
/dev/sdb2        388238f5-27a9-4f5f-a1e6-2d35f4ad603e   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdh1        585A-364C                              vfat                                     
/dev/sdh: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdh1        /media/585A-364C         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set e2d7945f-8f9c-48b3-ada7-cfbb717c4925
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set e2d7945f-8f9c-48b3-ada7-cfbb717c4925
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=e2d7945f-8f9c-48b3-ada7-cfbb717c4925 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set e2d7945f-8f9c-48b3-ada7-cfbb717c4925
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=e2d7945f-8f9c-48b3-ada7-cfbb717c4925 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set e2d7945f-8f9c-48b3-ada7-cfbb717c4925
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e2d7945f-8f9c-48b3-ada7-cfbb717c4925 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set e2d7945f-8f9c-48b3-ada7-cfbb717c4925
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e2d7945f-8f9c-48b3-ada7-cfbb717c4925 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "FreeDOS (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 904b-2b03
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=e2d7945f-8f9c-48b3-ada7-cfbb717c4925 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=365b5753-cdb5-4ac5-8086-253ea7e93640 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=79e6c001-e3fe-457e-b93c-b1671cee1ada none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# montage du partage samba sur leadserv pour sauvegarde et synchronisation
//leadserv.u-bourgogne.fr/olivier /media/leadserv smbfs credentials=/home/olivier/.leadservCred,uid=olivier,gid=olivier,users    0    0

=================== sda2: Location of files loaded by Grub: ===================


   7.3GB: boot/grub/core.img
   6.2GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.31-14-generic
   2.3GB: boot/initrd.img-2.6.31-22-generic
    .7GB: boot/vmlinuz-2.6.31-14-generic
   2.2GB: boot/vmlinuz-2.6.31-22-generic
   2.3GB: initrd.img
    .7GB: initrd.img.old
   2.2GB: vmlinuz
    .7GB: vmlinuz.old

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 388238f5-27a9-4f5f-a1e6-2d35f4ad603e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 388238f5-27a9-4f5f-a1e6-2d35f4ad603e
set locale_dir=($root)/boot/grub/locale
set lang=fr
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 388238f5-27a9-4f5f-a1e6-2d35f4ad603e
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=388238f5-27a9-4f5f-a1e6-2d35f4ad603e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 388238f5-27a9-4f5f-a1e6-2d35f4ad603e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=388238f5-27a9-4f5f-a1e6-2d35f4ad603e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 388238f5-27a9-4f5f-a1e6-2d35f4ad603e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 388238f5-27a9-4f5f-a1e6-2d35f4ad603e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "FreeDOS (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 904b-2b03
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (on /dev/sda2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set e2d7945f-8f9c-48b3-ada7-cfbb717c4925
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=e2d7945f-8f9c-48b3-ada7-cfbb717c4925 ro quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode) (on /dev/sda2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set e2d7945f-8f9c-48b3-ada7-cfbb717c4925
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=e2d7945f-8f9c-48b3-ada7-cfbb717c4925 ro single
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set e2d7945f-8f9c-48b3-ada7-cfbb717c4925
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=e2d7945f-8f9c-48b3-ada7-cfbb717c4925 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set e2d7945f-8f9c-48b3-ada7-cfbb717c4925
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=e2d7945f-8f9c-48b3-ada7-cfbb717c4925 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=388238f5-27a9-4f5f-a1e6-2d35f4ad603e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=365b5753-cdb5-4ac5-8086-253ea7e93640 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=79e6c001-e3fe-457e-b93c-b1671cee1ada none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 312.8GB: boot/grub/core.img
 295.6GB: boot/grub/grub.cfg
 302.7GB: boot/initrd.img-2.6.35-22-generic
 312.8GB: boot/vmlinuz-2.6.35-22-generic
 302.7GB: initrd.img
 312.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 3c 90 46 52 44 4f 53  34 2e 31 00 02 10 08 00  |.<.FRDOS4.1.....|
00000010  02 00 02 00 00 f8 00 01  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 10 00 80 00 29 03  2b 4b 90 4e 4f 20 4e 41  |......).+K.NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa fc  |ME    FAT16   ..|
00000040  31 c0 8e d8 bd 00 7c b8  e0 1f 8e c0 89 ee 89 ef  |1.....|.........|
00000050  b9 00 01 f3 a5 ea 5e 7c  e0 1f 00 00 60 00 8e d8  |......^|....`...|
00000060  8e d0 8d 66 a0 fb 88 56  24 c7 46 c0 10 00 c7 46  |...f...V$.F....F|
00000070  c2 01 00 8c 5e c6 c7 46  c4 a0 63 8b 76 1c 8b 7e  |....^..F..c.v..~|
00000080  1e 03 76 0e 83 d7 00 89  76 d2 89 7e d4 8a 46 10  |..v.....v..~..F.|
00000090  98 f7 66 16 01 c6 11 d7  89 76 d6 89 7e d8 8b 5e  |..f......v..~..^|
000000a0  0b b1 05 d3 eb 8b 46 11  31 d2 f7 f3 50 01 c6 83  |......F.1...P...|
000000b0  d7 00 89 76 da 89 7e dc  8b 46 d6 8b 56 d8 5f c4  |...v..~..F..V._.|
000000c0  5e 5a e8 95 00 c4 7e 5a  b9 0b 00 be f1 7d 57 f3  |^Z....~Z.....}W.|
000000d0  a6 5f 26 8b 45 1a 74 0b  83 c7 20 26 80 3d 00 75  |._&.E.t... &.=.u|
000000e0  e7 72 65 50 c4 5e 5a 8b  7e 16 8b 46 d2 8b 56 d4  |.reP.^Z.~..F..V.|
000000f0  e8 67 00 58 1e 07 8e 5e  5c bf 00 20 ab 89 c6 8b  |.g.X...^\.. ....|
00000100  56 5c 01 f6 73 03 80 c6  10 8e da ad 3d f8 ff 72  |V\..s.......=..r|
00000110  eb 31 c0 ab 0e 1f c4 5e  5a be 00 20 ad 09 c0 75  |.1.....^Z.. ...u|
00000120  05 88 d3 ff 6e 5a 48 48  8b 7e 0d 81 e7 ff 00 f7  |....nZHH.~......|
00000130  e7 03 46 da 13 56 dc e8  20 00 eb e0 5e ac 56 b4  |..F..V.. ...^.V.|
00000140  0e cd 10 3c 2e 75 f5 c3  e8 f1 ff 45 72 72 6f 72  |...<.u.....Error|
00000150  21 2e 30 e4 cd 13 cd 16  cd 19 56 89 46 c8 89 56  |!.0.......V.F..V|
00000160  ca 8c 86 9e e7 89 9e 9c  e7 e8 d0 ff 2e b4 41 bb  |..............A.|
00000170  aa 55 8a 56 24 84 d2 74  19 cd 13 72 15 d1 e9 81  |.U.V$..t...r....|
00000180  db 54 aa 75 0d 8d 76 c0  89 5e cc 89 5e ce b4 42  |.T.u..v..^..^..B|
00000190  eb 26 8b 4e c8 8b 56 ca  8a 46 18 f6 66 1a 91 f7  |.&.N..V..F..f...|
000001a0  f1 92 f6 76 18 89 d1 88  c6 86 e9 d0 c9 d0 c9 08  |...v............|
000001b0  e1 41 c4 5e c4 b8 01 02  8a 56 24 cd 13 72 89 8b  |.A.^.....V$..r..|
000001c0  46 0b 57 be a0 63 c4 be  9c e7 89 c1 f3 a4 5f b1  |F.W..c........_.|
000001d0  04 d3 e8 01 86 9e e7 83  46 c8 01 83 56 ca 00 4f  |........F...V..O|
000001e0  75 8b c4 9e 9c e7 5e c3  00 00 00 00 00 00 00 00  |u.....^.........|
000001f0  00 4b 45 52 4e 45 4c 20  20 53 59 53 00 00 55 aa  |.KERNEL  SYS..U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 
```

I hope that someone will be kind enough to help me interpreting all those results...

Olivier.

---

### Post by Rubi1200 on 2010-10-12
@Obrousse

Have you tried running ```
sudo update-grub
``` in the terminal from 9.10?

What did you tell GRUB to do when you installed Maverick?

Why does it say you have Windows installed in the MBR of sdb?

---

### Post by Obrousse on 2010-10-12
> **Rubi1200 said:**
> 
Have you tried running ```
sudo update-grub
``` in the terminal from 9.10?

I will try it ASAP and keep you informed.

> **Rubi1200 said:**
> 
What did you tell GRUB to do when you installed Maverick?

I told nothing as I just followed the classical installation process. I just noticed that it installed grub on /dev/sda and verified this with the version showed at the next start up. All OS are there and only One is working.

> **Rubi1200 said:**
> 
Why does it say you have Windows installed in the MBR of sdb?
Just because there is a small partition called FreeDos that HP uses to store drivers and configurations (it is formatted in fat and grub offers the possibility to go for it.)

I'll keep you informed. Thank you for helping.
Olivier.

---

### Post by Obrousse on 2010-10-12
Here are the results of ```
sudo update-grub
``` under 9.10:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found FreeDOS on /dev/sda1
Found Ubuntu 10.10 (10.10) on /dev/sdb2
done
```

I will try to rebbot now hoping that 9.10 will still work :popcorn:

regards,
Olivier.

---

### Post by Rubi1200 on 2010-10-12
The results look normal and I believe you should be able to boot now into both 9.10 and 10.10

Good luck and let us know how it goes.

---

### Post by Obrousse on 2010-10-13
Hello,

I have a bad news...

The proposed procedure did not worked and the 10.10 is still not booting.

The good point is that I still have access to my 9.10.

I noticed a thing that didn't report previously when selecting the 9.10 the "underscore" blinks for 10 seconds approximately before the Ubuntu logo appears. In the case of the 10.10 the underscore is blinking only for 5 second maximum before the screen get no more signals. Is it of any help? I'm not sure but I have no other clues...

regards,
Olivier.

---

### Post by Obrousse on 2010-10-13
> **rubencouto said:**
> 
I thing (hd0) is my linux disk, but when I do root=(hd0,1) and run "root" command I get a message "file system is ntfs". I've tried to run vmlinuz and initrd.img but it says the file is not found... So, I'm stuck!

just a question did you try root=(hd0,0) or root=(hd0,2) maybe your drive as several Windows and Linux partitions and that you are looking at the wrong one?

> **rubencouto said:**
> 
I wouldn't like to install ubuntu back again because I dont want to loose all my documents (if I havn't already...). Do you guys have any suggestions? Is there a safe way to get linux to load back up?
:(

If you can boot through a live CD you can easily save your documents by mounting the partition where data are stored and a storage one then ```
cp orig save
``` your doc thanks to the live session.

---

### Post by Obrousse on 2010-10-14
Is there someone that can tell me how I can get boot log messages of my 10.10 installation in order to know what is going wrong?

I wander if the TESLA 1060 may be involved in this problem as it may be considered as vga board by the system but has no display function...

I will have to try that and keep inform the community.

Olivier.

---

### Post by Aetixintro on 2010-10-14
To the OP of this thread:
I think you have generated more than the allowance of 4 primary partitions (including the ext4). It appears that you have 3 harddisks (or some kind of disks, SCSI?).

You should check for your number of primary partitions and consult man-pages and such and in case it's necessary, adjust your primary partitions to 4 (using the Logical Partition widely) and I hope all will be good.

This is all I can say. (Is there Solaris in there too? Perhaps you should stick with only 2 OSs if not only to get your documents back, which is a dear thing, I agree!)

Cheers! :)

---

### Post by rubencouto on 2010-10-14
Hello!

I ended up reinstalling Ubuntu 10.04. I saved the file root.disk. How do I restore the files that it contains?

---

### Post by Obrousse on 2010-10-15
Maybe look if the ```
dd
``` command may help you as it is a low level copy utility. BUT I'm not sure that it is the solution or even a good idea.



I checked on my system with the Tesla unplugged and a new installation of Maverick and I must admit that I have done a mistake... My OS is booting I can ear the drum startup sound but I have not screen display. so the problem is not a grub one but more an interface one.

Sorry for the "polution" on this topic, my mistake.
Olivier.

---

### Post by Obrousse on 2010-10-15
As I found a solution to my problem, I just want to ad a link to it...

[http://ubuntu-tutorials.com/...-workaround/]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")

Once again sorry for the "polution".

Olivier.

---

