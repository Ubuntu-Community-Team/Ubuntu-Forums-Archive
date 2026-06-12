---
title: "Windows 8.1 - cannot fix grub"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by nicoseb on 2013-10-26
Hi all,

I have a Gigabyte laptop that came with secure boot and windows 8. 
After a bit of battling, I managed to get my dual boot with Ubuntu 13.10..

Anyway, I upgraded zindows to 8.1, now grub is gone. 
I restarted from a live CD and chrooted to my drive. I used boot-repair multiple times (with successful output) both in default and with some advanced options; also reinstalled grub manually... Each time it tries once to boot to grub but gives a message for a very short amount of time. I recorded it and it is a regular bios message "Rebbot and Select proper Boot device of Insert Boot media in selected boot device and press a key"

I even tried something called EasyBCD under winblows, it shows the correct boot options, but same there, it is unable to make the linux partition fire up.

Anyway, no way to boot my linux box. Does anyone have an idea how to fix this? No need to redirect me to another post with grub reinstall or boot-repair, seen them all...
I am thinking of trying this other boot loader, refind, to see if it works [http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
Also re-reading this bios message, I'm thinking my partition might not have a boot flag anymore... I'll try that too with parted. Although both grub and win 8 are supposed to fire up from the same boot partition (the EFI one)

Please help! 
thx

---

### Post by LuvLinuxOS on 2013-10-26
Have you fdisk /mbr from window then tried restoring grub? Is grub installed to the mbr?  Is the grub.conf file pointing to the right partition for Ubuntu 13.10?  Just a few question to get your troubleshooting mind to start firing.  rEFInd seems to be a good tool but I would use it with caution as what ever custom setting you install will need to be redone on any rewriting of the MBR!!! I hope this helps.

[> ~LuvLinuxOS~]("http://luvlinuxos.blogspot.com")

---

### Post by fantab on 2013-10-26
Boot-Repair tool generates 'BootInfo Summary'. Post the link to BootInfo summary.

---

### Post by nicoseb on 2013-10-27
Thanks guys for the replies.
@luvlinux fdisk does not exist in windows 8 (not that I could tell anyway), and grub was not installed to the MBR.

Funny story though, I re-chrooter yet again. Before that I played around with boot flags (but reverted back everything), corrected a couple of bad blocks on my windows partition, and just did yet another boot-repair, actually 2, one after changing the live CD hostname to my normal hostname.
Everything went as it did before, but this time I was greeted with grub upon restart!!! I have no idea why it worked...
I redid a boot-repair upon restart to be really sure, and I even succesfully changed my grub to secure-boot!

@fantab, here is the bootinfo summary that was output right before grub finally worked. The only real difference I noticed was that at the end it said to make sure to boot from /dev/sda whereas it used to say /dev/sda2 before it worked.

What's less funny is tht the win 8.1 does not boot anymore complaining about a premature ending to it's boot file on the EFI partition... something else to google up!

```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 27Sep2013]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/grubx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /EFI/pro/Boot/bootmgfw.efi /EFI/pro/Boot/bootmgr.efi 
                       /EFI/pro/Boot/memtest.efi /bootmgr /boot/bcd

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Ubuntu 13.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: /dev/sda6 already mounted or /mnt/BootInfo/sda6 busy

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......c..9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1496144 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   250,069,679   250,069,679  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       616,447       614,400 Windows Recovery Environment (Windows)
/dev/sda2         616,448       821,247       204,800 EFI System partition
/dev/sda3         821,248     1,083,391       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,083,392   177,180,671   176,097,280 Data partition (Windows/Linux)
/dev/sda5     177,180,672   177,897,471       716,800 Windows Recovery Environment (Windows)
/dev/sda6     177,897,472   229,097,471    51,200,000 EFI System partition
/dev/sda7     229,097,472   250,068,991    20,971,520 Windows Recovery Environment (Windows)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2055 MB, 2055208960 bytes
36 heads, 35 sectors/track, 3185 cylinders, total 4014080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          1,520     4,014,079     4,012,560   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5E10224C10222B89                       ntfs       Windows RE tools
/dev/sda2        F624-4AF8                              vfat       SYSTEM
/dev/sda4        4490699290698AEE                       ntfs       WINDOWS
/dev/sda5        FE3CBE7A3CBE2D91                       ntfs       
/dev/sda6        a75d50a4-b759-46bb-b0e6-0f82fb14d1ab   ext4       
/dev/sda7        C2DC3661DC365041                       ntfs       Recovery image
/dev/sdb1        4CDC-D5AF                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6 --hint='hd0,gpt6'  a75d50a4-b759-46bb-b0e6-0f82fb14d1ab
else
  search --no-floppy --fs-uuid --set=root a75d50a4-b759-46bb-b0e6-0f82fb14d1ab
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a75d50a4-b759-46bb-b0e6-0f82fb14d1ab' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6 --hint='hd0,gpt6'  a75d50a4-b759-46bb-b0e6-0f82fb14d1ab
    else
      search --no-floppy --fs-uuid --set=root a75d50a4-b759-46bb-b0e6-0f82fb14d1ab
    fi
    linux    /boot/vmlinuz-3.11.4-031104-generic root=UUID=a75d50a4-b759-46bb-b0e6-0f82fb14d1ab ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.11.4-031104-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-a75d50a4-b759-46bb-b0e6-0f82fb14d1ab' {
    menuentry 'Ubuntu, with Linux 3.11.4-031104-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.4-031104-generic-advanced-a75d50a4-b759-46bb-b0e6-0f82fb14d1ab' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6 --hint='hd0,gpt6'  a75d50a4-b759-46bb-b0e6-0f82fb14d1ab
        else
          search --no-floppy --fs-uuid --set=root a75d50a4-b759-46bb-b0e6-0f82fb14d1ab
        fi
        echo    'Loading Linux 3.11.4-031104-generic ...'
        linux    /boot/vmlinuz-3.11.4-031104-generic root=UUID=a75d50a4-b759-46bb-b0e6-0f82fb14d1ab ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.4-031104-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.4-031104-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.4-031104-generic-recovery-a75d50a4-b759-46bb-b0e6-0f82fb14d1ab' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6 --hint='hd0,gpt6'  a75d50a4-b759-46bb-b0e6-0f82fb14d1ab
        else
          search --no-floppy --fs-uuid --set=root a75d50a4-b759-46bb-b0e6-0f82fb14d1ab
        fi
        echo    'Loading Linux 3.11.4-031104-generic ...'
        linux    /boot/vmlinuz-3.11.4-031104-generic root=UUID=a75d50a4-b759-46bb-b0e6-0f82fb14d1ab ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.4-031104-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-advanced-a75d50a4-b759-46bb-b0e6-0f82fb14d1ab' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6 --hint='hd0,gpt6'  a75d50a4-b759-46bb-b0e6-0f82fb14d1ab
        else
          search --no-floppy --fs-uuid --set=root a75d50a4-b759-46bb-b0e6-0f82fb14d1ab
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=a75d50a4-b759-46bb-b0e6-0f82fb14d1ab ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-12-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-recovery-a75d50a4-b759-46bb-b0e6-0f82fb14d1ab' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6 --hint='hd0,gpt6'  a75d50a4-b759-46bb-b0e6-0f82fb14d1ab
        else
          search --no-floppy --fs-uuid --set=root a75d50a4-b759-46bb-b0e6-0f82fb14d1ab
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=a75d50a4-b759-46bb-b0e6-0f82fb14d1ab ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-12-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root F624-4AF8
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root F624-4AF8
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "EFI/pro/Boot/bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root F624-4AF8
chainloader (${root})/EFI/pro/Boot/bootmgfw.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
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
# / was on /dev/sda5 during installation
UUID=a75d50a4-b759-46bb-b0e6-0f82fb14d1ab /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=F624-4AF8  /boot/efi       vfat    defaults        0       1
UUID=F624-4AF8    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


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

menuentry "Try Lubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Lubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/lubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/lubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
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
append initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Lubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Lubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper only-ubiquity  quiet splash --

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
menu label Try Lubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Lubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --

label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-R4T4pFI5/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-R4T4pFI5/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-R4T4pFI5/Tmp_Log: No such file or directory

ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-10-26__18h55 ===================
boot-repair version : 3.199~ppa31~raring
boot-sav version : 3.199~ppa31~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.199~ppa31~raring
boot-repair is executed in live-session (Ubuntu 13.10, saucy, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
mount: /dev/sdb1 already mounted or /mnt/boot-sav/sdb1 busy
mount /dev/sdb1 : Error code 32
mount -r /dev/sdb1 /mnt/boot-sav/sdb1
sudo: unable to resolve host lubuntu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="Windows RE tools" UUID="5E10224C10222B89" TYPE="ntfs"
/dev/sda2: LABEL="SYSTEM" UUID="F624-4AF8" TYPE="vfat"
/dev/sda4: LABEL="WINDOWS" UUID="4490699290698AEE" TYPE="ntfs"
/dev/sda5: UUID="FE3CBE7A3CBE2D91" TYPE="ntfs"
/dev/sda6: UUID="a75d50a4-b759-46bb-b0e6-0f82fb14d1ab" TYPE="ext4"
/dev/sda7: LABEL="Recovery image" UUID="C2DC3661DC365041" TYPE="ntfs"
/dev/sdb1: SEC_TYPE="msdos" UUID="4CDC-D5AF" TYPE="vfat"

Windows not detected by os-prober on sda4.
Linux not detected by os-prober on sda5. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Linux not detected by os-prober on sda6. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi

=================== //etc/grub.d/ :
drwxr-xr-x  2 root root      4096 Oct 26 17:52 grub.d
total 76
-rwxr-xr-x 1 root root  7850 Oct 10 13:48 00_header
-rwxr-xr-x 1 root root  5949 Aug 15 04:26 05_debian_theme
-rwxr-xr-x 1 root root 11479 Oct 10 13:48 10_linux
-rwxr-xr-x 1 root root 10258 Apr  9  2013 20_linux_xen
-rwxr-xr-x 1 root root  1798 Jun 17 05:52 20_memtest86+
-rwxr-xr-x 1 root root   452 Oct 26 17:52 25_custom
-rwxr-xr-x 1 root root 11531 Oct 10 13:48 30_os-prober
-rwxr-xr-x 1 root root  1426 Apr  9  2013 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  9  2013 40_custom
-rwxr-xr-x 1 root root   216 Apr  9  2013 41_custom
-rw-r--r-- 1 root root   483 Apr  9  2013 README




=================== //etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
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
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/boot/efi detected in the fstab of sda5: UUID=F624-4AF8     (sda2)

=================== sda6/etc/grub.d/ :
drwxr-xr-x  2 root root      4096 Oct 26 17:52 grub.d
total 76
-rwxr-xr-x 1 root root  7850 Oct 10 13:48 00_header
-rwxr-xr-x 1 root root  5949 Aug 15 04:26 05_debian_theme
-rwxr-xr-x 1 root root 11479 Oct 10 13:48 10_linux
-rwxr-xr-x 1 root root 10258 Apr  9  2013 20_linux_xen
-rwxr-xr-x 1 root root  1798 Jun 17 05:52 20_memtest86+
-rwxr-xr-x 1 root root   452 Oct 26 17:52 25_custom
-rwxr-xr-x 1 root root 11531 Oct 10 13:48 30_os-prober
-rwxr-xr-x 1 root root  1426 Apr  9  2013 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  9  2013 40_custom
-rwxr-xr-x 1 root root   216 Apr  9  2013 41_custom
-rw-r--r-- 1 root root   483 Apr  9  2013 README




=================== sda6/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
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
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/boot/efi detected in the fstab of sda6: UUID=F624-4AF8     (sda2)
=================== No kernel in /mnt/boot-sav/sdb1/boot:
grub



efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0000,0003,0004
Boot0000* Windows Boot Manager    HD(2,96800,32000,2b5036da-f913-4c0b-b68e-fc03fd6f4639)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...e................
Boot0003* ubuntu    HD(2,96800,32000,2b5036da-f913-4c0b-b68e-fc03fd6f4639)File(EFIUbuntugrubx64.efi)
Boot0004* UEFI: Generic Flash Disk 8.07    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(6,0)HD(1,5f0,3d3a10,576dc696)AMBO
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda4.
sda5    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /.
sda6    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.
sda7    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda7.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-kernel,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb1.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     liveusb,    no-os,    1520 sectors * 512 bytes


=================== parted -l:

Model: ATA M4-CT128M4SSD3 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
1      1049kB  316MB   315MB   ntfs         Basic data partition          hidden, diag
2      316MB   420MB   105MB   fat32        EFI system partition          boot
3      420MB   555MB   134MB                Microsoft reserved partition  msftres
4      555MB   90.7GB  90.2GB  ntfs                                       msftdata
5      90.7GB  91.1GB  367MB   ntfs                                       hidden, diag
6      91.1GB  117GB   26.2GB  ext4                                       boot
7      117GB   128GB   10.7GB  ntfs                                       diag


Model: Generic Flash Disk (scsi)
Disk /dev/sdb: 2055MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
1      778kB  2055MB  2054MB  primary  fat16        boot

=================== parted -lm:

BYT;
/dev/sda:128GB:scsi:512:512:gpt:ATA M4-CT128M4SSD3;
1:1049kB:316MB:315MB:ntfs:Basic data partition:hidden, diag;
2:316MB:420MB:105MB:fat32:EFI system partition:boot;
3:420MB:555MB:134MB::Microsoft reserved partition:msftres;
4:555MB:90.7GB:90.2GB:ntfs::msftdata;
5:90.7GB:91.1GB:367MB:ntfs::hidden, diag;
6:91.1GB:117GB:26.2GB:ext4::boot;
7:117GB:128GB:10.7GB:ntfs::diag;

BYT;
/dev/sdb:2055MB:scsi:512:512:msdos:Generic Flash Disk;
1:778kB:2055MB:2054MB:fat16::boot;


=================== mount:
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
none on /sys/fs/cgroup type tmpfs (rw,uid=0,gid=0,mode=0755,size=1024)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
none on /sys/fs/cgroup type tmpfs (rw,uid=0,gid=0,mode=0755,size=1024)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
none on /sys/fs/cgroup type tmpfs (rw,uid=0,gid=0,mode=0755,size=1024)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
none on /sys/fs/cgroup type tmpfs (rw,uid=0,gid=0,mode=0755,size=1024)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
none on /sys/fs/cgroup type tmpfs (rw,uid=0,gid=0,mode=0755,size=1024)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
none on /sys/fs/cgroup type tmpfs (rw,uid=0,gid=0,mode=0755,size=1024)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
none on /sys/fs/cgroup type tmpfs (rw,uid=0,gid=0,mode=0755,size=1024)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type vfat (rw)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type ext4 (rw)
/dev/sda7 on /mnt/boot-sav/sda7 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type vfat (ro)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uinput urandom v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  f8 5f 09 00 00 00 00 00  |........._......|
00000030  00 64 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.d..............|
00000040  f6 00 00 00 01 00 00 00  89 2b 22 10 4c 22 10 5e  |.........+".L".^|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200
ls /mnt/boot-sav/sda2/2:
ls /mnt/boot-sav/sda2: Boot
bootmgr
BOOTNXT
BOOTSECT.BAK
EFI
FSCK0000.REC
FSCK0001.REC
FSCK0002.REC
Temp  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 09 00  |........?....h..|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 f8 4a 24 f6 4e  4f 20 4e 41 4d 45 20 20  |..).J$.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 88 10 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 07 7f 0a 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  ee 8a 69 90 92 69 90 44  |..........i..i.D|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 90 8f 0a  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff ef 0a 00 00 00 00 00  |................|
00000030  aa 74 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.t..............|
00000040  f6 00 00 00 01 00 00 00  91 2d be 3c 7a be 3c fe  |.........-.<z.<.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda7
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 c0 a7 0d  |........?.......|
00000020  00 00 00 00 80 00 80 00  f8 ff 3f 01 00 00 00 00  |..........?.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  41 50 36 dc 61 36 dc c2  |........AP6.a6..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 06 00  |.X.SYSLINUX..@..|
00000010  02 00 02 00 00 f8 f5 00  3f 00 ff 00 f0 05 00 00  |........?.......|
00000020  10 3a 3d 00 00 01 29 af  d5 dc 4c 4e 4f 20 4e 41  |.:=...)...LNO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc f0 7b 8e d9 b8  00 20 8e c0 fc bd 00 7c  |....{.... .....||
00000050  38 4e 24 7d 24 8b c1 99  e8 3c fa fc 31 c9 8e d1  |8N$}$....<..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP....U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 50  d4 16 00 66 ba 00 00 00  |..E}.f.P...f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
df: '/run/user': No such file or directory
df: '/sys/fs/pstore': No such file or directory
df: '/sys/fs/cgroup/systemd': No such file or directory
df: '/sys/fs/cgroup/systemd': No such file or directory
df: '/sys/fs/cgroup/systemd': No such file or directory
df: '/sys/fs/cgroup/systemd': No such file or directory
df: '/sys/fs/cgroup/systemd': No such file or directory
df: '/sys/fs/cgroup/systemd': No such file or directory
df: '/sys/fs/cgroup/systemd': No such file or directory
df: '/sys/fs/cgroup/systemd': No such file or directory

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda5      ext4       24G   15G  8.1G  65% /
udev           devtmpfs  3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs      24G   15G  8.1G  65% /run
none           tmpfs      24G   15G  8.1G  65% /run/lock
none           tmpfs      24G   15G  8.1G  65% /run/shm
/dev/sda1      fuseblk   300M  218M   83M  73% /mnt/boot-sav/sda1
/dev/sda2      vfat       96M   67M   30M  70% /mnt/boot-sav/sda2
/dev/sda4      fuseblk    84G   78G  6.4G  93% /mnt/boot-sav/sda4
/dev/sda6      ext4       24G   15G  8.1G  65% /mnt/boot-sav/sda6
/dev/sda7      fuseblk    10G  6.5G  3.6G  65% /mnt/boot-sav/sda7
/dev/sdb1      vfat      2.0G  731M  1.2G  38% /mnt/boot-sav/sdb1

=================== fdisk -l:

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5a2a1f05

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   250069679   125034839+  ee  GPT

Disk /dev/sdb: 2055 MB, 2055208960 bytes
36 heads, 35 sectors/track, 3185 cylinders, total 4014080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x576dc696

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        1520     4014079     2006280    6  FAT16


EFI detected. Please check the options.

=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub-efi of sda5, using the following options:        sda2/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s    backup-and-rename-efi-files


sda5/boot/efi not empty
Mount sda2 on //boot/efi
ls //boot/efi/2:
ls //boot/efi: Boot
bootmgr
BOOTNXT
BOOTSECT.BAK
EFI
FSCK0000.REC
FSCK0001.REC
FSCK0002.REC
Temp  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
grub-install (GRUB) 2.00-19ubuntu2,grub-install (GRUB) 2.

chroot / efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0000,0003,0004
Boot0000* Windows Boot Manager    HD(2,96800,32000,2b5036da-f913-4c0b-b68e-fc03fd6f4639)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...e................
Boot0003* ubuntu    HD(2,96800,32000,2b5036da-f913-4c0b-b68e-fc03fd6f4639)File(EFIUbuntugrubx64.efi)
Boot0004* UEFI: Generic Flash Disk 8.07    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(6,0)HD(1,5f0,3d3a10,576dc696)AMBO

chroot / uname -r
Kernel: 3.8.0-19-generic
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes

Reinstall the grub-efi of sda5
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi : BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0000,0004
Boot0000* Windows Boot Manager
Boot0004* UEFI: Generic Flash Disk 8.07
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0001,0000,0004
Boot0000* Windows Boot Manager
Boot0004* UEFI: Generic Flash Disk 8.07
Boot0001* ubuntu
exit code of grub-install :0
mv 25_custom
ls //boot/efi/2:
ls //boot/efi: Boot
bootmgr
BOOTNXT
BOOTSECT.BAK
EFI
FSCK0000.REC
FSCK0001.REC
FSCK0002.REC
Temp  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
df /dev/sda2
Save and rename //boot/efi/EFI/Microsoft/Boot/bootmgfw.efi (//boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi)
cp //boot/efi/EFI/ubuntu/grubx64.efi //boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
df /dev/sda2
cp //boot/efi/EFI/ubuntu/grubx64.efi //boot/efi/EFI/Microsoft/Boot/bootx64.efi (& .grb)
df /dev/sda2
Save and rename //boot/efi/EFI/Boot/bootx64.efi (//boot/efi/EFI/Boot/bkpbootx64.efi)
cp //boot/efi/EFI/ubuntu/grubx64.efi //boot/efi/EFI/Boot/bootx64.efi
ls //boot/efi/2:
ls //boot/efi: Boot
bootmgr
BOOTNXT
BOOTSECT.BAK
EFI
FSCK0000.REC
FSCK0001.REC
FSCK0002.REC
Temp  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Add //boot/efi efi entries in //etc/grub.d/25_custom
Adding custom //boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
Adding custom //boot/efi/EFI/Boot/bkpbootx64.efi
sda2/bkpbootx64.efi already added
sda2/bkpbootmgfw.efi already added
Adding custom //boot/efi/EFI/pro/Boot/bootmgfw.efi
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi : BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0000,0004
Boot0000* Windows Boot Manager
Boot0004* UEFI: Generic Flash Disk 8.07
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0001,0000,0004
Boot0000* Windows Boot Manager
Boot0004* UEFI: Generic Flash Disk 8.07
Boot0001* ubuntu
exit code of grub-install :0

efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0001,0000,0004
Boot0000* Windows Boot Manager    HD(2,96800,32000,2b5036da-f913-4c0b-b68e-fc03fd6f4639)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...e................
Boot0001* ubuntu    HD(2,96800,32000,2b5036da-f913-4c0b-b68e-fc03fd6f4639)File(EFIubuntugrubx64.efi)
Boot0004* UEFI: Generic Flash Disk 8.07    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(6,0)HD(1,5f0,3d3a10,576dc696)AMBO

chroot / efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0001,0000,0004
Boot0000* Windows Boot Manager    HD(2,96800,32000,2b5036da-f913-4c0b-b68e-fc03fd6f4639)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...e................
Boot0001* ubuntu    HD(2,96800,32000,2b5036da-f913-4c0b-b68e-fc03fd6f4639)File(EFIubuntugrubx64.efi)
Boot0004* UEFI: Generic Flash Disk 8.07    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(6,0)HD(1,5f0,3d3a10,576dc696)AMBO

chroot / update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.4-031104-generic
Found initrd image: /boot/initrd.img-3.11.4-031104-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Adding boot menu entry for EFI firmware configuration
Unhide GRUB boot menu in sda5/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (128GB) disk!

```

---

### Post by oldfred on 2013-10-27
Added code tags and edited title to match Forum code of conduct.
[http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)

For some reason you are showing two efi partitions. Use gparted from liveCD and remove boot flag from second efi partition (sda6). That may confuse UEFI (or not) as it also is ext4 and UEFI cannot read it anyway.

Did you turn fast boot off after update, Windows likes to keep resetting things.

---

### Post by LuvLinuxOS on 2013-10-27
do you have an external hdd or flashdrive attached to your system???

[> ~LuvLinuxOS~]("http://luvlinuxos.blogspot.com")

---

### Post by nicoseb on 2013-11-02
Hi guys,

Sorry for the delay, I had a busy week... 
Anyway, thanks to you guys who replied and tried to help me out!
BTW sorry for the quote marks, I meant to put it in "code" mode...

Everything is working now :).
If someone else find this thread...
1) I booted using a lubuntu live-USB
2) I fixed grub using gparted and boot-repair. I even got grub with secure boot, which I did not use to have.

Please don't ask me how, as I said before it just magically reworked.
After that though, windows was dead.
I thought it was linked to this following bug 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)
But my issue was different, it said "end of premature file" for th windows EFI file.

3) I mounted the efi partition and looked at the file, no wonder it was dead, it was a 0 bytes file.
I re-run boot-repair with a bunch of options, tried the automated recovery of windows which would fail, try the bootfix {/MBR /BOOT /BCD} but nothgin did it.

4) I finally followed these commands:
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)
Now grub works with both lubunutu and win 8.1 in secure boot. :)

---

### Post by fantab on 2013-11-02
Good work. Glad you got your Dual-Boot going.

---

