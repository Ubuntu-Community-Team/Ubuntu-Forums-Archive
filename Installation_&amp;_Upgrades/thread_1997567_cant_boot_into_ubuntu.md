---
title: "cant boot into ubuntu"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by akshayvadnere on 2012-06-05
i have installed ubuntu 12.04 64 bit for the 20 time now but still the grub bootloader doesnt show up and windows 7 gets automatically started. what should i do? this doesnt happen when i install ubuntu 11.10 or backtrack 5 r2. please help. i tried redownloading a fresh iso of ubuntu 2 times but the problem persists.

---

### Post by Bucky Ball on 2012-06-05
What happens when you boot from the CD and 'Try Ubuntu' rather than install? Does Ubuntu run ok from the CD?

---

### Post by akshayvadnere on 2012-06-05
'try ubuntu' works just fine.also the installation shows no errors. at the end it asks me restart pc and remove the installation media, after this the pc directly boots into windows 7.

---

### Post by darkod on 2012-06-05
Boot into live mode and use the boot info script from the link in my signature. Post the results as explained there. It will show more details.

One option is that grub2 from ubuntu ended up on another disk and you only need to change the order in bios (in case you have more than one hdd).

Another option is that grub2 didn't install at all, in which case you can simply reinstall it, without reinstalling the whole ubuntu (you said that didn't help anyway).

The results will show us what is best to be done.

---

### Post by akshayvadnere on 2012-06-05
how should i boot into live mode.

---

### Post by dino99 on 2012-06-05
> **akshayvadnere said:**
> how should i boot into live mode.

from livecd

---

### Post by Shadius on 2012-06-05
> **akshayvadnere said:**
> how should i boot into live mode.

Insert the Ubuntu LiveCD and select **Try Ubuntu**, then download and run the Boot Info Script. Post back the results here using the [CODE] tags or by pressing the # button on the toolbar of the message box.

---

### Post by akshayvadnere on 2012-06-05
i downloaded the boot info script and chose the option of 'run in terminal' window appeared and disappeared in a flash..how to use the boot info script, please help..

---

### Post by darkod on 2012-06-05
Open terminal yourself. Don't use right-click, Run in terminal.

Click the ubuntu logo, first button in the Unity interface on the left, and in the search line type terminal. It will show you the program, click on it to open.

Then, depending if the script is downloaded and extracted in your Home folder, execute it with:
sudo ./bootinfoscript

Or depending where is the extracted file, with:
sudo ./path/bootinfoscript

That will create results.txt file. Post the content as per the instructions.

---

