---
title: "Another messed up grub menu... URGENT"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by lifelike27 on 2011-05-27
I've gone and done something stupid...

I needed to rearrange my partitions so I booted into my live CD and moved my ubuntu partition. Then just in case I reinstalled grub:
```
sudo mount /dev/sda3 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
sudo umount /mnt
sudo reboot
```After that, I was able to boot into Ubuntu fine. I did forget to run update-grub after that, so the next time I restarted my laptop, I was stuck at a black screen.

I've tried to do the same thing again, but now I get the following error:
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

```Nothings working... :(

---

### Post by Hedgehog1 on 2011-05-27
We need to get a look at your partitons and grub to get an idea what is going on.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

### Post by lifelike27 on 2011-05-27
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    693493760 of the same hard drive for core.img, but core.img can not be 
    found at this location.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              40       409,639       409,600 EFI System partition
/dev/sda2         411,648   205,211,647   204,800,000 Data partition (Windows/Linux)
/dev/sda3     693,493,760   888,805,375   195,311,616 Data partition (Windows/Linux)
/dev/sda4     888,805,376   976,510,975    87,705,600 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sda5     675,909,632   693,493,759    17,584,128 Swap partition (Linux)
/dev/sda6     205,211,648   568,975,359   363,763,712 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        70D6-1701                              vfat       EFI
/dev/sda2        B6C48B20C48AE24B                       ntfs       
/dev/sda3        1699c6fb-8c85-4e75-a8ed-6dbded9adb97   ext4       
/dev/sda4        b75d8bf9-452c-3395-9fbc-29cc373c8d67   hfsplus    Snow Leopard
/dev/sda5        8cb7190a-6090-4bed-8d34-3321d7cdf8f2   swap       
/dev/sda6        64E6C2D24FFE2A79                       ntfs       Storage

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /mnt                     ext4       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========================== sda2/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
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

insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt3)'
search --no-floppy --fs-uuid --set=root 1699c6fb-8c85-4e75-a8ed-6dbded9adb97
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt3)'
search --no-floppy --fs-uuid --set=root 1699c6fb-8c85-4e75-a8ed-6dbded9adb97
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
    savedefault
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt3)'
    search --no-floppy --fs-uuid --set=root 1699c6fb-8c85-4e75-a8ed-6dbded9adb97
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1699c6fb-8c85-4e75-a8ed-6dbded9adb97 ro  vga=792 quiet  quiet splash
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt3)'
    search --no-floppy --fs-uuid --set=root 1699c6fb-8c85-4e75-a8ed-6dbded9adb97
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1699c6fb-8c85-4e75-a8ed-6dbded9adb97 ro single  vga=792 quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt3)'
    search --no-floppy --fs-uuid --set=root 1699c6fb-8c85-4e75-a8ed-6dbded9adb97
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt3)'
    search --no-floppy --fs-uuid --set=root 1699c6fb-8c85-4e75-a8ed-6dbded9adb97
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    savedefault
    insmod part_gpt
    insmod ntfs
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root B6C48B20C48AE24B
    chainloader +1
}
menuentry "Mac OS X (32-bit) (on /dev/sda4)" --class osx --class darwin --class os {
    savedefault
    insmod part_gpt
    insmod hfsplus
    set root='(/dev/sda,gpt4)'
    search --no-floppy --fs-uuid --set=root 8986a7c6f5502f1f
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 8986a7c6f5502f1f uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda4)" --class osx --class darwin --class os {
    savedefault
    insmod part_gpt
    insmod hfsplus
    set root='(/dev/sda,gpt4)'
    search --no-floppy --fs-uuid --set=root 8986a7c6f5502f1f
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 8986a7c6f5502f1f uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

#menuentry "MODIFIED Mac OS X (32-bit)" {
#    set root=(hd0,4)
#    insmod video
#    insmod vbe
#    chainloader /usr/standalone/i386/chain0 cpu=1 
#    xnu_kernel /mach_kernel rd=disk0s6
#    if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
#        xnu_mkext /System/Library/Extensions.mkext
#    else
#        xnu_kextdir /System/Library/Extensions
#    fi
#}

menuentry "Mac OS X Boot Loader" {
insmod hfsplus
set root='(hd0,4)'
chainloader (hd0,3)/boot/chameleon/boot0
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>           <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid     0       0
# / was on /dev/sda3 during installation
UUID=1699c6fb-8c85-4e75-a8ed-6dbded9adb97 /               ext4    errors=remount-ro,user_xattr 0       1
/dev/sda5       none           swap       sw               0       0

--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 340.826393127 = 365.959553024  boot/grub/core.img                             1
 385.117210388 = 413.516455936  boot/grub/grub.cfg                             1
 401.073940277 = 430.649864192  boot/initrd.img-2.6.38-8-generic               2
 340.820316315 = 365.953028096  boot/vmlinuz-2.6.38-8-generic                  1
 401.073940277 = 430.649864192  initrd.img                                     2
 340.820316315 = 365.953028096  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 40 06 00 4f 0c 00 00  00 00 00 00 02 00 00 00  |.@..O...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 01 17 d6 70 45  46 49 20 20 20 20 20 20  |..)...pEFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda4

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 a3  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 58 b0 04 8d  |...=HXt.=H+uX...|
00000060  36 ed e3 8d 3e 20 e5 e8  96 01 75 49 8d b6 1d 01  |6...> ....uI....|
00000070  8b 34 81 3c 00 02 75 3d  66 8b 5c 5c 66 0f cb 66  |.4.<..u=f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb 7f 03 77 25  |......f.......w%|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 bf f0  e1 e8 6d 00 8a 16 04 e6  |.|h.N.....m.....|
000000b0  ea 00 02 00 20 bf e7 e3  e8 5e 00 f4 eb fd 66 60  |.... ....^....f`|
000000c0  89 c3 66 31 c0 88 d8 81  fb 40 00 72 02 b0 40 e8  |..f1.....@.r..@.|
000000d0  12 00 29 c3 74 0b 66 01  c1 c1 e0 09 66 01 c2 eb  |..).t.f.....f...|
000000e0  e1 66 61 c3 66 60 06 89  e5 89 d3 80 e7 0f 66 c1  |.fa.f`........f.|
000000f0  ea 04 30 d2 8e c2 1e 1e  66 03 0e 00 e6 66 51 06  |..0.....f....fQ.|
00000100  53 30 e4 50 68 10 00 8a  16 04 e6 89 e6 b4 42 cd  |S0.Ph.........B.|
00000110  13 72 a2 89 ec 07 66 61  c3 66 60 57 be dd e3 e8  |.r....fa.f`W....|
00000120  07 00 5e e8 03 00 66 61  c3 bb 01 00 ac 3c 00 74  |..^...fa.....<.t|
00000130  06 b4 0e cd 10 eb f5 c3  66 60 ad 86 e0 ab 3c 00  |........f`....<.|
00000140  74 23 89 c1 ad 86 e0 80  3e 01 e4 58 74 14 09 c0  |t#......>..Xt...|
00000150  75 01 48 80 fc 00 77 0a  3c 41 72 06 3c 5a 77 02  |u.H...w.<Ar.<Zw.|
00000160  04 20 ab e2 df 66 61 c3  66 60 b2 00 66 8b 44 02  |. ...fa.f`..f.D.|
00000170  66 3b 45 02 75 0f 80 3c  00 75 0a 66 8b 44 06 66  |f;E.u..<.u.f.D.f|
00000180  3b 45 06 74 48 77 44 72  3d 66 60 31 d2 87 f7 66  |;E.tHwDr=f`1...f|
00000190  ad 66 89 c1 87 f7 66 ad  66 39 c8 77 2e 72 27 87  |.f....f.f9.w.r'.|
000001a0  f7 ad 89 c1 87 f7 ad 80  f9 00 74 1f 39 c8 74 0b  |..........t.9.t.|
000001b0  77 07 fe ce 89 c1 e9 02  00 fe c6 f3 a7 77 0c 72  |w............w.r|
000001c0  05 88 f2 e9 07 00 fe ca  e9 02 00 fe c2 88 96 14  |................|
000001d0  00 80 fa 00 66 61 c3 50  57 8b 3e 0a e6 57 47 47  |....fa.PW.>..WGG|
000001e0  49 49 b0 00 f3 aa 89 3e  0a e6 5d 89 2d 5f 58 c3  |II.....>..].-_X.|
000001f0  2f 62 6f 6f 74 00 00 00  00 00 00 00 00 00 55 aa  |/boot.........U.|
00000200



```

