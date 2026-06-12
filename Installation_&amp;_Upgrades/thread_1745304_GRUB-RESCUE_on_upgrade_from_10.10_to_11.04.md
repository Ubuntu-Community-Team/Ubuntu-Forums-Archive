---
title: "GRUB-RESCUE on upgrade from 10.10 to 11.04"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by MXIIA on 2011-04-30
The day that the upgrade came out (not beta, the true release) I upgraded via the Update Manager. The upgrade went great until it asked me to reset to finalize. Upon doing that, I was greeted with a less than friendly grub-rescue> screen.

The materials I currently have at my disposal are a 10.10 installation disc, and an 8.04 installation disc, and a rescatux disc (super grub) that seems to yield an error upon any of the four options presented... how can I use these (both have Live CD) to fix the grub...

---

### Post by Hedgehog1 on 2011-04-30
First - using the 10.10 LiveCD, please do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-30
Next - You will need a Natty LiveCD/LiveUSB.

You can create it using your PC running from the 10.10 LiveCD. Download the Natty ISO to your hard drive, and then create a LiveCD or LiveUSB from that ISO.

Alternatively, you can create a Natty LiveCD/LiveUSB using another computer you may have access to.

We will need that Natty LiveCD/LiveUSB to make repairs in a bit.

***The Hedge***

:KS

---

### Post by MXIIA on 2011-05-01
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1         607,208,805   625,137,344    17,928,540   7 HPFS/NTFS
/dev/sda2                  63   196,683,794   196,683,732   7 HPFS/NTFS
/dev/sda3    *    196,683,795   197,093,394       409,600  82 Linux swap / Solaris
/dev/sda4         197,101,546   607,207,423   410,105,878   5 Extended
/dev/sda5         197,101,548   563,910,141   366,808,594  8e Linux LVM
/dev/sda6         563,910,656   602,973,155    39,062,500  83 Linux
/dev/sda7         602,974,208   607,207,423     4,233,216  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        86126BF0126BE421                       ntfs       Recovery                      
/dev/sda2        28AEF040AEF00858                       ntfs       Local                         
/dev/sda3        f27bbfea-8ab8-4f52-9c7c-47bf256e2395   swap                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        771aa6f8-faee-44c6-b3ae-46a07886cfeb   ext4                                     
/dev/sda6        3e152d17-fa86-4b1d-9e76-e96744e33ef4   ext4                                     
/dev/sda7        971f7395-102e-4831-9288-67434b1c9029   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
true
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 3e152d17-fa86-4b1d-9e76-e96744e33ef4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 86126BF0126BE421
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 28AEF040AEF00858
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=3e152d17-fa86-4b1d-9e76-e96744e33ef4 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda7 during installation
UUID=971f7395-102e-4831-9288-67434b1c9029 /boot           ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=771aa6f8-faee-44c6-b3ae-46a07886cfeb /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=f27bbfea-8ab8-4f52-9c7c-47bf256e2395 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 306.2GB: boot/grub/grub.cfg

============================= sda7/grub/grub.cfg: =============================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 3e152d17-fa86-4b1d-9e76-e96744e33ef4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 971f7395-102e-4831-9288-67434b1c9029
set locale_dir=($root)/grub/locale
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 971f7395-102e-4831-9288-67434b1c9029
    linux    /vmlinuz-2.6.38-8-generic root=UUID=3e152d17-fa86-4b1d-9e76-e96744e33ef4 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 971f7395-102e-4831-9288-67434b1c9029
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=3e152d17-fa86-4b1d-9e76-e96744e33ef4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 971f7395-102e-4831-9288-67434b1c9029
    linux    /vmlinuz-2.6.35-28-generic root=UUID=3e152d17-fa86-4b1d-9e76-e96744e33ef4 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 971f7395-102e-4831-9288-67434b1c9029
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /vmlinuz-2.6.35-28-generic root=UUID=3e152d17-fa86-4b1d-9e76-e96744e33ef4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 971f7395-102e-4831-9288-67434b1c9029
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 971f7395-102e-4831-9288-67434b1c9029
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 86126BF0126BE421
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 28AEF040AEF00858
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=971f7395-102e-4831-9288-67434b1c9029 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=f27bbfea-8ab8-4f52-9c7c-47bf256e2395 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 308.8GB: boot/grub/core.img
 308.8GB: grub/core.img
 308.9GB: grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda7

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 b8 e9 f4 23  |...............#|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```If it helps any, I usually have / mounted as /dev/sda6 and /home mounted as /dev/sda5

