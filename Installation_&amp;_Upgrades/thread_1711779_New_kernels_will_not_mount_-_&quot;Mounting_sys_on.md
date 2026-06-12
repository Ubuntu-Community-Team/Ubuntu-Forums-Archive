---
title: "New kernels will not mount - &quot;Mounting /sys on /root/sys failed&quot;"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by BigDon on 2011-03-21
Hi folks,

Have been searching the forums for a while attempting to locate the solution to my problem, but so far no cigar!

My problem is this:

I have a currently running kernel 2.6.35-24-generic. When I run an upgrade - makes no difference which package, 2.6.35-25-generic, 2.6.35-27-generic,
2.6.35-28-generic, or 2.6.35-29-generic - the package will download, install, and build the initrd.img and finally update grub. Just like it is supposed to (I suppose...it has in the past anyway!) with no errors.

However, when I reboot and attempt to use the new kernel, I get the error: "Mounting /sys on /root/sys failed" and "Mounting /proc on /root/proc failed"  I am able to boot into the 35-24 kernel and all is well... no errors, no problems at startup, nothing!! I am just unable to boot into the new kernel-

All the information I have found here through my searches indicate problems others have had when dual-booting their system... not the case here! I have a 100% pure Ubuntu Maverick box with a brand new hard drive installed and configured.

Here is the output from the Boot-Info script I ran:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,282,879   156,282,817  83 Linux
/dev/sda2         156,282,880   408,186,879   251,904,000  83 Linux
/dev/sda3         408,186,880   972,267,519   564,080,640   5 Extended
/dev/sda5         408,188,928   566,763,519   158,574,592  83 Linux
/dev/sda6         566,765,568   927,209,471   360,443,904  83 Linux
/dev/sda7         927,211,520   972,267,519    45,056,000  83 Linux
/dev/sda4         972,267,520   976,773,119     4,505,600  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        a94264f0-d78c-4a97-abc4-e8eb63f2c953   ext4                                     
/dev/sda2        9d25dd8c-e4e3-416b-b26b-20b361143a44   ext4       home                          
/dev/sda3: PTTYPE="dos" 
/dev/sda4        bafda4c8-de08-4387-9f74-b120b4457969   swap                                     
/dev/sda5        1f831658-8c63-4c4f-831a-89e274e47f8c   ext3       webprogs                      
/dev/sda6        3f7d42e1-b77e-4ad4-9641-88add0cedb81   ext3       video                         
/dev/sda7        7c144755-9c7a-47a9-9714-5374991de0d4   ext3       backup                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /home                    ext4       (rw,,commit=0)
/dev/sda5        /webprogs                ext3       (rw,,commit=0)
/dev/sda6        /video                   ext3       (rw,,commit=0)
/dev/sda7        /backup                  ext3       (rw,,commit=0)


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
set default="2"
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
search --no-floppy --fs-uuid --set a94264f0-d78c-4a97-abc4-e8eb63f2c953
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a94264f0-d78c-4a97-abc4-e8eb63f2c953
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a94264f0-d78c-4a97-abc4-e8eb63f2c953
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=a94264f0-d78c-4a97-abc4-e8eb63f2c953 ro  splash quiet vga=758  quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a94264f0-d78c-4a97-abc4-e8eb63f2c953
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=a94264f0-d78c-4a97-abc4-e8eb63f2c953 ro single  splash quiet vga=758
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a94264f0-d78c-4a97-abc4-e8eb63f2c953
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=a94264f0-d78c-4a97-abc4-e8eb63f2c953 ro  splash quiet vga=758  quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a94264f0-d78c-4a97-abc4-e8eb63f2c953
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=a94264f0-d78c-4a97-abc4-e8eb63f2c953 ro single  splash quiet vga=758
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a94264f0-d78c-4a97-abc4-e8eb63f2c953
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=a94264f0-d78c-4a97-abc4-e8eb63f2c953 ro  splash quiet vga=758  quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a94264f0-d78c-4a97-abc4-e8eb63f2c953
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=a94264f0-d78c-4a97-abc4-e8eb63f2c953 ro single  splash quiet vga=758
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a94264f0-d78c-4a97-abc4-e8eb63f2c953
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=a94264f0-d78c-4a97-abc4-e8eb63f2c953 ro  splash quiet vga=758  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a94264f0-d78c-4a97-abc4-e8eb63f2c953
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=a94264f0-d78c-4a97-abc4-e8eb63f2c953 ro single  splash quiet vga=758
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a94264f0-d78c-4a97-abc4-e8eb63f2c953
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a94264f0-d78c-4a97-abc4-e8eb63f2c953
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
/dev/sda1       /	        ext4    errors=remount-ro 0       1
/dev/sda2	/home		ext4
/dev/sda3	/		xfs
/dev/sda4 	none            swap    sw           0       0
/dev/sda5	/webprogs	ext3
/dev/sda6	/video		ext3
/dev/sda7	/backup		ext3