I should also mention that I used gdisk to to get Windows to work while triple booting with OS X.

---

### Post by Hedgehog1 on 2011-05-27
Thanks for posting the script output.

You have created an interesting situation for yourself.

I am confused as to how you booted into Ubuntu after the initial re-arranging of partitions; I would have expected you had the same error the first time.

Did you remember the --recheck this time?

```
sudo mount /dev/sda3 /mnt
sudo grub-install **[COLOR="Red"]--recheck[/COLOR]** --root-directory=/mnt /dev/sda
sudo umount /mnt
sudo reboo
```

If that doesn't work, we will have to call in the big guns.

***The Hedge***

:KS

---

### Post by lifelike27 on 2011-05-28
Yup, I did. I get the same error. 

Earlier I noticed something as well. When I open GParted and change the boot flag for the ubuntu partition to bios_grub, I'm able to install grub to that partition. When I restart, I'm still stuck with that black screen. :(

---

### Post by Hedgehog1 on 2011-05-28
Is the reboot to a black screen the 'Flashing cursor in the upper left hand corner' back screen?

If so your grub is fine and you need to change the video booting options: 

[http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

***The Hedge***

:KS

---

### Post by nitstorm on 2011-05-28
> **lifelike27 said:**
> Yup, I did. I get the same error. 

Earlier I noticed something as well. When I open GParted and change the boot flag for the ubuntu partition to bios_grub, I'm able to install grub to that partition. When I restart, I'm still stuck with that black screen. :(


Did u remember the * sudo update-grub * this time?

---

### Post by lifelike27 on 2011-05-28
> **nitstorm said:**
> Did u remember the * sudo update-grub * this time?

I don't think I was clear the first time. When I tried to install grub into the sda3 partition (ubuntu partiton) I got the same blank screen with the blinking cursor as Hedgehog described. I wasn't able to boot into my Ubuntu partition to run update-grub.

---

### Post by Hedgehog1 on 2011-05-28
So I think that:

1) Change the boot flag for the ubuntu partition to bios_grub

2) Fix the video boot issue

Makes sense - but will that get you booting again into all your various OSs?

Will Grub stay functional after that?

:confused:

---

### Post by nitstorm on 2011-05-28
You can update your grub by binding the /proc /dev and /sys from the live cd to ur ubuntu partition on HDD
[URL="http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7"]
http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7[/URL]

Check that out...

Also there is something about finding core.img in method 3) in that link so check that out as well

