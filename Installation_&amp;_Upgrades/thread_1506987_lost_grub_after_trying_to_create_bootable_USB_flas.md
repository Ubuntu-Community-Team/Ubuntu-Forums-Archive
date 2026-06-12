---
title: "lost grub after trying to create bootable USB flashdrive"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by starbuckk on 2010-06-11
(note: searched and found a few threads about this but none with answers)

I was trying to make a bootable USB Flash install. To be used on another machine actually. Did not want to risk initial install on the target machine for fear of screwing something up/

Ubuntu was working fine on the desktop until I tried this.  Now, when I try to boot without the USB installed, I get an error and a "grub rescue>" prompt.  I've searched, and made several attempts to solve this to no avail. Tried unmounting the usb drive and doing update-grub. No luck.

Tried to follow a couple different site directions and found that the instructions dont' work.  Specifically "sudo grub" says it can't find the program.

Found one page that said the only answer they could find was to reinstall ubuntu (!!!!).  Nooooooo.

My goal was to have a bootable USB drive for use on my windows laptop.  And my desktop same as always. But if I try to boot the machine without the USB it won't do it.

Someone had in response to another questin asked for a configuration post, so here below is my RESULTS.txt file:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

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

/dev/sda1    *          2,048     1,026,047     1,024,000  83 Linux
/dev/sda2           1,026,048   410,626,047   409,600,000  83 Linux
/dev/sda3         410,626,048   411,650,047     1,024,000  82 Linux swap / Solaris
/dev/sda4         411,665,625   976,768,064   565,102,440   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16026435072 bytes
255 heads, 63 sectors/track, 1948 cylinders, total 31301631 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    29,894,655    29,892,608  83 Linux
/dev/sdb2          29,896,702    31,299,583     1,402,882   5 Extended
/dev/sdb5          29,896,704    31,299,583     1,402,880  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9987adaf-7cc8-412f-bd49-1b06d76424d4   ext4                                     
/dev/sda2        cee84a32-723c-4b3f-b180-56a24cfc5439   ext4                                     
/dev/sda3        94b1f96b-7bcb-4ada-b1f4-577037863b2f   swap                                     
/dev/sda4        F81C2B271C2AE07C                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        e0165550-d03f-4090-b069-5418bcfa5c1b   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        277d57b6-05ca-4c00-adae-9034524f90db   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /boot                    ext4       (rw)
/dev/sdb1        /media/e0165550-d03f-4090-b069-5418bcfa5c1b ext4       (rw,nosuid,nodev,uhelper=udisks)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set cee84a32-723c-4b3f-b180-56a24cfc5439
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
search --no-floppy --fs-uuid --set 9987adaf-7cc8-412f-bd49-1b06d76424d4
set locale_dir=($root)/grub/locale
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9987adaf-7cc8-412f-bd49-1b06d76424d4
    linux    /vmlinuz-2.6.32-21-generic root=UUID=cee84a32-723c-4b3f-b180-56a24cfc5439 ro   quiet splash
    initrd    /initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9987adaf-7cc8-412f-bd49-1b06d76424d4
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /vmlinuz-2.6.32-21-generic root=UUID=cee84a32-723c-4b3f-b180-56a24cfc5439 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9987adaf-7cc8-412f-bd49-1b06d76424d4
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9987adaf-7cc8-412f-bd49-1b06d76424d4
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set f81c2b271c2ae07c
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: grub/core.img
    .2GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-21-generic
    .0GB: vmlinuz-2.6.32-21-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=cee84a32-723c-4b3f-b180-56a24cfc5439 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=9987adaf-7cc8-412f-bd49-1b06d76424d4 /boot           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=94b1f96b-7bcb-4ada-b1f4-577037863b2f none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


    .5GB: initrd.img
    .5GB: initrd.img.old
    .5GB: vmlinuz

================================ sda4/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set e0165550-d03f-4090-b069-5418bcfa5c1b
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set e0165550-d03f-4090-b069-5418bcfa5c1b
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
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e0165550-d03f-4090-b069-5418bcfa5c1b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e0165550-d03f-4090-b069-5418bcfa5c1b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e0165550-d03f-4090-b069-5418bcfa5c1b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e0165550-d03f-4090-b069-5418bcfa5c1b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e0165550-d03f-4090-b069-5418bcfa5c1b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e0165550-d03f-4090-b069-5418bcfa5c1b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9987adaf-7cc8-412f-bd49-1b06d76424d4
    linux /vmlinuz-2.6.32-21-generic root=UUID=cee84a32-723c-4b3f-b180-56a24cfc5439 ro quiet splash
    initrd /initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9987adaf-7cc8-412f-bd49-1b06d76424d4
    linux /vmlinuz-2.6.32-21-generic root=UUID=cee84a32-723c-4b3f-b180-56a24cfc5439 ro single
    initrd /initrd.img-2.6.32-21-generic
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set f81c2b271c2ae07c
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=277d57b6-05ca-4c00-adae-9034524f90db none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
   5.4GB: boot/grub/grub.cfg
   2.4GB: boot/initrd.img-2.6.32-21-generic
   2.2GB: boot/vmlinuz-2.6.32-21-generic
   2.4GB: initrd.img
   2.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  04 00 00 00 a8 11 b1 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