### Post by akshayvadnere on 2012-06-06
this was in result file:

 ```
 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

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
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  BackTrack 5 R2 - Code Name 
                       Revolution 64 bit
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1628952 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648   413,515,775   413,104,128   7 NTFS / exFAT / HPFS
/dev/sda3         413,515,776 1,283,915,775   870,400,000   7 NTFS / exFAT / HPFS
/dev/sda4       1,283,917,822 1,465,147,391   181,229,570   5 Extended
/dev/sda5       1,283,917,824 1,322,977,279    39,059,456  83 Linux
/dev/sda6       1,322,979,328 1,465,147,391   142,168,064  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8103 MB, 8103395328 bytes
196 heads, 32 sectors/track, 2523 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    15,826,943    15,826,912   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        F04483F54483BD3A                       ntfs       
/dev/sda2        508A85828A8564F6                       ntfs       Windows
/dev/sda3        5CB6E77DB6E755D4                       ntfs       New Volume
/dev/sda5        bb7c0ca1-0e61-432b-9df8-ac0aad0bd805   ext4       
/dev/sda6        39e0041a-05ed-453f-8f6d-b7027646dfa6   ext4       
/dev/sdb1        A45D-CFE4                              vfat       AKSHAY

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set bb7c0ca1-0e61-432b-9df8-ac0aad0bd805
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  set gfxpayload=keep
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
search --no-floppy --fs-uuid --set bb7c0ca1-0e61-432b-9df8-ac0aad0bd805
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 3.2.6' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set bb7c0ca1-0e61-432b-9df8-ac0aad0bd805
    linux    /boot/vmlinuz-3.2.6 root=UUID=bb7c0ca1-0e61-432b-9df8-ac0aad0bd805 ro   text splash vga=791
    initrd    /boot/initrd.img-3.2.6
}
menuentry 'Ubuntu, with Linux 3.2.6 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set bb7c0ca1-0e61-432b-9df8-ac0aad0bd805
    echo    'Loading Linux 3.2.6 ...'
    linux    /boot/vmlinuz-3.2.6 root=UUID=bb7c0ca1-0e61-432b-9df8-ac0aad0bd805 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.6
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set bb7c0ca1-0e61-432b-9df8-ac0aad0bd805
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set bb7c0ca1-0e61-432b-9df8-ac0aad0bd805
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set F04483F54483BD3A
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
# / was on /dev/sda5 during installation
UUID=bb7c0ca1-0e61-432b-9df8-ac0aad0bd805 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrdf.img-3.2.6                         2
               =                boot/initrd.img-3.2.6                          2
               =                boot/initrds.img-3.2.6                         2
               =                boot/vmlinuz-3.2.6                             1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 39e0041a-05ed-453f-8f6d-b7027646dfa6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 39e0041a-05ed-453f-8f6d-b7027646dfa6
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 39e0041a-05ed-453f-8f6d-b7027646dfa6
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=39e0041a-05ed-453f-8f6d-b7027646dfa6 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 39e0041a-05ed-453f-8f6d-b7027646dfa6
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=39e0041a-05ed-453f-8f6d-b7027646dfa6 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 39e0041a-05ed-453f-8f6d-b7027646dfa6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 39e0041a-05ed-453f-8f6d-b7027646dfa6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root F04483F54483BD3A
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.2.6 (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root bb7c0ca1-0e61-432b-9df8-ac0aad0bd805
    linux /boot/vmlinuz-3.2.6 root=UUID=bb7c0ca1-0e61-432b-9df8-ac0aad0bd805 ro text splash vga=791
    initrd /boot/initrd.img-3.2.6
}
menuentry "Ubuntu, with Linux 3.2.6 (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root bb7c0ca1-0e61-432b-9df8-ac0aad0bd805
    linux /boot/vmlinuz-3.2.6 root=UUID=bb7c0ca1-0e61-432b-9df8-ac0aad0bd805 ro single
    initrd /boot/initrd.img-3.2.6
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=39e0041a-05ed-453f-8f6d-b7027646dfa6 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

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

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry6 
menu label Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry7 
menu label Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash -- 
 
label ubnentry8 
menu label Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash -- 
 
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

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
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
```

---

### Post by wilee-nilee on 2012-06-06
Boot that ubuntu cd open a terminal and copy and paste these command as they are and follow the directions.

```
sudo mount /dev/sda6 /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``````
apt-get purge grub-pc grub-common
```When asked here if you want to completely remove grub say yes
```
apt-get install grub-pc grub-common
```When asked here where you want grub tick sda only use the space key to do this.
```
grub-install --recheck /dev/sda
``````
update-grub
``````
Exit chroot: CTRL-D on keyboard
``````
sudo reboot
```Precise will be first on the boot menu and has grub control.

---

### Post by akshayvadnere on 2012-06-06
please reply. i have posted the script

---

### Post by darkod on 2012-06-06
You already have the reply. Follow the instructions wilee gave you to reinstall grub2. That should get it going. Right now the ubuntu grub2 didn't install completely.

If you are only checking your email for replies, some might be missing, visit the forum and you should see them all.

---

### Post by Bucky Ball on 2012-06-06
> **darkod said:**
> you already have the reply. Follow the instructions wilee gave you to reinstall grub2. 

+1.

---

### Post by akshayvadnere on 2012-06-06
After this step

apt-get purge grub-pc grub-commonit gives this message


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'grub-pc' can't be removed
E: Unable to locate package grub-common
root@ubuntu:/#

---

### Post by wilee-nilee on 2012-06-06
> **akshayvadnere said:**
> After this step

apt-get purge grub-pc grub-commonit gives this message


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'grub-pc' can't be removed
E: Unable to locate package grub-common
root@ubuntu:/#

So are you copying and pasting these commands exactly, one mistake and they will not work?

Don't try typing them is my advice.

---