I am currently finishing the download of the ISO... Edit: download is finished, appropriate CD has been burned. 

Thank you for your time :) Let's hope this works.(sorry for the bad grammar)

---

### Post by keiichi_morisato on 2011-05-01
Hi, 

I did the upgrade in the same way a day after it came out and am stuck at the grub-rescue prompt also.  This is in a VMware installation.  I burned a natty live CD and was glad to see that my file system was visible after I booted from it.

The output of the bootinfo.sh script, which I ran after booting the live CD, is below.

Many thanks for any pointers to resolve this.  Apologies for jumping in; I am a ubuntu newbie and was taken by surprise.




                ```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders, total 41943040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    40,105,983    40,103,936  83 Linux
/dev/sda2          40,108,030    41,940,991     1,832,962   5 Extended
/dev/sda5          40,108,032    41,940,991     1,832,960  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        ee852062-52f5-4d30-bd37-2c9d128b4c87   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0ae755eb-7459-4a3f-93fc-3d4db2318e98   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/ee852062-52f5-4d30-bd37-2c9d128b4c87 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root ee852062-52f5-4d30-bd37-2c9d128b4c87
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root ee852062-52f5-4d30-bd37-2c9d128b4c87
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee852062-52f5-4d30-bd37-2c9d128b4c87
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sda1 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee852062-52f5-4d30-bd37-2c9d128b4c87
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sda1 ro single 
    echo    'Loading initial ramdisk ...'
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee852062-52f5-4d30-bd37-2c9d128b4c87
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=ee852062-52f5-4d30-bd37-2c9d128b4c87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee852062-52f5-4d30-bd37-2c9d128b4c87
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=ee852062-52f5-4d30-bd37-2c9d128b4c87 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee852062-52f5-4d30-bd37-2c9d128b4c87
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=ee852062-52f5-4d30-bd37-2c9d128b4c87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee852062-52f5-4d30-bd37-2c9d128b4c87
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=ee852062-52f5-4d30-bd37-2c9d128b4c87 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee852062-52f5-4d30-bd37-2c9d128b4c87
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ee852062-52f5-4d30-bd37-2c9d128b4c87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee852062-52f5-4d30-bd37-2c9d128b4c87
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ee852062-52f5-4d30-bd37-2c9d128b4c87 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee852062-52f5-4d30-bd37-2c9d128b4c87
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee852062-52f5-4d30-bd37-2c9d128b4c87
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
# Commented out by Dropbox
# UUID=ee852062-52f5-4d30-bd37-2c9d128b4c87 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0ae755eb-7459-4a3f-93fc-3d4db2318e98 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=ee852062-52f5-4d30-bd37-2c9d128b4c87 / ext4 errors=remount-ro,user_xattr 0 1

=================== sda1: Location of files loaded by Grub: ===================


  10.9GB: boot/grub/core.img
   6.6GB: boot/grub/grub.cfg
   3.6GB: boot/initrd.img-2.6.35-22-generic
   3.6GB: boot/initrd.img-2.6.35-27-generic
   6.0GB: boot/initrd.img-2.6.35-28-generic
  10.9GB: boot/vmlinuz-2.6.35-22-generic
  10.9GB: boot/vmlinuz-2.6.35-27-generic
  11.2GB: boot/vmlinuz-2.6.35-28-generic
   9.5GB: boot/vmlinuz-2.6.38-8-generic
   6.0GB: initrd.img
   3.6GB: initrd.img.old
  11.2GB: vmlinuz
  10.9GB: vmlinuz.old

```

---

### Post by Hedgehog1 on 2011-05-01
This post is for **MXIIA**:

