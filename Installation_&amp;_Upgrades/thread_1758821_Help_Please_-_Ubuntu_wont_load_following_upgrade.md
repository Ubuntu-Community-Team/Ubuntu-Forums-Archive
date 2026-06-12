---
title: "Help Please - Ubuntu wont load following upgrade"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by me075064 on 2011-05-15
Hi all,

I've been dual booting Ubuntu and Windows 7 for a while and up until now Ubuntu has worked great for me.
Last night I performed the update to install the lastest version of the Ubuntu which appeared to go ok, but following the restart Ubuntu no longer loads. (Screen shot attached [ATTACH]192209[/ATTACH])
When I choose a previous version of Ubuntu from a sub menu of the boot menu it appears to load fine - and has a new interface, and Windows 7 still loads.
Can anyone help me fix my system?

Many thanks 
John M

---

### Post by wilee-nilee on 2011-05-15
That is unreadable remove the screenshot and upload it with the paper clip in the reply window.

---

### Post by Hedgehog1 on 2011-05-15
It is hanging at 'checking battery state' as far as I can tell from the photo.

***The Hedge***

:KS

---

### Post by me075064 on 2011-05-15
Sorry about the image - I've now attached it via the paperclip

---

### Post by Rubi1200 on 2011-05-15
Hi and welcome to the forums me075064 :-)

What graphics card and how much RAM is installed?

Please post the results of the boot info script from a LiveCD/USB.

There is a link at the bottom of my post with instructions on how to do this.

When posting the results in a new post highlight all text and click on the # icon in the toolbar to wrap the text with code tags (makes for easier reading).

Thanks.

---

### Post by me075064 on 2011-05-15
Hi thanks for the help.

My laptop is an Acer Aspire 5542 with 4 gb or RAM and an ATI Radeon hd 4200 Graphics chipset

I've booted from a live usb and run the script you suggested the results are below:

Once again many thanks; I was really happy with ubuntu before the upgrade.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048    24,782,847       204,800   7 HPFS/NTFS
/dev/sda3          24,782,848   585,855,749   561,072,902   7 HPFS/NTFS
/dev/sda4         585,857,022   625,141,759    39,284,738   5 Extended
/dev/sda5         585,857,024   623,413,247    37,556,224  83 Linux
/dev/sda6         623,415,296   625,141,759     1,726,464  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2031 MB, 2031091712 bytes
63 heads, 62 sectors/track, 1015 cylinders, total 3966976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     3,964,589     3,964,528   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       7ec10e13-bfd4-4c95-bdc5-fef5c64d2571   ext3                                     
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE                     
/dev/sda2        7E6EBAD16EBA8187                       ntfs       SYSTEM RESERVED               
/dev/sda3        16D0C1D5D0C1BAEF                       ntfs       ACER                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        ab12a404-028a-45da-8a47-07a32b2e32eb   ext4                                     
/dev/sda6        f651e456-7b3d-4580-bfc8-a80933691907   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C858-D96B                              vfat       MYLINUXLIVE                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root ab12a404-028a-45da-8a47-07a32b2e32eb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root ab12a404-028a-45da-8a47-07a32b2e32eb
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root ab12a404-028a-45da-8a47-07a32b2e32eb
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=ab12a404-028a-45da-8a47-07a32b2e32eb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root ab12a404-028a-45da-8a47-07a32b2e32eb
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=ab12a404-028a-45da-8a47-07a32b2e32eb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root ab12a404-028a-45da-8a47-07a32b2e32eb
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=ab12a404-028a-45da-8a47-07a32b2e32eb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root ab12a404-028a-45da-8a47-07a32b2e32eb
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=ab12a404-028a-45da-8a47-07a32b2e32eb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root ab12a404-028a-45da-8a47-07a32b2e32eb
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=ab12a404-028a-45da-8a47-07a32b2e32eb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root ab12a404-028a-45da-8a47-07a32b2e32eb
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=ab12a404-028a-45da-8a47-07a32b2e32eb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root ab12a404-028a-45da-8a47-07a32b2e32eb
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=ab12a404-028a-45da-8a47-07a32b2e32eb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root ab12a404-028a-45da-8a47-07a32b2e32eb
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=ab12a404-028a-45da-8a47-07a32b2e32eb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root ab12a404-028a-45da-8a47-07a32b2e32eb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root ab12a404-028a-45da-8a47-07a32b2e32eb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root DAA41C49A41C2B11
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 7E6EBAD16EBA8187
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ab12a404-028a-45da-8a47-07a32b2e32eb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f651e456-7b3d-4580-bfc8-a80933691907 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 310.8GB: boot/grub/core.img
 302.9GB: boot/grub/grub.cfg
 306.0GB: boot/initrd.img-2.6.35-25-generic
 312.2GB: boot/initrd.img-2.6.35-28-generic
 312.3GB: boot/initrd.img-2.6.38-8-generic
 312.3GB: boot/initrd.img-2.6.38-8-generic-pae
 311.1GB: boot/vmlinuz-2.6.35-25-generic
 311.6GB: boot/vmlinuz-2.6.35-28-generic
 309.8GB: boot/vmlinuz-2.6.38-8-generic
 309.9GB: boot/vmlinuz-2.6.38-8-generic-pae
 312.3GB: initrd.img
 312.3GB: initrd.img.old
 309.9GB: vmlinuz
 309.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 d0 01  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3e 00 00 00  |........?...>...|