=================== sda1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
  60.3GB: boot/grub/grub.cfg
    .1GB: boot/initrd.img-2.6.35-24-generic
  20.1GB: boot/initrd.img-2.6.35-25-generic
  20.2GB: boot/initrd.img-2.6.35-27-generic
   5.9GB: boot/initrd.img-2.6.35-27-generic-pae
  20.9GB: boot/initrd.img-2.6.35-28-generic
   4.4GB: boot/vmlinuz-2.6.35-24-generic
   4.4GB: boot/vmlinuz-2.6.35-25-generic
   5.9GB: boot/vmlinuz-2.6.35-27-generic
   5.9GB: boot/vmlinuz-2.6.35-28-generic
  20.9GB: initrd.img
  20.2GB: initrd.img.old
   5.9GB: vmlinuz
   5.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  e7 07 d9 88 07 63 77 0d  3f 19 0d 3f c8 0a 18 e2  |.....cw.?..?....|
00000010  d7 08 13 a4 78 24 bb 1e  93 24 87 36 9b 00 d6 84  |....x$...$.6....|
00000020  71 8b 8b 92 9c 20 69 3d  ef 57 78 2e 0b ac ab 5a  |q.... i=.Wx....Z|
00000030  f1 cf 0d 80 00 00 f1 bd  a4 e6 30 00 00 00 00 00  |..........0.....|
00000040  90 87 1c 0b 81 16 34 1a  0b c8 26 80 c2 cd 80 00  |......4...&.....|
00000050  00 00 92 af e6 5c b2 c9  bb 93 50 15 20 97 bd 01  |.....\....P. ...|
00000060  9b a1 d5 d7 77 a0 a3 03  de e0 30 68 82 46 9b 9b  |....w.....0h.F..|
00000070  76 df f5 b9 17 f1 11 80  f0 49 fc b0 02 ad d5 f4  |v........I......|
00000080  17 44 61 d1 d2 c4 fe 35  34 f0 87 e4 87 86 c0 00  |.Da....54.......|
00000090  90 87 1d 0b 95 ee a6 5f  9d ef 47 3f 30 41 0d 89  |......._..G?0A..|
000000a0  00 a1 8b 2d ef e4 2b b2  00 62 ba e5 da 04 53 c3  |...-..+..b....S.|
000000b0  84 ab bb 5b 52 71 10 4e  20 7f 14 32 1d 03 82 85  |...[Rq.N ..2....|
000000c0  a8 60 c3 f6 0f c6 a1 64  d4 5d 8c 03 0e 3d e4 d7  |.`.....d.]...=..|
000000d0  86 2d 2d 3e 03 71 f1 be  ab b5 d5 d8 3f 2a 3c 36  |.-->.q......?*<6|
000000e0  70 87 02 ff ff ff ff ff  00 fa fe e4 00 7b ff f6  |p............{..|
000000f0  00 7d 00 d8 00 89 01 3f  01 34 00 34 00 2e ff 83  |.}.....?.4.4....|
00000100  00 43 00 b4 ff 8e 00 3d  00 bd ff f0 ff 43 ff 82  |.C.....=.....C..|
00000110  00 1d ff 42 fe ce ff b9  ff cc ff e3 00 5d 00 0d  |...B.........]..|
00000120  00 09 ff 41 ff c8 ff 6b  ff 49 00 71 ff 71 00 00  |...A...k.I.q.q..|
00000130  90 87 1e 0f d6 04 8c 60  5c 5f c1 73 fc 4f c7 96  |.......`\_.s.O..|
00000140  69 df d4 1e 8d e0 6b 87  14 e1 07 0e 31 d0 fc 80  |i.....k.....1...|
00000150  d2 28 76 c7 2c 3c 69 bc  f1 d8 ce b9 20 af cf 94  |.(v.,<i..... ...|
00000160  58 5e e3 22 8f d0 0e f1  1f a5 87 45 0e 97 d1 c1  |X^.".......E....|
00000170  3c 6f ca 16 28 2e ed ac  1f b4 2c d7 54 1d 46 a6  |<o..(.....,.T.F.|
00000180  90 87 1f 0f 86 87 9c 40  0e 08 7f 8a 78 fa 4d 34  |.......@....x.M4|
00000190  9e 30 85 99 05 34 97 fd  8a b1 f9 31 89 a1 ed 50  |.0...4.....1...P|
000001a0  86 08 d0 69 3c 57 bf c0  7b 65 72 45 65 5f 87 07  |...i<W..{erEe_..|
000001b0  a0 a6 b1 4f 04 1c 1c 13  c4 a3 07 15 ff 9a 00 fe  |...O............|
000001c0  ff ff 83 fe ff ff 00 08  00 00 00 a8 73 09 00 fe  |............s...|
000001d0  ff ff 05 fe ff ff 00 b0  73 09 00 f8 7b 15 00 00  |........s...{...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically

```

I sure would appreciate any assistance you guys and gals would lend getting this solved!

Thanks,
-DON-

---