---

### Post by lifelike27 on 2011-05-28
nitstorm, I followed that website and was able to update-grub. It showed my operating systems being added to the menu but when I restarted, I'm still stuck at the black screen.

hedgehog1, I followed that thread link and it wasn't much help. When following the steps in the Troubleshooting Flow Chart, I got stuck on step 1. I answered no for all the points under it and it said to reinstall grub, which I can't do.. =\

Again, the boot flag for the Ubuntu partition is on bios_grub which doesn't seem right to me since I've never used that boot flag, ever.

---

### Post by lifelike27 on 2011-05-28
One more thing to mention. Sometimes when I boot in the live cd and try sudo mount /dev/sda3 /mnt

I get an error: ```
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```So I open up GParted and 'check' sda3. After that I can mount it...

dmesg | tail gives me this:
```
[  182.356514] scsi 5:0:0:0: Direct-Access     StoreJet TS250GSJ25S-S         PQ: 0 ANSI: 2 CCS
[  182.357706] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  182.358639] sd 5:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[  182.359576] sd 5:0:0:0: [sdb] Write Protect is off
[  182.359582] sd 5:0:0:0: [sdb] Mode Sense: 34 00 00 00
[  182.360686] sd 5:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  182.367489]  sdb: sdb1
[  182.370222] sd 5:0:0:0: [sdb] Attached SCSI disk
[  330.795029] CE: hpet4 increased min_delta_ns to 7500 nsec
[  330.795036] CE: hpet4 increased min_delta_ns to 11250 nsec
```

---

### Post by oldfred on 2011-05-28
Script is showing an EFI partition. Are you booting with BIOS or UEFI? If booting with BIOS you need to have the bios_grub partition. If you have not gotten gdisk, download gdisk from rodbooks site as it is newer. 

Grub then installs without any complaint and shows up in the bios_grub partition.

The script will show it like this from my sdb1 which is a gpt bios_grub partition, It is not formated so a lot of partition tools just do not see the partition:

```
    File system:       
    Boot sector type:  Grub2's core.img
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

```Even though it is not really a boot flag some of the partition tools call it that when you set it. Grub2 when installing will automatically find it. 

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on