I think the thing on your disk that confused the upgrade process is that you have your swap partition marked as 'bootable' (it has the '*' on it.

```
/dev/sda3    *    196,683,795   197,093,394       409,600  82 Linux swap / Solaris
```

So I would like to correct this (for next time you upgrade) and also get you running again.

Please boot from the **Natty/11.04** LiveCD/LiveUSB (you may already be running from it to read the forum).

Run gparted (you now get to it from the 'power button' menu, system settings (last item in the menu)).

Right click on the /dev/sda3, select 'manage flags', and **uncheck** the boot flag.

Next, right click on the /dev/sda2, select 'manage flags', and **check** the boot flag. This will allow you to boot directly from windows should you ever need to.

Next, we will clean up grub to match your system layout.  The following commands are for your machine based on the script output. Your install also uses a separate '/boot' partition, so that makes is a little more unique.

```
sudo mkdir /mnt/boot
```

```
sudo mount /dev/sda7 /mnt/boot
```

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

You should be able to reboot into Natty from the hard disk now.

***The Hedge***

:KS

p.s. **keiichi_morisato**, I will look at your script output next.

---

### Post by MXIIA on 2011-05-01
sudo mount /dev/sda5 /mnt
For mine, do you mean sda6? As that is where my / is mounted. My /home is mounted on sda5.

Edit: yes you did, it worked, I was greeted with a grub> prompt at boot, which means that I need to update the grub menu file with update-grub
```

update-grub

```

---

### Post by Hedgehog1 on 2011-05-01
This post is for **keiichi_morisato**,

Greetings fellow west-coaster!

I cannot see anything wrong with the script output to give me an idea why you are the the grub prompt.

You indicated this is a VMware install.  I use Virtual Box for my (many) virtual machines, and the version that supports Natty as a guest OS just became available less the 2 weeks ago (version 4.0.6).

I don't know if VMware is supporting Natty yet, (and even if it didn't grub ***should*** work in any case).  Can I request you do a test by creating a new Virtual Machine and install Natty from the LiveCD on that?  This will tell us if the issue is something I am just not seeing in the output script, or if VMware isn't ready for Natty quite yet.

Thanks!

***The Hedge***

:KS

p.s. What is your Host OS?

---

### Post by Hedgehog1 on 2011-05-01
> **MXIIA said:**
> sudo mount /dev/sda5 /mnt
For mine, do you mean sda6? As that is where my / is mounted. My /home is mounted on sda5.

Thanks for double checking, you are right, it really should instead be:

```
sudo mount /dev/sda6 /mnt
```

***The Hedge***

:KS

---

### Post by keiichi_morisato on 2011-05-01
Hi Hedge,

Thank you for replying so rapidly.  My host OS is Windows 7 Professional.

I'm using VMware workstation version 7.1.4 build-385536.  I checked for upgrades and I appear to have the latest VMware.  I used the live CD to install a version of Natty in a new virtual machine and everything went fine.  I can't see anything unusual in that installation.  It booted to the GUI and let me log in with no errors.

So it looks like VMware isn't the problem.

Keiichi

---

### Post by Hedgehog1 on 2011-05-01
> **keiichi_morisato said:**
> Hi Hedge,

Thank you for replying so rapidly.  My host OS is Windows 7 Professional.

I'm using VMware workstation version 7.1.4 build-385536.  I checked for upgrades and I appear to have the latest VMware.  I used the live CD to install a version of Natty in a new virtual machine and everything went fine.  I can't see anything unusual in that installation.  It booted to the GUI and let me log in with no errors.

So it looks like VMware isn't the problem.

Keiichi

OK - Thanks for running that test.  So now we know that Natty runs fine in VMware workstation version 7.1.4 build-385536.

If the ISO is fine and VMware is fine, then the upgrade didn't go right and I cannot  what the error from the output script (others might).

Lets try a safe thing and see how that goes:

From the LiveCd/LiveUSB (or the ISO in your case):

