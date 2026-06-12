---
title: "PANIC !!! Ubuntu Lucid is broken - HELP !!!"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by komitaltrade on 2010-05-24
I hav e broken Lucid.

1) I tried to reinstall grub from live usb without problem, but i still dont have grub menu on Shift. Instead it going to load, but than is stoped with message "(process:258): GLib-WARNING **: getpwuid_r(): failed due unknown user id (0)"

2) If nobody know what to do, I will try to do something, but how to enter in installed root from Live USB?

---

### Post by wilee-nilee on 2010-05-24
post this script in code tags. [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by OooBuntuRox on 2010-05-24
> **komitaltrade said:**
> I hav e broken Lucid.

1) I tried to reinstall grub from live usb without problem, but i still dont have grub menu on Shift. Instead it going to load, but than is stoped with message "(process:258): GLib-WARNING **: getpwuid_r(): failed due unknown user id (0)"

2) If nobody know what to do, I will try to do something, but how to enter in installed root from Live USB?

I did a google search and it looks like you're not alone. You can try going through the list if you're determined. At first glance, it looks like there isn't a solution yet. The links below are a place for you to start (if nothing else).

[http://ubuntuforums.org/showthread.php?t=1476454](http://ubuntuforums.org/showthread.php?t=1476454)

[http://www.google.com/#hl=en&source=hp&q=%28process%3A25%3A+GLib-WARNING+**%3A+getpwuid_r%28%29%3A+failed+due+unknown+user+id+%280%29%22&btnG=Google+Search&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=9e0a8bd7e5b81f0b](http://www.google.com/#hl=en&source=hp&q=%28process%3A25%3A+GLib-WARNING+**%3A+getpwuid_r%28%29%3A+failed+due+unknown+user+id+%280%29%22&btnG=Google+Search&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=9e0a8bd7e5b81f0b)

OooBuntuRox :guitar:

---

### Post by komitaltrade on 2010-05-25
Rox thanks. I'm completely destroyed. It is huge and and unforgivable mistake of Canonical to launch edition with bug without solution.

At least to know how to save and extract the files from system.

Somebody?

Wilee, I don't understand what you mean. I'm not able to approach on any part of the system. So, how I can put and where I can put the script??? From Live CD is no sense. So, I'm not able to boot or enter in system in any way.

---

### Post by komitaltrade on 2010-05-25
OK Wilee, I got it. I attached result.

---

### Post by wilee-nilee on 2010-05-25
I have posted on the site for easy access, I hope this os okay, so hold on
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *          2,048   619,229,183   619,227,136  83 Linux
/dev/sda2         619,231,230   625,141,759     5,910,530   5 Extended
/dev/sda5         619,231,232   625,141,759     5,910,528  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1998 MB, 1998471168 bytes
255 heads, 63 sectors/track, 242 cylinders, total 3903264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,887,729     3,887,667   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2001 MB, 2001731584 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3909632 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63     3,903,794     3,903,732   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        62fe31cf-fb7f-4849-ade2-5389b478d70d   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        59d2b953-6a3e-4e4b-9e69-8bd90b314322   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F0BE-6E8E                              vfat       LJUBA                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        7CB762771A311026                       ntfs       DATA                          
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 62fe31cf-fb7f-4849-ade2-5389b478d70d
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 62fe31cf-fb7f-4849-ade2-5389b478d70d
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 62fe31cf-fb7f-4849-ade2-5389b478d70d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=62fe31cf-fb7f-4849-ade2-5389b478d70d ro  splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 62fe31cf-fb7f-4849-ade2-5389b478d70d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=62fe31cf-fb7f-4849-ade2-5389b478d70d ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 62fe31cf-fb7f-4849-ade2-5389b478d70d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=62fe31cf-fb7f-4849-ade2-5389b478d70d ro  splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 62fe31cf-fb7f-4849-ade2-5389b478d70d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=62fe31cf-fb7f-4849-ade2-5389b478d70d ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 62fe31cf-fb7f-4849-ade2-5389b478d70d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 62fe31cf-fb7f-4849-ade2-5389b478d70d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
UUID=62fe31cf-fb7f-4849-ade2-5389b478d70d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=59d2b953-6a3e-4e4b-9e69-8bd90b314322 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  60.2GB: boot/grub/core.img
 217.1GB: boot/grub/grub.cfg
  62.3GB: boot/initrd.img-2.6.32-21-generic
  63.2GB: boot/initrd.img-2.6.32-22-generic
  62.9GB: boot/vmlinuz-2.6.32-21-generic
  62.3GB: boot/vmlinuz-2.6.32-22-generic
  63.2GB: initrd.img
  62.3GB: initrd.img.old
  62.3GB: vmlinuz
  62.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  df 02 5a 00 58 0b 5a 00  98 0b 5a 00 bc 0b 5a 00  |..Z.X.Z...Z...Z.|
00000010  f7 02 5a 00 11 03 5a 00  e4 0b 5a 00 08 0c 5a 00  |..Z...Z...Z...Z.|
00000020  44 0c 5a 00 64 0c 5a 00  1f 03 5a 00 a8 0c 5a 00  |D.Z.d.Z...Z...Z.|
00000030  34 03 5a 00 d4 0c 5a 00  4d 03 5a 00 64 03 5a 00  |4.Z...Z.M.Z.d.Z.|
00000040  81 03 5a 00 90 03 5a 00  97 03 5a 00 20 0d 5a 00  |..Z...Z...Z. .Z.|
00000050  a9 03 5a 00 c1 03 5a 00  dc 03 5a 00 44 0d 5a 00  |..Z...Z...Z.D.Z.|
00000060  f2 03 5a 00 80 0d 5a 00  0b 04 5a 00 90 03 5a 00  |..Z...Z...Z...Z.|
00000070  19 04 5a 00 90 03 5a 00  31 04 5a 00 a8 0d 5a 00  |..Z...Z.1.Z...Z.|
00000080  47 04 5a 00 55 04 5a 00  68 04 5a 00 7f 04 5a 00  |G.Z.U.Z.h.Z...Z.|
00000090  95 04 5a 00 ad 04 5a 00  bc 04 5a 00 e0 0d 5a 00  |..Z...Z...Z...Z.|
000000a0  d3 04 5a 00 14 0e 5a 00  f1 04 5a 00 3c 0e 5a 00  |..Z...Z...Z.<.Z.|
000000b0  0e 05 5a 00 68 0e 5a 00  2a 05 5a 00 ac 0e 5a 00  |..Z.h.Z.*.Z...Z.|
000000c0  43 05 5a 00 e4 0e 5a 00  60 05 5a 00 1c 0f 5a 00  |C.Z...Z.`.Z...Z.|
000000d0  54 0f 5a 00 74 0f 5a 00  75 05 5a 00 b0 0f 5a 00  |T.Z.t.Z.u.Z...Z.|
000000e0  93 05 5a 00 ad 05 5a 00  c2 05 5a 00 dc 0f 5a 00  |..Z...Z...Z...Z.|
000000f0  d9 05 5a 00 ee 05 5a 00  06 06 5a 00 19 06 5a 00  |..Z...Z...Z...Z.|
00000100  24 06 5a 00 3a 06 5a 00  4b 06 5a 00 66 06 5a 00  |$.Z.:.Z.K.Z.f.Z.|
00000110  84 06 5a 00 00 10 5a 00  99 06 5a 00 44 10 5a 00  |..Z...Z...Z.D.Z.|
00000120  b4 06 5a 00 c9 06 5a 00  e1 06 5a 00 8c 10 5a 00  |..Z...Z...Z...Z.|
00000130  f8 06 5a 00 0e 07 5a 00  1e 07 5a 00 37 07 5a 00  |..Z...Z...Z.7.Z.|
00000140  47 07 5a 00 60 07 5a 00  73 07 5a 00 8d 07 5a 00  |G.Z.`.Z.s.Z...Z.|
00000150  a1 07 5a 00 bd 07 5a 00  d7 07 5a 00 b0 10 5a 00  |..Z...Z...Z...Z.|
00000160  ea 07 5a 00 10 11 5a 00  00 00 00 00 00 00 00 00  |..Z...Z.........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  79 1a 5a 00 7d 1a 5a 00  81 1a 5a 00 85 1a 5a 00  |y.Z.}.Z...Z...Z.|
00000190  89 1a 5a 00 8d 1a 5a 00  91 1a 5a 00 95 1a 5a 00  |..Z...Z...Z...Z.|
000001a0  9c 1a 5a 00 a3 1a 5a 00  ab 1a 5a 00 b5 1a 5a 00  |..Z...Z...Z...Z.|
000001b0  be 1a 5a 00 c5 1a 5a 00  00 00 00 00 00 00 00 fe  |..Z...Z.........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 30 5a 00 00 00  |...........0Z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by wilee-nilee on 2010-05-25
I have limited skills in this so bear with me, and it was good that you post the script as there are people that are good at deciphering the problems.

So are sdb and sdc thumb drives? if they are unplug them and try booting from sda with the f12 key prompt at startup to choose the boot device. Both sdb and sdc read as 2 gigs in size if I read this script. Or are they a wireless device...etc.

If I am misreading the script it is okay, as I wont suggest anything that will change your setup at this point

---

### Post by komitaltrade on 2010-05-25
OK

As it talk about the user, I at final entered in system via Live CD (I made sudo passwd and than mounted /dev/sda1 on /mnt) and I scaned file system permissions with ls - l and home system also. File is attached.

P.S. I don[t have any idea why I have Boot Sector type windows, when I don[t have any other system except Ubuntu Lucid???

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:

---

### Post by komitaltrade on 2010-05-25
Yes, they are USB sticks (one with Live CD and one to make the copy of Readme).

Now, Readme1 is without sticks.

---

### Post by wilee-nilee on 2010-05-25
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   619,229,183   619,227,136  83 Linux
/dev/sda2         619,231,230   625,141,759     5,910,530   5 Extended
/dev/sda5         619,231,232   625,141,759     5,910,528  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        62fe31cf-fb7f-4849-ade2-5389b478d70d   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        59d2b953-6a3e-4e4b-9e69-8bd90b314322   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt/repair              ext4       (rw)
/dev/sda1        /mnt                     ext4       (rw)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  df 02 5a 00 58 0b 5a 00  98 0b 5a 00 bc 0b 5a 00  |..Z.X.Z...Z...Z.|
00000010  f7 02 5a 00 11 03 5a 00  e4 0b 5a 00 08 0c 5a 00  |..Z...Z...Z...Z.|
00000020  44 0c 5a 00 64 0c 5a 00  1f 03 5a 00 a8 0c 5a 00  |D.Z.d.Z...Z...Z.|
00000030  34 03 5a 00 d4 0c 5a 00  4d 03 5a 00 64 03 5a 00  |4.Z...Z.M.Z.d.Z.|
00000040  81 03 5a 00 90 03 5a 00  97 03 5a 00 20 0d 5a 00  |..Z...Z...Z. .Z.|
00000050  a9 03 5a 00 c1 03 5a 00  dc 03 5a 00 44 0d 5a 00  |..Z...Z...Z.D.Z.|
00000060  f2 03 5a 00 80 0d 5a 00  0b 04 5a 00 90 03 5a 00  |..Z...Z...Z...Z.|
00000070  19 04 5a 00 90 03 5a 00  31 04 5a 00 a8 0d 5a 00  |..Z...Z.1.Z...Z.|
00000080  47 04 5a 00 55 04 5a 00  68 04 5a 00 7f 04 5a 00  |G.Z.U.Z.h.Z...Z.|
00000090  95 04 5a 00 ad 04 5a 00  bc 04 5a 00 e0 0d 5a 00  |..Z...Z...Z...Z.|
000000a0  d3 04 5a 00 14 0e 5a 00  f1 04 5a 00 3c 0e 5a 00  |..Z...Z...Z.<.Z.|
000000b0  0e 05 5a 00 68 0e 5a 00  2a 05 5a 00 ac 0e 5a 00  |..Z.h.Z.*.Z...Z.|
000000c0  43 05 5a 00 e4 0e 5a 00  60 05 5a 00 1c 0f 5a 00  |C.Z...Z.`.Z...Z.|
000000d0  54 0f 5a 00 74 0f 5a 00  75 05 5a 00 b0 0f 5a 00  |T.Z.t.Z.u.Z...Z.|
000000e0  93 05 5a 00 ad 05 5a 00  c2 05 5a 00 dc 0f 5a 00  |..Z...Z...Z...Z.|
000000f0  d9 05 5a 00 ee 05 5a 00  06 06 5a 00 19 06 5a 00  |..Z...Z...Z...Z.|
00000100  24 06 5a 00 3a 06 5a 00  4b 06 5a 00 66 06 5a 00  |$.Z.:.Z.K.Z.f.Z.|
00000110  84 06 5a 00 00 10 5a 00  99 06 5a 00 44 10 5a 00  |..Z...Z...Z.D.Z.|
00000120  b4 06 5a 00 c9 06 5a 00  e1 06 5a 00 8c 10 5a 00  |..Z...Z...Z...Z.|
00000130  f8 06 5a 00 0e 07 5a 00  1e 07 5a 00 37 07 5a 00  |..Z...Z...Z.7.Z.|
00000140  47 07 5a 00 60 07 5a 00  73 07 5a 00 8d 07 5a 00  |G.Z.`.Z.s.Z...Z.|
00000150  a1 07 5a 00 bd 07 5a 00  d7 07 5a 00 b0 10 5a 00  |..Z...Z...Z...Z.|
00000160  ea 07 5a 00 10 11 5a 00  00 00 00 00 00 00 00 00  |..Z...Z.........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  79 1a 5a 00 7d 1a 5a 00  81 1a 5a 00 85 1a 5a 00  |y.Z.}.Z...Z...Z.|
00000190  89 1a 5a 00 8d 1a 5a 00  91 1a 5a 00 95 1a 5a 00  |..Z...Z...Z...Z.|
000001a0  9c 1a 5a 00 a3 1a 5a 00  ab 1a 5a 00 b5 1a 5a 00  |..Z...Z...Z...Z.|
000001b0  be 1a 5a 00 c5 1a 5a 00  00 00 00 00 00 00 00 fe  |..Z...Z.........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 30 5a 00 00 00  |...........0Z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/home/ubuntu/boot_info_script055.sh: line 1266: cd: /mnt/repair/: No such file or directory
```

---

### Post by komitaltrade on 2010-05-25
To not be confused, /mnt and /mnt/repair are folders in Live CD where I mounted original file system (so, dont look at it).

---

### Post by wilee-nilee on 2010-05-25
I don't see a operating system installed to sda, I may be wrong on this though. I am assuming that sda is the hard drive inside the computer and that it is not broken.,

I think a more experienced user will be more helpful. 

To much information is missing, such as did you have a running Ubuntu setup to begin with that failed and you tried to fix grub? Was this a install that has never worked, or was this a upgrade from hardy or Karmic or some other distro that has now failed.

---

### Post by komitaltrade on 2010-05-25
1) I dont think how problem is in grub (but, it is strange how I cant open the Grub with Shift!!!). 

2) Sysytem is not fresh.

3) As getpwuid function shall search the user database for an entry with a matching *uid, *it mean (I think) how I have the problem with (at least) one user. It can be user wick (see file with permissions), but I dont want to delete him.

As I changed his permission (to drwxr-xr-x or 444 from d---------), question is

- what count permission with UID (maybe because I did it in terminal and not in GUI???)?
- how to go back now (if it count)?

As I can mount filesystem in Live CD mnt, I think how it can be repaired, but how (I can experiment, but I dont like it anymore)?

---

### Post by wilee-nilee on 2010-05-25
I don't understand any of your last post I think we may have a language barrier here, or I don't understand.

Did you run the script from the live cd on either post of the script? that is how it is done.

Can you boot with a live cd, and can you access the hard drive from the home sidebar, if so what do you see?

Is this your computer and are you using it directly?

There is something suspicious about this whole thread in some instances your use of the English language is understandable in other posts is as if it is another person.

Good luck I am done trying.

---

### Post by komitaltrade on 2010-05-25
yes, I run the script from Live CD, but I wrote how meessage on boot dont mean how something is wrong with Grub (thats confirmed also with script).

I wrote how message about getpwuid mean how problem is with user. See message in my original post and link [http://www.opengroup.org/onlinepubs/009695399/functions/getpwuid.html](http://www.opengroup.org/onlinepubs/009695399/functions/getpwuid.html)

I just cant figure what is conection between user permissions and UID (if you see my file with permissions, you can see how i set just wick like ordinary desktop user to have root rights - others are originally with root permissions).

I found on RedHat how umask should be 002, but Im not sure on that and also how exactly to do it.

I gues how I can mount filesystem in Live CD /mnt and than create sudo passwd to access to mnt and to /home/wick. So,to type umask 002 /home/wick, but Im not sure in that. I need confirmations.


Wilee, you helped to find how bunch of the users who have those message dont have the problem with boot (Grub), it is problem with umask the user and his UID.

---

