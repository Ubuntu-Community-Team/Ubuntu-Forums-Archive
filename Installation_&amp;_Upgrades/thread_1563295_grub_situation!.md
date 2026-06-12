---
title: "grub situation!"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by M93 on 2010-08-28
how can i install grub and make it the default?

---

### Post by presence1960 on 2010-08-28
> **M93 said:**
> how can i install grub and make it the default?

That is such a vague question since we know nothing about your setup or boot process. If you want a starting point we need way more info. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by M93 on 2010-08-28
i dont have a liveCD...i used wubi to install
when i wrote the code it gave>>
bash: /home/mahmoud/Desktop/boot_info_script*.sh: No such file or directory

forgive me for being a total noob:)

---

### Post by M93 on 2010-08-28
im trying to make a liveCD but it tells me >>
please replace the disc with a supported CD or DVD <<

although the dvd i put is brand new DVD-R 1x-16x

---

### Post by Rubi1200 on 2010-08-28
If you have a Wubi install and want to make Ubuntu the default for booting see here:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?)

---

### Post by wilee-nilee on 2010-08-28
> **M93 said:**
> im trying to make a liveCD but it tells me >>
please replace the disc with a supported CD or DVD <<

although the dvd i put is brand new DVD-R 1x-16x

You need to use a cd-r or load it to a thumb drive using unetbootin.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Do not try to install grub it is not the full install in Wubi.

---

### Post by M93 on 2010-08-28
> **wilee-nilee said:**
> You need to use a cd-r or load it to a thumb drive using unetbootin.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Do not try to install grub it is not the full install in Wubi.

ive downloaded it and set bios to read from usb first...
then restart..it says >>
grub>

---

### Post by wilee-nilee on 2010-08-29
> **M93 said:**
> ive downloaded it and set bios to read from usb first...
then restart..it says >>
grub>

Does it give you the same grub prompt without the thumb plugged in?

Since you have a Wubi install at some point did you have a grub update that you did and installed somewhere like sda?

You can get a choice of boot from with a f-key prompt, mine is f12 it could even be esc. Sometimes just setting the bios to read will bypass the one you want, when the key prompt for a boot choice works.

---

### Post by M93 on 2010-08-29
> **wilee-nilee said:**
> Does it give you the same grub prompt without the thumb plugged in?


yes, thats why i thought of re-doing it, right?

---

### Post by M93 on 2010-08-29
ok it worked this time :)
now im in ubuntu from the usb

---

### Post by wilee-nilee on 2010-08-29
> **M93 said:**
> ok it worked this time :)
now im in ubuntu from the usb

You should go to the bootscript link in my signature download it drag it to the desktop, then run the command presence1960 gave you it is on the links page as well.

This will deposit a file on the desktop, then come back to your thread while on the Live desktop and post the script from that new file in a reply; **highlight the whole text and click on the # in the reply top panel.**

---

### Post by presence1960 on 2010-08-29
> **M93 said:**
> i dont have a liveCD...i used wubi to install
when i wrote the code it gave>>
bash: /home/mahmoud/Desktop/boot_info_script*.sh: No such file or directory

forgive me for being a total noob:)

From ubuntu download the script from the link in my signature. Once downloaded move the file to Desktop. Now open a terminal and run that command.

---

### Post by M93 on 2010-08-29
.

---

### Post by M93 on 2010-08-29
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

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
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /wubildr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    21,194,751    21,192,704  27 Hidden HPFS/NTFS
/dev/sda2    *     21,194,752   432,002,855   410,808,104   7 HPFS/NTFS
/dev/sda3         432,003,070   488,396,799    56,393,730   5 Extended
/dev/sda5         432,003,072   485,976,063    53,972,992  83 Linux
/dev/sda6         485,978,112   488,396,799     2,418,688  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       a45e7702-fff3-4de9-934e-a4ca02643f6c   ext4                                     
/dev/sda1        E8CE6EEDCE6EB40A                       ntfs       Recovery                      
/dev/sda2        6E9CF5F59CF5B823                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        8a32facb-bdaa-4b03-a41f-9ed7b5f3081a   ext4                                     
/dev/sda6        cf3b8262-ca1c-488c-b9a0-8edff1e1ac6a   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

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
}

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
menuentry "Ubuntu, Linux 2.6.35-19-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6e9cf5f59cf5b823
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-19-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-19-generic
}
menuentry "Ubuntu, Linux 2.6.35-19-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6e9cf5f59cf5b823
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-19-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-19-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6e9cf5f59cf5b823
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6e9cf5f59cf5b823
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e8ce6eedce6eb40a
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6e9cf5f59cf5b823
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