00000020  70 7e 3c 00 18 0f 00 00  00 00 00 00 02 00 00 00  |p~<.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 6b d9 58 c8 4e  4f 20 4e 41 4d 45 20 20  |..)k.X.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 08 6b 2c 00  66 ba 00 00 00 00 bb 00  |}.f..k,.f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by Rubi1200 on 2011-05-15
Hi,
sorry for the delayed response. Since you have 11.04 installed and the script I told you to use is for previous versions, can I ask you to please run it again but this time use this updated version.

The reason is the way the script parses information and we want to get the correct information to help you properly.

Thanks.

```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'
```
Just run this in the terminal to download the script and then use the instructions to run it and post back here.

---

### Post by MAFoElffen on 2011-05-15
> **me075064 said:**
> Hi all,

I've been dual booting Ubuntu and Windows 7 for a while and up until now Ubuntu has worked great for me.
Last night I performed the update to install the lastest version of the Ubuntu which appeared to go ok, but following the restart Ubuntu no longer loads. (Screen shot attached [ATTACH]192209[/ATTACH])
When I choose a previous version of Ubuntu from a sub menu of the boot menu it appears to load fine - and has a new interface, and Windows 7 still loads.
Can anyone help me fix my system?

Many thanks 
John M
Soory-- after seeing this not getting anywhere, I thought I'd jump in an offer some assistance.

You did say that you can boot a previous version of the linux kernel fine.  You gave a photo of a grub menu.  So grub is loaded correctly.  You can boot at least an earlier linux kernel.

Refer to this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
Follow the Trouble Shooting Flowchart and follow the instructions to see if you can boot into a text console with the current kernel.

If you can, then your problem is graphics or desktop... Tell me how far you get so we can reslove your troubles.  Previos to that, there are a lot a variables of the maybe's.

---

### Post by me075064 on 2011-05-15
Thanks - Problem is sorted. The issue was graphics drivers.

Using the trouble shooting guide I was able to boot into low graphics mode and then search for the correct hardware drivers (and also revert back to classic mode ;) )
Everything is now working a treat. 

Many thanks for all your help -much appreciated :P

---

### Post by MAFoElffen on 2011-05-15
> **me075064 said:**
> Thanks - Problem is sorted. The issue was graphics drivers.

Using the trouble shooting guide I was able to boot into low graphics mode and then search for the correct hardware drivers (and also revert back to classic mode ;) )
Everything is now working a treat. 

Many thanks for all your help -much appreciated :P
You're welcome.

Since you are the thread originator, if solved, please remember to use the forum thread tools to mark this thread as "solved."

---

### Post by Rubi1200 on 2011-05-16
> **me075064 said:**
> Thanks - Problem is sorted. The issue was graphics drivers.

Using the trouble shooting guide I was able to boot into low graphics mode and then search for the correct hardware drivers (and also revert back to classic mode ;) )
Everything is now working a treat. 

Many thanks for all your help -much appreciated :P

Glad you got it sorted out :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