```
sudo mount /dev/sda1 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Then see if Natty will boot properly for you.

This is just a rebuild of grub - but it is a reasonable thing to try.

***The Hedge***

:KS

---

### Post by MXIIA on 2011-05-01
So far I've gotten out of grub-rescue into grub>... I made a new topic about this, as it appears it is a different problem

Hedge, can you take a look at 
[http://ubuntuforums.org/showthread.php?t=1746094](http://ubuntuforums.org/showthread.php?t=1746094)

---

### Post by keiichi_morisato on 2011-05-01
Hi again,

I did the grub rebuild and it completed with no errors.  I rebooted and got a kernel panic saying it couldn't mount the root file system "on unknown-block(0,0)"

I am enclosing a screen shot of the rest of the error message.  I could not see how to put this in as text, sorry.

-K

---

### Post by Hedgehog1 on 2011-05-01
> **keiichi_morisato said:**
> Hi again,

I did the grub rebuild and it completed with no errors.  I rebooted and got a kernel panic saying it couldn't mount the root file system "on unknown-block(0,0)"

I am enclosing a screen shot of the rest of the error message.  I could not see how to put this in as text, sorry.

-K

I think you are facing a clean reinstall of 11.04.

Your best option is (from my point of view) to create a Natty VM of the size you want and copy your documents to that.

The other option is to create a separate '/home' partition so you can do OS Upgrades and Reinstalls without damaging your data. You can do that in the current VM, or in a new VM.

***The Hedge***

:KS

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by keiichi_morisato on 2011-05-01
Hi Hedge,

OK, thanks very much indeed for your help.  I can install Natty and get my code by booting from the ISO really fast.  The issue is all of the other stuff I installed, some of which I can't quite remember how to install except that it couldn't be done from the package manager.  That will take some time.

Sigh.  I guess the moral of the story is to wait a few months from when the update is released before trying it, and doing a backup first.

-K

---

### Post by oscar_ra on 2011-05-02
Hi Dude, i got the same problem who have [MXIIA]("http://ubuntuforums.org/member.php?u=676082") and [keiichi_morisato]("http://ubuntuforums.org/member.php?u=1291835"), so i did that you said so please help me, i'm a noob too. and sorry for my english :)
here's the code.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   517,813,050   514,739,003   7 HPFS/NTFS
/dev/sda3         605,739,008   625,141,759    19,402,752  17 Hidden HPFS/NTFS
/dev/sda4         517,814,270   605,739,007    87,924,738   5 Extended
/dev/sda5         517,814,272   602,046,693    84,232,422  83 Linux
/dev/sda6         602,048,512   605,739,007     3,690,496  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        00E0772AE0772556                       ntfs       System                        
/dev/sda2        E6709D06709CDE9D                       ntfs       TI105444W0C                   
/dev/sda3        DCC2C2E7C2C2C4CC                       ntfs       HDDRECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        079da388-8859-4bf1-8de5-ff195b763dea   ext4                                     
/dev/sda6        cd146570-6987-4dac-83e4-a87b16777ae3   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
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
search --no-floppy --fs-uuid --set=root 079da388-8859-4bf1-8de5-ff195b763dea
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 079da388-8859-4bf1-8de5-ff195b763dea
set locale_dir=($root)/boot/grub/locale
set lang=es_CO
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
menuentry 'Ubuntu, con Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 079da388-8859-4bf1-8de5-ff195b763dea
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=079da388-8859-4bf1-8de5-ff195b763dea ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, con Linux 2.6.38-8-generic-pae (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 079da388-8859-4bf1-8de5-ff195b763dea
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=079da388-8859-4bf1-8de5-ff195b763dea ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, con Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 079da388-8859-4bf1-8de5-ff195b763dea
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=079da388-8859-4bf1-8de5-ff195b763dea ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, con Linux 2.6.35-28-generic-pae (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 079da388-8859-4bf1-8de5-ff195b763dea
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=079da388-8859-4bf1-8de5-ff195b763dea ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
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
    search --no-floppy --fs-uuid --set=root 079da388-8859-4bf1-8de5-ff195b763dea
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 079da388-8859-4bf1-8de5-ff195b763dea
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 00E0772AE0772556
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root E6709D06709CDE9D
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root DCC2C2E7C2C2C4CC
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
UUID=079da388-8859-4bf1-8de5-ff195b763dea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cd146570-6987-4dac-83e4-a87b16777ae3 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 282.4GB: boot/grub/core.img
 274.1GB: boot/grub/grub.cfg
 269.9GB: boot/initrd.img-2.6.35-28-generic-pae
 271.8GB: boot/initrd.img-2.6.38-8-generic-pae
 282.5GB: boot/vmlinuz-2.6.35-28-generic-pae
 270.2GB: boot/vmlinuz-2.6.38-8-generic-pae
 271.8GB: initrd.img
 269.9GB: initrd.img.old
 270.2GB: vmlinuz
 282.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 18 8e e1 20  |............... |
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by ancaleth on 2011-05-06
Same problem here, and tired of fighting getting nowhere. Upgrade from Ubuntu 10.10 to 11.04 caused Grub to vanish. A problem which I also have, when booting Windows 7 from the other partition for some reason. However, I never had problems rescuing Grub before. 

I am burning a 64/bit live CD of 10.4 to try recuperation via chroot, as all other methods have failed yet. But maybe there is a better way?

EDIT> I hope there is, because the only other PC in the house is a Mac and it has decided, not to allow me to make a 64/bit live cd.

---