============================= sda2/Wubi/etc/fstab: =============================

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

================= sda2/Wubi: Location of files loaded by Grub: =================


   4.6GB: boot/grub/grub.cfg
   1.9GB: boot/initrd.img-2.6.32-24-generic
   4.0GB: boot/initrd.img-2.6.35-19-generic
   8.7GB: boot/vmlinuz-2.6.32-24-generic
   8.8GB: boot/vmlinuz-2.6.35-19-generic
   4.0GB: initrd.img
   1.9GB: initrd.img.old
   8.8GB: vmlinuz
   8.7GB: vmlinuz.old

=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 8a32facb-bdaa-4b03-a41f-9ed7b5f3081a
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 8a32facb-bdaa-4b03-a41f-9ed7b5f3081a
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8a32facb-bdaa-4b03-a41f-9ed7b5f3081a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8a32facb-bdaa-4b03-a41f-9ed7b5f3081a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8a32facb-bdaa-4b03-a41f-9ed7b5f3081a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8a32facb-bdaa-4b03-a41f-9ed7b5f3081a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8a32facb-bdaa-4b03-a41f-9ed7b5f3081a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8a32facb-bdaa-4b03-a41f-9ed7b5f3081a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e8ce6eedce6eb40a
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6e9cf5f59cf5b823
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=8a32facb-bdaa-4b03-a41f-9ed7b5f3081a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cf3b8262-ca1c-488c-b9a0-8edff1e1ac6a none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 225.6GB: boot/grub/core.img
 234.8GB: boot/grub/grub.cfg
 225.8GB: boot/initrd.img-2.6.32-21-generic
 225.6GB: boot/vmlinuz-2.6.32-21-generic
 225.8GB: initrd.img
 225.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  6e 00 44 00 61 00 74 00  61 00 2d 00 6f 00 6d 00  |n.D.a.t.a.-.o.m.|