### Post by akshayvadnere on 2012-06-06
i tried copying them, but still didnt work..again did the same thing by reinstalling ubuntu but same problem...i used the same cd to install ubuntu on my pc and it works just fine. only in my laptop this problem occurs. right now i m also using backtrack 5 r2 and the grub bootloader of backtrack is executed at beginning but there is no option for ubuntu 12.04

---

### Post by wilee-nilee on 2012-06-06
> **akshayvadnere said:**
> i tried copying them, but still didnt work..again did the same thing by reinstalling ubuntu but same problem...i used the same cd to install ubuntu on my pc and it works just fine. only in my laptop this problem occurs

I have a feeling you have a DRM issue lets use another tool to get the bootscript but a modified version that will show this sort of problem.

Use this tool the boot-repair app, just run the bootinfo summary, and post the HTTP address.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Also when you start saying reinstall, and include a reference to another  computer, **be exact in what you have done, when it was done and to what  computer**, otherwise we get to asking a lot of questions to confirm what  exactly has been done.

That section of your explanation could have multiple interpretations easily.

---

### Post by akshayvadnere on 2012-06-06
i'll try that new method. the steps i used were:
1. i selected something else option for installation.
2.i have a 70gb partition for ubuntu i formatted that drive and used / as mount point also i used extrn 4 format
3.for installing boot loader i selected the 1st option from drop down menu which shows me my entire hard disk size 750 gb. in the drop down menu i have one option in which it shows windows 7 and other shows ubuntu 10.04 which i guess is for backtrack.

---

### Post by wilee-nilee on 2012-06-06
> **akshayvadnere said:**
> i'll try that new method. the steps i used were:
1. i selected something else option for installation.
2.i have a 70gb partition for ubuntu i formatted that drive and used / as mount point also i used extrn 4 format
3.for installing boot loader i selected the 1st option from drop down menu which shows me my entire hard disk size 750 gb. in the drop down menu i have one option in which it shows windows 7 and other shows ubuntu 10.04 which i guess is for backtrack.

THanks that makes it a bit clearer. To be honest I'm not sure why the original commands did not work.

The Ubuntu install in sda6 is just missing this.
```
/boot/grub/core.img
```

I wonder if you just have a bad install, it does happen, but the secondary boot script may show information needed.

Not sure why you have installed backtrack as well it is made to be on a usb stick not a full install. It is rather useless as a full install really. As well it is for the serious geeks who know how to use it, personally I would not even try.

---

### Post by darkod on 2012-06-06
I would still try again with the chroot procedure. This time actually type the commands, the copy paste in terminal can also go wrong. And use separate mount commands instead of the long loop one.

That error message in post #15 mentioned virtual packages, not sure if that refers to live mode or not. Because if you tried that outside of the chroot, it would not have worked.

You need to boot with the cd in Try Ubuntu, open terminal and execute one by one all commands, without restarting the computer. When you restart, all changes done in the live session are lost and you have to start at the beginning again.

So, boot live mode, open terminal and try:
```
sudo mount /dev/sda6 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt

apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
grub-install /dev/sda
update-grub

exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

See if that helps.

---

### Post by akshayvadnere on 2012-06-06
this url was generated
[http://paste.ubuntu.com/1027435/](http://paste.ubuntu.com/1027435/)

---

### Post by wilee-nilee on 2012-06-06
> **darkod said:**
> I would still try again with the chroot procedure. This time actually type the commands, the copy paste in terminal can also go wrong. And use separate mount commands instead of the long loop one.

That error message in post #15 mentioned virtual packages, not sure if that refers to live mode or not. Because if you tried that outside of the chroot, it would not have worked.

You need to boot with the cd in Try Ubuntu, open terminal and execute one by one all commands, without restarting the computer. When you restart, all changes done in the live session are lost and you have to start at the beginning again.

So, boot live mode, open terminal and try:
```
sudo mount /dev/sda6 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt

apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
grub-install /dev/sda
update-grub

exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```See if that helps.

Good eye darkod, the very strange command that subs for these straight forward ones here has a virtual element to it.

OP I would try this.

---

### Post by akshayvadnere on 2012-06-06
this url was generated
[http://paste.ubuntu.com/1027435/](http://paste.ubuntu.com/1027435/)

---

### Post by darkod on 2012-06-06
After running the commands from post #21?

Those results look the same as the first ones.

On another note, since it looks like BT uses grub2 also, maybe all you need to do is boot BT and try to execute in terminal something like:
sudo update-grub

Not sure about BT but that's what you would use in ubuntu to detect a new OS. It should detect your new ubuntu installation, the only thing is what command do you need to run in BT to update grub2, whether it's the same as in ubuntu or not.

The procedure for installing grub2 from ubuntu should still work, but it's up to you. You can try simply updating BT's grub2.

---

### Post by wilee-nilee on 2012-06-06
> **darkod said:**
> After running the commands from post #21?

Those results look the same as the first ones.

On another note, since it looks like BT uses grub2 also, maybe all you need to do is boot BT and try to execute in terminal something like:
sudo update-grub

Not sure about BT but that's what you would use in ubuntu to detect a new OS. It should detect your new ubuntu installation, the only thing is what command do you need to run in BT to update grub2, whether it's the same as in ubuntu or not.

The procedure for installing grub2 from ubuntu should still work, but it's up to you. You can try simply updating BT's grub2.

I think that script was run before trying your commands, just in the time frame.

I missed the third script, so I am probably wrong here

---

### Post by darkod on 2012-06-06
> **wilee-nilee said:**
> I think that script was run before trying your commands, just in the time frame.

I missed the third script, so I am probably wrong here

Both links have same numbers. Both posts with links are for the same results. Not sure if it was run before trying post #21 though, I think so too.

---

### Post by Bucky Ball on 2012-06-06
> **darkod said:**
> 
On another note, since it looks like BT uses grub2 also, maybe all you need to do is boot BT and try to execute in terminal something like:
sudo update-grub



+1. This could just work. That means, of course, that Backtrack will now be running the show, re grub and therefore booting you machine, and that may not be desirable ...

Any changes you want to make to the grub will need to be made in Backtrack. ;)

---

### Post by akshayvadnere on 2012-06-07
so can anyone tell me how to update grub from backtrack..what about the url i posted about boot repair, did it show any errors?

---

### Post by wilee-nilee on 2012-06-07
> **akshayvadnere said:**
> so can anyone tell me how to update grub  from backtrack..what about the url i posted about boot repair, did it  show any errors?

From post 25
```
sudo update-grub
```Have you tried from the live cd darkods commands in post 21.

The comands I gave you originally were for a chroot into the ubuntu install the ones in 21 are as well but in a different command sequence.

The deal here is that this should be an easy fix, so we are a bit confused as to why my commands did not work, at least I am anyway.

try the ones in 21 if you have not yet from a live cd.

The last two scripts you posted were the same ones, they all look the same basically.

If you post a script explain what you did with the post.

---

### Post by akshayvadnere on 2012-06-07
ok. i'll try those commands too, can i also try the recommended repair option from boot repair disk?

---

### Post by wilee-nilee on 2012-06-07
> **akshayvadnere said:**
> ok. i'll try those commands too, can i also try the recommended repair option from boot repair disk?

The only one on the boot-reapir you would use is the purge, in advanced, which is exactly what we have been trying so far with my commands and darkods.

You could try if you want, it will give you commands to copy and paste.

---

### Post by akshayvadnere on 2012-06-07
this is what i got by darklod's command

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get remove --purge grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'grub-pc' can't be removed
E: Unable to locate package grub-common
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'grub-pc' has no installation candidate
root@ubuntu:/# grub-install /dev/sda
The program 'grub-install' can be found in the following packages:
 * grub
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-pc
 * lupin-support
 * grub-coreboot
 * grub-ieee1275
Try: apt-get install <selected package>
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'grub-pc' has no installation candidate
root@ubuntu:/# update-grub
The program 'update-grub' can be found in the following packages:
 * grub
 * grub2-common
Try: apt-get install <selected package>
root@ubuntu:/#

---

### Post by akshayvadnere on 2012-06-07
yippie!!!!!! ubuntu has finally started. i ran the boot repair disk in 64 bit session and it worked..thank you guys so much for your support aand help..although it shows me 3 errors at the beginning after selecting the ubuntu option from boot menu..but its working so i guess they wont be a problem..thank you all once again!!

---

### Post by Bucky Ball on 2012-06-09
Great news. Please mark thread as solved if it is. ;)

---

