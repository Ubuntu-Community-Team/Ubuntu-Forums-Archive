---
title: "Updated from 10.10 to 11.04, now W7 doesn't boot properly"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by JuYoung101 on 2011-06-01
For many years, my system has been a Windows 7 and Ubuntu dual boot. But after online updating from 10.10 to 11.04, when selecting Windows 7 from the boot loader it just takes me to a black screen with a flashing input marker (the underscore type one) but won't show anything being inputted.

First partition is Windows 7 set as boot.
Second partition is a Logical with Ubuntu, /.  A Linux swap after that.


Anybody have an idea as to what is happening here or how to fix this? 
Would reallly prefer not to re-install 7 with how long it has taken to get it to my liking.

---

### Post by yo_bhan on 2011-06-02
you should fix mbr win 7 first, using win 7 installation dvd.
choose repair>comman prompt>

and then type in terminal
bootrec /fixboot ->enter
bootrec /fixmbr ->enter

restart

after that fix grub ubuntu using live cd

type in terminal
$ sudo fdisk -l

check your ubuntu partition
[IMG]http://dl.dropbox.com/u/12471603/pic/Natty-Smaller/ss5.jpg[/IMG]
[FONT=monospace]mount your linux partition
[/FONT]in my case, I have sda1 for linux

$ sudo mount /dev/sda1 /media

-reinstall grub ubuntu

$ sudo grub-install --root-directory=/media /dev/sda

-reboot, login to your ubuntu
-then update your grub

$ sudo update-grub

hope this help :D

---

### Post by Hedgehog1 on 2011-06-02
We need to get a look at your install to get an idea what is going on.

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

### Post by JuYoung101 on 2011-06-02
Is there another way to fix the MBR without using a W7 install disc?
HP shipped me a W7 upgrade disc but that's back in Arizona with the rest of my misc. stuff. Would it work using my roommate's install disc?

---

### Post by Hedgehog1 on 2011-06-02
You can download the ISOs and create win7 or vista recovery disks.