00000010  69 00 6e 00 61 00 69 00  73 00 75 00 75 00 73 00  |i.n.a.i.s.u.u.s.|
00000020  2e 00 00 00 68 00 01 00  54 00 69 00 65 00 64 00  |....h...T.i.e.d.|
00000030  6f 00 73 00 74 00 6f 00  61 00 20 00 5b 00 32 00  |o.s.t.o.a. .[.2.|
00000040  5d 00 20 00 65 00 69 00  20 00 76 00 6f 00 69 00  |]. .e.i. .v.o.i.|
00000050  20 00 61 00 76 00 61 00  74 00 61 00 20 00 6b 00  | .a.v.a.t.a. .k.|
00000060  69 00 72 00 6a 00 6f 00  69 00 74 00 74 00 61 00  |i.r.j.o.i.t.t.a.|
00000070  6d 00 69 00 73 00 74 00  61 00 20 00 76 00 61 00  |m.i.s.t.a. .v.a.|
00000080  72 00 74 00 65 00 6e 00  2e 00 00 00 60 00 01 00  |r.t.e.n.....`...|
00000090  4d 00 65 00 72 00 6b 00  6b 00 69 00 6a 00 6f 00  |M.e.r.k.k.i.j.o.|
000000a0  6e 00 6f 00 61 00 20 00  5b 00 32 00 5d 00 20 00  |n.o.a. .[.2.]. .|
000000b0  65 00 69 00 20 00 76 00  6f 00 69 00 20 00 6d 00  |e.i. .v.o.i. .m.|
000000c0  75 00 75 00 6e 00 74 00  61 00 61 00 20 00 4f 00  |u.u.n.t.a.a. .O.|
000000d0  45 00 4d 00 2d 00 6d 00  65 00 72 00 6b 00 65 00  |E.M.-.m.e.r.k.e.|
000000e0  69 00 6b 00 73 00 69 00  2e 00 00 00 60 00 01 00  |i.k.s.i.....`...|
000000f0  4b 00 61 00 6e 00 73 00  69 00 6f 00 74 00 61 00  |K.a.n.s.i.o.t.a.|
00000100  20 00 5b 00 32 00 5d 00  20 00 65 00 69 00 20 00  | .[.2.]. .e.i. .|
00000110  76 00 6f 00 69 00 20 00  6d 00 75 00 75 00 6e 00  |v.o.i. .m.u.u.n.|
00000120  74 00 61 00 61 00 20 00  6c 00 79 00 68 00 79 00  |t.a.a. .l.y.h.y.|
00000130  65 00 6b 00 73 00 69 00  20 00 70 00 6f 00 6c 00  |e.k.s.i. .p.o.l.|
00000140  75 00 6b 00 73 00 69 00  2e 00 00 00 6c 00 01 00  |u.k.s.i.....l...|
00000150  54 00 65 00 6b 00 73 00  74 00 69 00 74 00 69 00  |T.e.k.s.t.i.t.i.|
00000160  65 00 64 00 6f 00 73 00  74 00 6f 00 61 00 20 00  |e.d.o.s.t.o.a. .|
00000170  5b 00 32 00 5d 00 20 00  65 00 69 00 20 00 76 00  |[.2.]. .e.i. .v.|
00000180  6f 00 69 00 20 00 61 00  76 00 61 00 74 00 61 00  |o.i. .a.v.a.t.a.|
00000190  20 00 6c 00 75 00 6b 00  65 00 6d 00 69 00 73 00  | .l.u.k.e.m.i.s.|
000001a0  74 00 61 00 20 00 76 00  61 00 72 00 74 00 65 00  |t.a. .v.a.r.t.e.|
000001b0  6e 00 2e 00 00 00 00 00  64 00 01 00 4d 00 00 fe  |n.......d...M...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 37 03 00 fe  |............7...|
000001d0  ff ff 05 fe ff ff 02 90  37 03 00 f0 24 00 00 00  |........7...$...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb
```

u can ignore the wubi part i wont use it, i'll uninstall it later today
and if theres a way to get rid of the vista part i'd be really grateful :)

---

### Post by M93 on 2010-08-29
i got grub working as soon as i restarted the pc:):)

---

### Post by wilee-nilee on 2010-08-29
> **M93 said:**
> i got grub working as soon as i restarted the pc:):)

The script looks good, it sounds like it is working now.

In the future just try to post all the operating systems you have installed otherwise it makes it really hard to know whats up. ;)

If you want to get rid of Vista, which if it is a OEM I would just shrink and leave on, you can remove it with gparted in Ubuntu. Just run after doing this in Ubuntu before rebooting
```
sudo update-grub
```

The only thing I would add is it appears that sda1 is the Vista recovery partition and sda2 is the main Vista OS.

---

### Post by M93 on 2010-08-29
> **wilee-nilee said:**
> The script looks good, it sounds like it is working now.

In the future just try to post all the operating systems you have installed otherwise it makes it really hard to know whats up. ;)

If you want to get rid of Vista, which if it is a OEM I would just shrink and leave on, you can remove it with gparted in Ubuntu. Just run after doing this in Ubuntu before rebooting
```
sudo update-grub
```

The only thing I would add is it appears that sda1 is the Vista recovery partition and sda2 is the main Vista OS.

i installed gparted, removed the 10GB vista part
but now i cant expand the ubuntu
gparted only allow me to make a new primary part or leave it unallocated...what shall i do?
i want to add that 10GB to the ubuntu part

---

### Post by M93 on 2010-08-29
> **wilee-nilee said:**
> The script looks good, it sounds like it is working now.

In the future just try to post all the operating systems you have installed otherwise it makes it really hard to know whats up. ;)


im sry bout that...im still learning what do i need to know to solve a problem...so thank u for giving this tip
i'll take care bout that nxt time ;)

---

### Post by wilee-nilee on 2010-08-30
> **M93 said:**
> i installed gparted, removed the 10GB vista part
but now i cant expand the ubuntu
gparted only allow me to make a new primary part or leave it unallocated...what shall i do?
i want to add that 10GB to the ubuntu part

Sorry for the delay the instant email through yahoo is not working.

To expand the Ubuntu partition just right click on the swap and turn it off, to allow this change.

---

### Post by M93 on 2010-08-30
i turned it off but i found nthn different still i can only make primary part
and the only part i can extend is the sda2 (win7 195GB)
while i want to extend the ubuntu part
i'll upload a screenshot maybe it could be more helpful

and dont worry bout the delay u've walked me through alot, thank u :)

---

### Post by M93 on 2010-08-30
heres the screenshot i hope it helps :)

---

### Post by wilee-nilee on 2010-08-30
> **M93 said:**
> heres the screenshot i hope it helps :)

You said you wanted to get rid of the vista part, which is actually W7 and is sda2.

The only way to expand the Ubuntu is to shrink sda2, or reformatting it to something else leaving a blank space for Ubuntu to expand to. Ubuntu is also inside a extended partition=sda3 so that has to be expanded 1st.

You don't want any windows am I correct here?

---

### Post by M93 on 2010-08-30
i want the sda2 its win7, but i also want to increase ubuntu(sda5) by that 'unallocated' 10GB
u said i have to shrink sda2 to expand sda5...can i do that then add those 10GB to sda2?

---

### Post by wilee-nilee on 2010-08-30
> **M93 said:**
> i want the sda2 its win7, but i also want to increase ubuntu(sda5) by that 'unallocated' 10GB
u said i have to shrink sda2 to expand sda5...can i do that then add those 10GB to sda2?

First lets get to a situation where we are understanding each other.

Was sda1 your recovery for W7, and does W7 boot now? Do you have a backup or reinstall disc for W7. What was it?

I have heard that moving a NTFS partition around or expanding to the left is not a good idea and will probably result in losing the OS. I may be wrong but better safe then sorry hopefully others will help here.

I recognize that you want the extra space allocated to Ubuntu but as it is right now I'm not sure about what to do other then see if W7 boots going to it's disc manager and see if it will expand into the space in front of it and then work. If W7 will exspand with it's virtual partitioner then I would reboot it and then shrink it to allow room for Ubuntu. Not sure if this will work, but you should have everything backed up, and have the ability to reinstall both OS no matter what, before doing anything.

Really you need another HD your W7 partition is 90% full about 75% is advised. I'm not sure with having the partition that full that expanding then shrinking is going to work very well, you sort of have your cart in front of the horse here. You might be best to expand W7 and not put anymore into it then you have to then get another HD to store and use as wanted.

---

### Post by M93 on 2010-08-30
sda1 was vista recovery...deleted and now its a free space
sda2 is W7 the OS...and yes it boots
i do have an iso

> Really you need another HD your W7 partition is 90% full about 75% is advised
yes i know that thats y i have this thread where i was trying to get tips about choosing one
[http://ubuntuforums.org/showthread.php?t=1563117](http://ubuntuforums.org/showthread.php?t=1563117)

---

### Post by M93 on 2010-08-30
> Re: Resizing Linux partition with windows ?
originally posted by: [http://ubuntuforums.org/member.php?u=749318](http://ubuntuforums.org/member.php?u=749318)
If you download gparted from the USC it'll be on your hard drive meaning you can't use to partition your hard drive!! Use a Live CD (either Gparted itself or Ubuntu) and use it to partition your hard drive.

is that true?

---

### Post by wilee-nilee on 2010-08-30
From what I understand gparted can be used to resize W7 if you turn of the round to cylinders, mine is showing on.
[ATTACH]168003[/ATTACH]

Your problem is that you want to expand it to the right, to the front of the disc as it is seen in your gparted shot, this as far as I know can bork it. Gparted can be used in the other direction, but if the windows disk manager is usable it is the best choice.

I would try just for more info the W7 forums.
[http://www.sevenforums.com/](http://www.sevenforums.com/)
Just post a screen shot/snip of the windows disk manager when you post there.

---

### Post by M93 on 2010-08-30
i did that liveUSB thing and the partitioning went fine but when i load win7 it tells me to put the installation cd to fix a problem so i'll do that n come back

---

### Post by wilee-nilee on 2010-08-30
> **M93 said:**
> i did that liveUSB thing and the partitioning went fine but when i load win7 it tells me to put the installation cd to fix a problem so i'll do that n come back

If the auto repair doesn't work here are the commands you may need. You can always reload the grub bootloader so don't worry about running the fixmbr command if needed and any others.
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /f/r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by M93 on 2010-08-31
i removed win7 totally after i gathered some of wut i needed files
and gave all the space to ubuntu and its working gr8 now :)
thank u alot! :)

---