It only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues
Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by srs5694 on 2011-05-28
> **lifelike27 said:**
> Earlier I noticed something as well. When I open GParted and change the boot flag for the ubuntu partition to bios_grub, I'm able to install grub to that partition. When I restart, I'm still stuck with that black screen. :(

The first part of the below comments are based on the assumption that you're using a BIOS-based computer, or at least installing Linux using a BIOS compatibility mode (as for instance most instructions for installing Linux on an Intel-based Mac suggest).

I'm sorry to say you've probably trashed your installation and will have to re-install Ubuntu.

In post #13 of this thread, oldfred summarized the purpose of the [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) (what GParted identifies as having a "bios_grub flag"). Setting this flag on a Linux boot partition was inappropriate, and when you re-ran grub-install, it overwrote the first ~30 KiB of your Linux partition. This almost certainly damaged the filesystem on that partition. There's a chance you'll be able to recover it by using fsck, but if not, you may have no choice but to restore from a backup or re-install from scratch.

If you can fix the damage with fsck, I recommend doing this:


[list=1]
[*]Create a *new* BIOS Boot Partition by using gdisk and giving the partition a type code of EF02 or by using GParted and creating a partition with the "bios_grub flag" enabled. You've got plenty of space between /dev/sda6 and /dev/sda5, so just create a partition of between 32 KiB and 1 MiB in that space.
[*]Re-install GRUB using grub-install.
[/list]


With any luck, the system will boot once you do this.

If you can't repair /dev/sda2 and have to re-install Ubuntu, be sure to create a BIOS Boot Partition prior to or during installation, or you're likely to run into the same problem again.

If, OTOH, you're using an EFI-based computer, things might not be so dire, but it really depends on the nature of the GRUB package you've got on your computer. If you're booting using EFI, the BIOS Boot Partition isn't required, and if your GRUB package in Ubuntu is the one for EFI (grub-efi rather than grub-pc), then I'm pretty sure it won't write to the BIOS Boot Partition, so you won't have trashed your installation when you re-installed GRUB. If that's the case, though, I'm not sure why GRUB isn't booting your system, except that GRUB on EFI seems to be rather delicate at the moment.

If you're using EFI, you might do better to use a combination of [rEFIt](http://refit.sourceforge.net/) and [ELILO](http://elilo.sourceforge.net/cgi-bin/blosxom) for booting. I've found this works much better on my one UEFI-based PC, although it's not very reliable at booting Ubuntu on my 32-bit Mac Mini or an Ubuntu installation in VirtualBox. (It's fine at booting OpenSUSE in VirtualBox, though; go figure.)

---

### Post by lifelike27 on 2011-05-28
SUCCESS! 

I followed srs5694 and created an unformatted partition with a boot flag bios_grub. Reinstalled grub in the sda3 partiton. It does feel like a dirty process to follow, but it did work. Once in my ubuntu partiton I ran gdisk to get my hybrid MBR partition running again. Now all OSes are working!

Thank you to all the people who helped me with this. You'll are all truly awesome!

Wooh!

---

### Post by Deniz343 on 2012-08-26
I don't know what you are talking about :p
But I found this > You need to use the --force option to allow usage of blocklists and should not use --grub-setup=/bin/true (which is similar to simply generating core.img).
grub-install will give out warnings like which should give you the idea of what might go wrong with this approach:
```
/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition. This is a BAD idea.
/sbin/grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. 
```
                        However, blocklists are UNRELIABLE and their use is discouraged.
Without --force you may get the below error and grub-setup will not setup its boot code in the partition boot sector:
```
/sbin/grub-setup: error: will not proceed with blocklists
```
With --force you should get:
```
Installation finished. No error reported.
```
The reason why grub-setup does not by default allow this is because in case of partition or a partitionless disk is that grub-bios relies on embedded blocklists in the partition bootsector to locate the /boot/grub/i386-pc/core.img file and the prefix dir /boot/grub. The sector locations of core.img may change whenever the filesystem in the partition is being altered (files copied, deleted etc.). For more info see [https://bugzilla.redhat.com/show_bug.cgi?id=728742](https://bugzilla.redhat.com/show_bug.cgi?id=728742) and [https://bugzilla.redhat.com/show_bug.cgi?id=730915](https://bugzilla.redhat.com/show_bug.cgi?id=730915).
The workaround for this is to set the immutable flag on /boot/grub/i386-pc/core.img (using chattr command as mentioned above) so that the sector locations of the core.img file in the disk is not altered. The immutable flag on /boot/grub/i386-pc/core.img needs to be set only if grub-bios is installed to a partition boot sector or a partitionless disk, not in case of installtion to MBR or simple generation of core.img without embedding any bootsector (mentioned above).

Best Regards

---