00000010  04 00 00 00 a8 31 b1 2f  00 00 00 00 e4 75 bf 0a  |.....1./.....u..|
00000020  04 00 00 00 a8 51 b1 2f  00 00 00 00 e4 75 bf 0a  |.....Q./.....u..|
00000030  04 00 00 00 a8 71 b1 2f  00 00 00 00 e4 75 bf 0a  |.....q./.....u..|
00000040  04 00 00 00 a8 91 b0 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
00000050  04 00 00 00 a8 b1 b0 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
00000060  04 00 00 00 a8 d1 b0 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
00000070  04 00 00 00 a8 f1 b0 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
00000080  04 00 00 00 a8 11 b0 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
00000090  04 00 00 00 a8 31 b0 2f  00 00 00 00 e4 75 bf 0a  |.....1./.....u..|
000000a0  00 00 00 00 11 02 00 00  98 14 0c 0d 20 00 00 00  |............ ...|
000000b0  04 00 00 00 a8 51 b0 2f  00 00 00 00 e4 75 bf 0a  |.....Q./.....u..|
000000c0  04 00 00 00 a8 71 b0 2f  00 00 00 00 e4 75 bf 0a  |.....q./.....u..|
000000d0  04 00 00 00 a8 91 cf 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
000000e0  04 00 00 00 a8 b1 cf 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
000000f0  04 00 00 00 a8 d1 cf 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
00000100  04 00 00 00 a8 f1 cf 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
00000110  04 00 00 00 a8 11 cf 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
00000120  04 00 00 00 a8 31 cf 2f  00 00 00 00 e4 75 bf 0a  |.....1./.....u..|
00000130  04 00 00 00 a8 51 cf 2f  00 00 00 00 e4 75 bf 0a  |.....Q./.....u..|
00000140  04 00 00 00 a8 71 cf 2f  00 00 00 00 e4 75 bf 0a  |.....q./.....u..|
00000150  04 00 00 00 a8 91 ce 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
00000160  04 00 00 00 a8 b1 ce 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
00000170  04 00 00 00 a8 d1 ce 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
00000180  04 00 00 00 a8 f1 ce 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
00000190  04 00 00 00 a8 11 ce 2f  00 00 00 00 e4 75 bf 0a  |......./.....u..|
000001a0  04 00 00 00 a8 31 ce 2f  00 00 00 00 e4 75 bf 0a  |.....1./.....u..|
000001b0  04 00 00 00 a8 51 ce 2f  00 00 00 00 e4 75 00 fe  |.....Q./.....u..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 68 15 00 00 00  |...........h....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by garvinrick4 on 2010-06-11
You are going to have to install grub2 from sda2 back into sda.

Put in your Live Cd.

Go into "disk utilitys" and label sda2 as lucid.

In disk utilitys also label sda1 as boot.
```

sudo mkdir /media/boot
``````
sudo mkdir /media/lucid
``````
sudo mount /dev/sda1 /media/boot
``````
sudo mount /dev/sda2 /media/lucid
```                          ```
sudo grub-install --recheck --root-directory=/media/lucid  [/dev/sda]("file:///media/dev/sda") 
``````
sudo umount /media/boot
``````
sudo umount /media/lucid
```Remove Live Cd boot into sda2
```

sudo update-grub
``````
sudo grub-mkconfig
```Now you will have just sda and no sdb in grub config file.


When you install always use sda never sda1 or sda2 or sda5 always sda.

If you install a sdb put grub in sdb on install if grub2 ok. It another type of grub then put your Live Cd in and do the install of grub from Ubuntu install sdax to sda. (x being your / install.)

---

### Post by bcbc on 2010-06-11
> **starbuckk said:**
> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.


Although bootinfoscript states that grub2 is loading from /dev/sda partition 1, there is a bug (or at least bootinfoscript needs to be updated for grub2 1.98 ) as it doesn't correctly identify the drive. I suspect it's really looking in partition 1 on /dev/sdb which you can confirm by viewing the first entry  ('e' to view/edit and ESC to return to menu). It will say "set root=(hd1,1)'"

First fix the flash:
Boot the first entry.
Then go to terminal and enter
```
sudo grub-install /dev/sdb
```

Then reboot. Now select your hard drive (that'll be the one that says "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda2)".Now go to a terminal and:
```
sudo grub-install /dev/sda
```

Remove flash and reboot. You'll only see your hard drive grub.
Boot from USB and you'll see your flash grub.

---

### Post by starbuckk on 2010-06-11
> **bcbc said:**
> Although bootinfoscript states that grub2 is loading from /dev/sda partition 1, there is a bug (or at least bootinfoscript needs to be updated for grub2 1.98 ) as it doesn't correctly identify the drive. I suspect it's really looking in partition 1 on /dev/sdb which you can confirm by viewing the first entry  ('e' to view/edit and ESC to return to menu). It will say "set root=(hd1,1)'"

First fix the flash:
Boot the first entry.
Then go to terminal and enter
```
sudo grub-install /dev/sdb
```Then reboot. Now select your hard drive (that'll be the one that says "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda2)".Now go to a terminal and:
```
sudo grub-install /dev/sda
```Remove flash and reboot. You'll only see your hard drive grub.
Boot from USB and you'll see your flash grub.


That did the trick! Solved the boot problem AND fixed my flash to be a portable install. Thanks for the answers guys!

---

### Post by bcbc on 2010-06-11
You're welcome :)

---

