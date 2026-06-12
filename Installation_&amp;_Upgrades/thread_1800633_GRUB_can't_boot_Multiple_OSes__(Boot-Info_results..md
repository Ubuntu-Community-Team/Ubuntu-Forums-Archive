---
title: "GRUB can't boot Multiple OSes  (Boot-Info results.txt available)"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by wappiejones on 2011-07-09
Hi Everyone,

I need help to boot all OSes on my PC.

The system came with Windows 7 installed.

After installing Ubuntu 11.04 (Natty) with Unity, I installed Xubuntu 11.04. All three OSes could be seen in the GRUB menu and I could boot any OS of choice.

Then I installed OpenSUSE 11.4. I suspect it installed legacy GRUB on the OpenSUSE root partition. Thereafter, I was not able to boot Ubuntu or Xubuntu.

I have now used a LiveCD (system rescue mode) to re-install GRUB on the MBR. However, I can only boot Win7 or Ubuntu. Can't access Xubuntu or OpenSUSE.

Thanks

The results of my boot-info file are as reproduced below:

```

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda1 has 
                       2457599 sectors, but according to the info from fdisk, 
                       it has 2457881 sectors.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda3 and looks at sector 443784870 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #9 
                       for /boot/grub/menu.lst.

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unbekannter Dateisystemtyp &#8222;&#8220;

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.4 
                       "Celadon" - Kernel ().
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Platte /dev/sda: 320.1 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spur, 38913 Zylinder, zusammen 625142448 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63     2,457,944     2,457,882   7 NTFS / exFAT / HPFS
/dev/sda2           2,457,945   234,516,479   232,058,535   7 NTFS / exFAT / HPFS
/dev/sda3    *    234,518,526   481,781,759   247,263,234   5 Extended
/dev/sda5         234,518,528   251,320,319    16,801,792  83 Linux
/dev/sda6         251,322,368   255,533,055     4,210,688  82 Linux swap / Solaris
/dev/sda7         255,535,104   423,307,263   167,772,160  83 Linux
/dev/sda8         423,309,312   443,492,351    20,183,040  83 Linux
/dev/sda9         443,506,518   461,659,904    18,153,387  83 Linux
/dev/sda10        461,660,160   481,781,759    20,121,600  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 4b6d8d58-2aee-4efa-8948-84b8bb5ff630   swap       
/dev/sda1        369E3B929E3B4A1F                       ntfs       SYSTEM_DRV
/dev/sda10       6cea43d6-5ea8-4e10-b413-44057b466904   ext4       
/dev/sda2        AAD43D92D43D61AD                       ntfs       Windows7_OS
/dev/sda5        a3f1c28a-9d9d-45bb-82d5-ecd2c2bc24ea   ext4       
/dev/sda7        668c29cd-0ff8-4e85-b2f1-0dd5a64bde50   ext4       
/dev/sda8        30371c5a-b0c6-4582-be47-c40a759ee119   ext4       
/dev/sda9        c92318b9-d5eb-4ac0-9314-c41318e376dd   ext4       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)


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
search --no-floppy --fs-uuid --set=root a3f1c28a-9d9d-45bb-82d5-ecd2c2bc24ea
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root a3f1c28a-9d9d-45bb-82d5-ecd2c2bc24ea
set locale_dir=($root)/boot/grub/locale
set lang=de_DE
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
menuentry 'Ubuntu, mit Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root a3f1c28a-9d9d-45bb-82d5-ecd2c2bc24ea
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=a3f1c28a-9d9d-45bb-82d5-ecd2c2bc24ea ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, mit Linux 2.6.38-8-generic-pae (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root a3f1c28a-9d9d-45bb-82d5-ecd2c2bc24ea
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=a3f1c28a-9d9d-45bb-82d5-ecd2c2bc24ea ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root a3f1c28a-9d9d-45bb-82d5-ecd2c2bc24ea
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root a3f1c28a-9d9d-45bb-82d5-ecd2c2bc24ea
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 369E3B929E3B4A1F
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root AAD43D92D43D61AD
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
# / was on /dev/sda5 during installation
UUID=a3f1c28a-9d9d-45bb-82d5-ecd2c2bc24ea /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=668c29cd-0ff8-4e85-b2f1-0dd5a64bde50 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
#UUID=3136f60f-a0a0-49a4-b11e-b8c0ad97dc21 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 117.979022980 = 126.679011328  boot/grub/core.img                             1
 116.216609955 = 124.786634752  boot/grub/grub.cfg                             1
 114.590206146 = 123.040296960  boot/initrd.img-2.6.38-8-generic-pae           3
 112.964294434 = 121.294487552  boot/vmlinuz-2.6.38-8-generic-pae              2
 114.590206146 = 123.040296960  initrd.img                                     3
 112.964294434 = 121.294487552  vmlinuz                                        2

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos'
search --no-floppy --fs-uuid --set=root 30371c5a-b0c6-4582-be47-c40a759ee119
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 30371c5a-b0c6-4582-be47-c40a759ee119
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos'
    search --no-floppy --fs-uuid --set=root 30371c5a-b0c6-4582-be47-c40a759ee119
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=30371c5a-b0c6-4582-be47-c40a759ee119 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos'
    search --no-floppy --fs-uuid --set=root 30371c5a-b0c6-4582-be47-c40a759ee119
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=30371c5a-b0c6-4582-be47-c40a759ee119 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos'
    search --no-floppy --fs-uuid --set=root 30371c5a-b0c6-4582-be47-c40a759ee119
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos'
    search --no-floppy --fs-uuid --set=root 30371c5a-b0c6-4582-be47-c40a759ee119
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 369E3B929E3B4A1F
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root AAD43D92D43D61AD
    chainloader +1
}
menuentry "Ubuntu, mit Linux 2.6.38-8-generic-pae (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root a3f1c28a-9d9d-45bb-82d5-ecd2c2bc24ea
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=a3f1c28a-9d9d-45bb-82d5-ecd2c2bc24ea ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, mit Linux 2.6.38-8-generic-pae (Wiederherstellungsmodus) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root a3f1c28a-9d9d-45bb-82d5-ecd2c2bc24ea
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=a3f1c28a-9d9d-45bb-82d5-ecd2c2bc24ea ro single
    initrd /boot/initrd.img-2.6.38-8-generic-pae
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
UUID=30371c5a-b0c6-4582-be47-c40a759ee119 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=33e21faf-0999-4f7f-8f59-c2f01def06ef none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 208.121669769 = 223.468941312  boot/grub/core.img                             1
 204.241603851 = 219.302752256  boot/grub/grub.cfg                             1
 203.902866364 = 218.939035648  boot/initrd.img-2.6.38-8-generic-pae           2
 203.189880371 = 218.173472768  boot/vmlinuz-2.6.38-8-generic-pae              2
 203.902866364 = 218.939035648  initrd.img                                     2
 203.189880371 = 218.173472768  vmlinuz                                        2

=========================== sda9/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Modified by YaST2. Last modification on Thu Jul  7 14:02:16 CEST 2011
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.4 - 2.6.37.6-0.5
    root (hd0,
    kernel /boot/vmlinuz-2.6.37.6-0.5-default root=/dev/disk/by-id/ata-WDC_WD3200AAKX-083CA0_WD-WCAYUC414911-part9 splash=silent quiet showopts
    initrd /boot/initrd-2.6.37.6-0.5-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.4 - 2.6.37.6-0.5
    root (hd0,
    kernel /boot/vmlinuz-2.6.37.6-0.5-default root=/dev/disk/by-id/ata-WDC_WD3200AAKX-083CA0_WD-WCAYUC414911-part9 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe
    initrd /boot/initrd-2.6.37.6-0.5-default

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    rootnoverify (hd0,1)
    chainloader +1
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/disk/by-id/ata-WDC_WD3200AAKX-083CA0_WD-WCAYUC414911-part9 /                    ext4       acl,user_xattr        1 1
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 212.663691521 = 228.345900032  boot/grub/menu.lst                             1
 211.613211632 = 227.217955840  boot/grub/stage2                               1
 212.802832603 = 228.495301632  boot/initrd                                    2
 212.802832603 = 228.495301632  boot/initrd-2.6.37.6-0.5-default               2
 212.737524986 = 228.425178112  boot/vmlinuz                                   1
 212.737524986 = 228.425178112  boot/vmlinuz-2.6.37.6-0.5-default              1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by ajgreeny on 2011-07-09
The easiest way out of this problem is to restore grub2 from a live CD of ubuntu, or xubuntu, then boot back to ubuntu and run ```
sudo update-grub
```  Follow the instructions in the **Grub2 basics** link in my signature.

---

### Post by oldfred on 2011-07-09
Did you intentionally encrypt your swap? Normally each install will share the swaps but not sure with the encryption.

Your install in sda8 has a missing partition in its entry should be msdos[COLOR=Red]8[/COLOR]:
> set root='(/dev/sda,msdos'

Not sure if search line will then work ok or not. And if os-prober from install in sda5 will find the correct entry for sda8.

Your OpenSUSE installed its old grub legacy boot loader to the partition boot sector of the extended partition. Since the extended is a valid partition (just also a container for all the logicals), I guess that will work. Again not sure if os-prober will find that.

If os-prober does not work you can add a manual entry into 40_custom to chain load to it.

```
menuentry "OpenSUSE on sda Chainboot" {
set root=(hd0,3)
chainloader +1
}

```

Or a full entry like the one here, but you would have to edit with your UUID, drives, & versions.

[http://ubuntuforums.org/showthread.php?t=1740690](http://ubuntuforums.org/showthread.php?t=1740690)

---

### Post by wappiejones on 2011-07-10
@ajgreeny: Thanks. Just needed grub update as. Everything worked perfectly thereafter.

@oldfriend: At every mention of msdos in the results.txt file from bootinfo, there appeared a smiley after "msdos". Since a post couldn't have more than 8 images, I was compelled to delete these (or some of them) ;-)

Could the moderator pls tag the post as SOLVED.

Again, cheers!

wappiejones

---

### Post by Bucky Ball on 2011-07-10
> **wappiejones said:**
> 

Could the moderator pls tag the post as SOLVED.



You can do that from 'Thread Tools' at top right by clicking 'Mark thread as solved.' ;)

---

