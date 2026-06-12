---
title: "Grub doesn't recognise WIndows 7"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by soulja786 on 2011-08-14
Hi Guys,

I am a complete newbie to Ubuntu and first time user, hopefully want to try it out and use it for some useful stuff.

I have 3 hard drives, 1 is for Windows 7 (My primary), 1 for Media/Downloads etc and 1 on which I have installed Ubuntu on just today. 

Installation went all good, except when I reconnected my other 2 hard drives and Set the Ubuntu drive to load first, GRUB doesn't pick up my Windows 7. 

Anyone have a solution for this? Couldn't find anything on the net specifically related to my scenario. 

I did read quite a few threads, and people have been asking to see some sort of script on bios/start up details. Here are mine:

Thank You for reading and helping! :) 

 

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        




---

### Post by coffeecat on 2011-08-14
> **soulja786 said:**
> Installation went all good, except when I reconnected my other 2 hard drives and Set the Ubuntu drive to load first, GRUB doesn't pick up my Windows 7. 

Does that mean that the drive with Windows was disconnected when you installed Ubuntu? If so, the grub installer would have been unaware of the presence of Windows and would not have included a Windows entry in the main grub.cfg configuration file.

Set the BIOS to boot from the Ubuntu drive, but keep the other two drives connected, boot into Ubuntu, open a terminal, and:

```
sudo update-grub
```

If I've misunderstood you, could we have the rest of the boot info script output, please? About 90% is missing! :) And please enclose it in code tags, not quote tags - for correct formatting.

---

### Post by soulja786 on 2011-08-16
Hi,

Thanks for your reply coffeecat. Yes you are correct, I did disconnet the other 2 drives when installing, to be safe?

sorry about the script, I thought it was too long so only added the first part.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

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

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   204,802,047   204,595,200   7 NTFS / exFAT / HPFS
/dev/sda3         204,802,048   976,769,023   771,966,976   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   480,010,239   480,008,192  83 Linux
/dev/sdb2         480,012,286   488,396,799     8,384,514   5 Extended
/dev/sdb5         480,012,288   488,396,799     8,384,512  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   160,083,967   160,081,920   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        9474183674181D94                       ntfs       System Reserved
/dev/sda2        EE08385C083825CD                       ntfs       Windows
/dev/sda3        66926B7C926B4F9B                       ntfs       Downloads and Media
/dev/sdb1        99797e3f-7682-4927-91ee-ef5e4ecc245a   ext4       
/dev/sdb5        5d140ee7-3294-4a0e-bcc0-c000746db76c   swap       
/dev/sdc1        9030E94E30E93BBA                       ntfs       Work

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/Windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/Downloads and Media fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 99797e3f-7682-4927-91ee-ef5e4ecc245a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 99797e3f-7682-4927-91ee-ef5e4ecc245a
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 99797e3f-7682-4927-91ee-ef5e4ecc245a
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=99797e3f-7682-4927-91ee-ef5e4ecc245a ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 99797e3f-7682-4927-91ee-ef5e4ecc245a
	echo	'Loading Linux 2.6.38-10-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=99797e3f-7682-4927-91ee-ef5e4ecc245a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 99797e3f-7682-4927-91ee-ef5e4ecc245a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 99797e3f-7682-4927-91ee-ef5e4ecc245a
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
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5d140ee7-3294-4a0e-bcc0-c000746db76c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 218.193855286 = 234.283868160  boot/grub/core.img                             1
 156.239543915 = 167.760932864  boot/grub/grub.cfg                             1
   1.047851562 = 1.125122048    boot/initrd.img-2.6.38-10-generic-pae          2
   0.860782623 = 0.924258304    boot/vmlinuz-2.6.38-10-generic-pae             1
   1.047851562 = 1.125122048    initrd.img                                     2
   0.860782623 = 0.924258304    vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by soulja786 on 2011-08-16
Actually, I have just run the sudo grub update command as you said in terminal, and it has successfully added the windows 7 loader. :) Thank You! :)

Ive got a few more questions regarding GRUB. Is there any way to remove the 'memory test' entries in the loader, and, is there any way for GRUB to load automatically instead of me holding down shift.?

Thanks! :)

---

### Post by Mark Phelps on 2011-08-16
The script result is what is to be expected when the Win7 drive was not connected.

Simply run the command that coffeecat suggested and you should be OK.

---

### Post by coffeecat on 2011-08-16
> **soulja786 said:**
> Is there any way to remove the 'memory test' entries in the loader

But, of course! Open a terminal, and:

```
sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub
```

> **soulja786 said:**
>  and, is there any way for GRUB to load automatically instead of me holding down shift.?

Do you mean that the grub menu is not showing unless you press shift? When you have a dual-boot with Windows, grub *should* be configured so that it shows the menu by default, but sometimes things go wrong with the configuration. If you mean that the menu is not showing, post the output of:

```
cat /etc/default/grub
```

**All** of it, please! :p There will be more than fits in a normal size terminal window so you'll need to scroll to highlight it all to copy. Highlight the output with the mouse, right-click and choose "copy". Then paste it into your post, but between code tags, please.

**EDIT**: not thinking straight - now that you've added Windows to the menu with update-grub, the menu may start to show. Let us know if that is so.

---

### Post by soulja786 on 2011-08-16
thanks a lot guys, CoffeeCat/Mark your help is much appreciated. I don't know if I ran that command for grub to load by default or because I added the windows entry, it does load automatically now when booting up. Also got rid of the memory entries :)

... any way to customise the GRUB bootloader screen? lol or am I pushing it :P... I'm hoping to learn more and pick up on Ubuntu so sorry about the noob'ness

---

### Post by coffeecat on 2011-08-16
> **soulja786 said:**
> ... any way to customise the GRUB bootloader screen? lol or am I pushing it

But, of course! :lol:

The simple and quick way with the version of grub that comes with Ubuntu 11.04 is to copy a .jpg, .png or .tga image to /boot/grub and then to run 'sudo update-grub' again. You need root privileges to copy to /boot/grub, so post back if you need help with that. The image then becomes the background for the grub menu. More here:

[http://ubuntuforums.org/showthread.php?t=1739412](http://ubuntuforums.org/showthread.php?t=1739412)

And more from drs305 (who has written a lot about grub in the forum):

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

But note drs305's opening comment in that thread about grub customizer and grub 1.99, which is what comes with Ubuntu 11.04. You might want to read that thread in detail before using grub customizer. The thread was started before the release of Ubuntu 11.04 when grub version 1.98 was the one that came with the then latest release of Ubuntu (10.10).

---

