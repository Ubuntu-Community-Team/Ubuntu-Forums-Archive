---
title: "Fresh install, unable to boot"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by Malakili on 2010-08-23
Hello All,

I'm totally new to ubuntu / linux so bare with me a little.

I've done a default install on ubuntu 10.04 64bit server edition on an Dell Edge R300 server from a USB stick. Everything seemed to go fine and I used GRUB to write to the MBR. Unfortunately when I reboot the machine it gets through the BIOS stage then when it tries to boot from the HDD it doesn nothing, the cursor just sits there blinking.

I am assuming it is something wrong with the setting in GRUB, but I am totally unsure on how I would go about changing them and what they might need changing to.

Any help would be greatly appreciated

Simon

---

### Post by lechien73 on 2010-08-23
Do you get a Grub prompt at all? Or does the problem happen before that?

You could try booting in again from your USB stick, downloading and running Boot Info Script from: [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Please post the results.txt file here, either as a text file or surrounded by [CODE] tags (highlight the text, then click the **#** button on the toolbar).

---

### Post by Malakili on 2010-08-23
No Grub prompt or anything, would it make any difference that I am running RAID 1 with a SAS/6iR Adapter?

Trying to figure out how to run that script from a the bootable USB drive now.

Cheers

Simon

---

### Post by lechien73 on 2010-08-23
Yes, that would make a difference. It could be that Grub has been installed to the MBR of one of the disks rather than to the MBR of the array itself.

The output of the Boot Info Script will be helpful, anyway - unless anyone here with experience in installing Grub on a RAID system can help more quickly.

---

### Post by Malakili on 2010-08-23
Sorry to sound like a total idiot, but I've downloaded the script and copied it to my USB drive on my machine.

Then on the server I've booted from the USB, gone to repair the install, it fails on the Detect and mount CD-ROM part as I am obiously doing it from USB and don't have a CD. So I've then gone to execute a shell and I'm stuck how to find and execute the script from there, sorry.

Simon

---

### Post by lechien73 on 2010-08-23
Of course - I forgot that the server disc doesn't have a Live CD option, sorry about that!

Just out of interest, what happens if you ask it to boot from the first hard disk in the system?

---

### Post by Malakili on 2010-08-23
I just get a flashing cursor and nothing happens.

---

### Post by Malakili on 2010-08-23
Made a LiveUSB of the desktop version and this is what came back from the script.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1027 MB, 1027604480 bytes
255 heads, 63 sectors/track, 124 cylinders, total 2007040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     2,007,039     2,006,977   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 249.0 GB, 248999051264 bytes
255 heads, 63 sectors/track, 30272 cylinders, total 486326272 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       194,559       192,512  83 Linux
/dev/sdb2             194,560    15,818,751    15,624,192  82 Linux swap / Solaris
/dev/sdb3          15,820,798   486,324,223   470,503,426   5 Extended
/dev/sdb5          15,820,800   251,070,463   235,249,664  83 Linux
/dev/sdb6         251,072,512   486,324,223   235,251,712  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        504E-4F77                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        bcd1bf69-5f8b-4e72-bb2a-c705f5a559cf   ext4                                     
/dev/sdb2        0f82971c-76c9-4a1a-97ab-9be7aa2cb152   swap                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        411ad311-1fd9-4fc5-967d-974a0a469f1d   ext4                                     
/dev/sdb6        32eb514e-ca4c-4f23-a474-ea1151c0d4eb   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/bcd1bf69-5f8b-4e72-bb2a-c705f5a559cf ext4       (rw,nosuid,nodev,uhelper=udisks)


============================= sdb1/grub/grub.cfg: =============================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 32eb514e-ca4c-4f23-a474-ea1151c0d4eb
if loadfont /share/grub/unicode.pf2 ; then
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
search --no-floppy --fs-uuid --set bcd1bf69-5f8b-4e72-bb2a-c705f5a559cf
set locale_dir=($root)/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set bcd1bf69-5f8b-4e72-bb2a-c705f5a559cf
    linux    /vmlinuz-2.6.32-24-generic root=UUID=411ad311-1fd9-4fc5-967d-974a0a469f1d ro   splash quiet
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set bcd1bf69-5f8b-4e72-bb2a-c705f5a559cf
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /vmlinuz-2.6.32-24-generic root=UUID=411ad311-1fd9-4fc5-967d-974a0a469f1d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set bcd1bf69-5f8b-4e72-bb2a-c705f5a559cf
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set bcd1bf69-5f8b-4e72-bb2a-c705f5a559cf
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-24-generic
    .0GB: vmlinuz-2.6.32-24-generic

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=411ad311-1fd9-4fc5-967d-974a0a469f1d /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=bcd1bf69-5f8b-4e72-bb2a-c705f5a559cf /boot           ext4    defaults        0       2
# /usr was on /dev/sdb6 during installation
UUID=32eb514e-ca4c-4f23-a474-ea1151c0d4eb /usr            ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=0f82971c-76c9-4a1a-97ab-9be7aa2cb152 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  ff ff 00 ff ff 00 ff ff  00 ff ff 00 ff ff 00 ff  |................|
00000010  ff 00 ff ff 00 ff ff 00  ff ff 00 ff ff 00 ff ff  |................|
00000020  00 ff ff 00 ff ff 00 ff  ff 00 ff ff 00 ff ff 00  |................|
00000030  ff ff 00 ff ff 00 ff ff  00 ff ff 00 ff ff 00 ff  |................|
00000040  ff 00 ff ff 00 ff ff 00  ff ff 00 ff ff 00 ff ff  |................|
00000050  00 ff ff 00 ff ff 00 ff  ff 00 ff ff 00 ff ff 00  |................|
00000060  ff ff 00 ff ff 00 ff ff  00 ff ff 00 ff ff 00 ff  |................|
00000070  ff 00 ff ff 00 ff ff 00  ff ff 00 ff ff 00 ff ff  |................|
00000080  00 ff ff 00 ff ff 00 ff  ff 00 ff ff 00 ff ff 00  |................|
00000090  ff ff 00 ff ff 00 ff ff  00 ff ff 00 ff ff 00 ff  |................|
000000a0  ff 00 ff ff 00 ff ff 00  ff ff 00 ff ff 00 ff ff  |................|
000000b0  00 ff ff 00 ff ff 00 ff  ff 00 ff ff 00 ff ff 00  |................|
000000c0  ff ff 00 ff ff 00 ff ff  00 ff ff 00 ff ff 00 ff  |................|
000000d0  ff 00 ff ff 00 ff ff 00  ff ff 00 ff ff 00 ff ff  |................|
000000e0  00 ff ff 00 ff ff 00 ff  ff 00 ff ff 00 ff ff 00  |................|
000000f0  ff ff 00 ff ff 00 ff ff  00 ff ff 00 ff ff 00 ff  |................|
00000100  ff 00 ff ff 00 ff ff 00  ff ff 00 ff ff 00 ff ff  |................|
00000110  00 ff ff 00 ff ff 00 ff  ff 00 ff ff 00 ff ff 00  |................|
00000120  ff ff 00 ff ff 00 ff ff  00 ff ff 00 ff ff 00 ff  |................|
00000130  ff 00 ff ff 00 ff ff 00  ff ff 00 ff ff 00 ff ff  |................|
00000140  00 ff ff 00 ff ff 00 ff  ff 00 ff ff 00 ff ff 00  |................|
00000150  ff ff 00 ff ff 00 ff ff  00 ff ff 00 ff ff 00 ff  |................|
00000160  ff 00 ff ff 00 ff ff 00  ff ff 00 ff ff 00 ff ff  |................|
00000170  00 ff ff 00 ff ff 00 ff  ff 00 ff ff 00 ff ff 00  |................|
00000180  ff ff 00 ff ff 00 ff ff  00 ff ff 00 ff ff 00 ff  |................|
00000190  ff 00 ff ff 00 ff ff 00  ff ff 00 ff ff 00 ff ff  |................|
000001a0  00 ff ff 00 ff ff 00 ff  ff 00 ff ff 00 ff ff 00  |................|
000001b0  ff ff 00 ff ff 00 ff ff  00 ff ff 00 ff ff 00 cb  |................|
000001c0  f4 d8 83 fe ff ff 02 00  00 00 00 a0 05 0e 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 a0  05 0e 00 b0 05 0e 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by lechien73 on 2010-08-24
So, I take it that your physical set-up is 2 x discs connected to your RAID controller, which are presented to the operating system as /dev/sdb

According to the output of bootinfoscript, Grub is not installed into the MBR of /dev/sdb, which probably explains why you're just getting the flashing cursor and nothing else.

From the Live USB you created, go to the terminal window and type:

```
sudo umount /media/bcd1bf69-5f8b-4e72-bb2a-c705f5a559cf
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Then reboot. For the first command, which has the long UUID string, just type /media/b and then press Tab to autocomplete.

---

### Post by Malakili on 2010-08-24
Progress!!

Now when I boot I get a GRUB prompt. Cheers

---

### Post by Malakili on 2010-08-24
Go figure, I just started with a clean install, but from a CD instead of the USB stick and it installed clean as a whistle, with the exact same settings as before.

Oh well, you live and learn I guess. Thanks for all your help.

Simon

---