Download the ISO for [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

However, before you hammer the MBR, if you would run the boot info script from either Ubuntu (if it is booting) or an Ubuntu LiveCD/LiveUSB if it is not, we can see what is going on with your system rather than guessing.

***The Hedge***

:KS

---

### Post by JuYoung101 on 2011-06-02
> **Hedgehog1 said:**
> You can download the ISOs and create win7 or vista recovery disks.

Download the ISO for [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

However, before you hammer the MBR, if you would run the boot info script from either Ubuntu (if it is booting) or an Ubuntu LiveCD/LiveUSB if it is not, we can see what is going on with your system rather than guessing.

***The Hedge***

:KS


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 1481903592 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63 1,464,843,812 1,464,843,750   7 NTFS / exFAT / HPFS
/dev/sda2       1,464,844,286 1,953,523,711   488,679,426   5 Extended
/dev/sda5       1,464,844,288 1,936,748,543   471,904,256  83 Linux
/dev/sda6       1,936,750,592 1,953,523,711    16,773,120  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3EF0C5B9F0C577A3                       ntfs       Quin
/dev/sda5        67b4fe54-81da-4927-b565-9f3a2a956601   ext4       
/dev/sda6        a3428d80-a081-4249-9d91-98aca0958889   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== sda1/Wubi/boot/grub/grub.cfg: =========================

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
}

insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 3ef0c5b9f0c577a3
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 3ef0c5b9f0c577a3
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-24-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ef0c5b9f0c577a3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, Linux 2.6.35-24-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ef0c5b9f0c577a3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ef0c5b9f0c577a3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ef0c5b9f0c577a3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ef0c5b9f0c577a3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ef0c5b9f0c577a3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ef0c5b9f0c577a3
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

============================= sda1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   6.300979614 = 6.765625344    boot/grub/grub.cfg                             1
   7.003349304 = 7.519789056    boot/initrd.img-2.6.32-24-generic              2
   7.924549103 = 8.508919808    boot/initrd.img-2.6.35-23-generic              2
   8.788581848 = 9.436667904    boot/initrd.img-2.6.35-24-generic              2
  10.669765472 = 11.456573440   boot/vmlinuz-2.6.32-24-generic                 1
  11.241798401 = 12.070789120   boot/vmlinuz-2.6.35-23-generic                 1
  11.245841980 = 12.075130880   boot/vmlinuz-2.6.35-24-generic                 1
   8.788581848 = 9.436667904    initrd.img                                     2
   7.924549103 = 8.508919808    initrd.img.old                                 2
  11.245841980 = 12.075130880   vmlinuz                                        1
  11.241798401 = 12.070789120   vmlinuz.old                                    1

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
search --no-floppy --fs-uuid --set=root 67b4fe54-81da-4927-b565-9f3a2a956601
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 67b4fe54-81da-4927-b565-9f3a2a956601
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
    search --no-floppy --fs-uuid --set=root 67b4fe54-81da-4927-b565-9f3a2a956601
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=67b4fe54-81da-4927-b565-9f3a2a956601 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 67b4fe54-81da-4927-b565-9f3a2a956601
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=67b4fe54-81da-4927-b565-9f3a2a956601 ro single 
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
    search --no-floppy --fs-uuid --set=root 67b4fe54-81da-4927-b565-9f3a2a956601
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 67b4fe54-81da-4927-b565-9f3a2a956601
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3EF0C5B9F0C577A3
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
UUID=67b4fe54-81da-4927-b565-9f3a2a956601 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda6 during installation
UUID=a3428d80-a081-4249-9d91-98aca0958889 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 706.626720428 = 758.734663680  boot/grub/core.img                             1
 754.639308929 = 810.287788032  boot/grub/grub.cfg                             1
 701.421875000 = 753.146003456  boot/initrd.img-2.6.38-8-generic               2
 706.625003815 = 758.732820480  boot/vmlinuz-2.6.38-8-generic                  1
 701.421875000 = 753.146003456  initrd.img                                     2
 706.625003815 = 758.732820480  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  3d d9 30 3c fe db 30 0d  05 36 3e 3d 00 3c 39 d8  |=.0<..0..6>=.<9.|
00000010  96 21 ec 30 37 3e 00 3e  32 d3 30 c7 37 3f 3e 21  |.!.07>.>2.0.7?>!|
00000020  11 7f 20 04 40 38 3f 6e  c5 26 38 40 3f 55 30 5e  |.. .@8?n.&8@?U0^|
00000030  7e ca 21 ef 0e 39 0f 00  8f 12 60 48 04 cf 39 41  |~.!..9....`H..9A|
00000040  0f 00 27 02 33 41 3a 41  f8 d5 10 94 30 ab 10 3a  |..'.3A:A....0..:|
00000050  42 41 00 3c ec 69 20 4a  42 3b 42 65 26 3b 43 42  |BA.<.i JB;Be&;CB|
00000060  be 71 26 3b 3c 43 09 1e  e7 30 1e 9e d3 30 3c 44  |.q&;<C...0...0<D|
00000070  43 09 f2 31 7a 42 3d d7  44 00 78 97 20 78 0f 10  |C..1zB=.D.x. x..|
00000080  3d 45 59 44 a1 22 92 42  3e 45 2d 40 7c 31 42 7f  |=EYD.".B>E-@|1B.|
00000090  3e 46 45 00 7c 7e 7c 3d  42 77 3e 3f 46 55 36 3f  |>FE.|~|=Bw>?FU6?|
000000a0  47 46 61 36 77 3f 40 47  2d 46 40 48 47 39 46 bf  |GFa6w?@G-F@HG9F.|
000000b0  0f 41 10 00 78 9a 18 13  41 db 49 10 21 10 5b 7f  |.A..x...A.I.!.[.|
000000c0  f2 42 42 49 18 09 10 3e  30 d3 30 42 4a 04 50 17  |.BBI...>0.0BJ.P.|
000000d0  10 0a 52 cf 43 4a 09 78  d3 20 4a 41 43 4b 33 4a  |..R.CJ.x. JACK3J|
000000e0  00 ca 11 22 52 44 4b c9  13 0f 10 e7 44 4c 4b d5  |..."RDK.....DLK.|
000000f0  11 9d 42 44 45 4c ee c5  26 45 4d 4c 21 46 45 46  |..BDEL..&EML!FEF|
00000100  4d ee 55 36 46 4e 4d 61  36 46 47 4e ee 2d 46 47  |M.U6FNMa6FGN.-FG|
00000110  4f 4e 39 46 47 48 4f b8  b1 40 24 40 33 40 48 50  |ON9FGHO..@$@3@HP|
00000120  4f 2d 40 5e dd 60 9a 51  51 1c 1b 25 06 13 51 39  |O-@^.`.QQ..%..Q9|
00000130  1b 9d 01 ad 02 52 0c 29  2d 41 3d 42 4f 53 52 2a  |.....R.)-A=BOSR*|
00000140  00 54 41 e2 22 53 4c 20  dc 75 20 c2 11 2a 52 29  |.TA."SL .u ..*R)|
00000150  51 40 5a 60 ce 8a 31 0c  52 11 f5 f1 05 02 53 31  |Q@Z`..1.R.....S1|
00000160  39 52 29 51 ed 52 0d 52  31 95 51 59 32 7f 54 01  |9R)Q.R.R1.QY2.T.|
00000170  02 00 5c 6c 45 3d 42 b7  01 13 12 0d 00 50 7a fa  |..\lE=B......Pz.|
00000180  f1 55 73 51 13 a9 03 1f  00 01 55 13 0d 00 6f 58  |.UsQ......U...oX|
00000190  72 50 7a 2c 60 14 51 b5  01 5e c5 03 02 03 2c 80  |rPz,`.Q..^....,.|
000001a0  3f 00 9e 43 00 ef 00 00  1e 05 e9 f2 04 3c 06 ee  |?..C.........<..|
000001b0  ea f1 76 0a 7c 69 62 00  0c 19 76 61 62 5c 00 fe  |..v.|ib...vab\..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b0 20 1c 00 fe  |............ ...|
000001d0  ff ff 05 fe ff ff 02 b0  20 1c 00 f8 ff 00 00 00  |........ .......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Hedgehog1 on 2011-06-02
Thanks for posting this.

You have a WUBI install of Ubuntu; and that changes the rules a little.

I have no idea if the fixmbr will help or hurt - So it's your call to try it; however if you would change the description in your thread to add the words WUBI, it may attract the attention of our WUBI experts more quickly.

***The Hedge***

:KS

---

### Post by JuYoung101 on 2011-06-02
Wow. Could have sworn I wiped the Wubi and installed 10.04 from LiveDisc, then updated at each release. Huh. Thanks though! =D

---

