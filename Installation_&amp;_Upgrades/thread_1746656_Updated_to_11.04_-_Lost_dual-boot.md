---
title: "Updated to 11.04 - Lost dual-boot"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by Narhinik on 2011-05-02
Hey, yesterday I decided to update from 10.10 to 11.04.

I was using Windows Vista in dual-boot with Ubuntu but after updating Ubuntu to 11.04 I lost my dual-boot menu. It worked without problems before update. Now it starts automatically to Ubuntu log in screen.

I have used Ubuntu for 1 month now and I'm a newbie with this, so please explain with easy step-by-step guide :)

I've tried so far:

1. Updating GRUB via terminal
2. Looked at my menu entries 
```

grep menuentry /boot/grub/grub.cfg

menuentry 'Ubuntu, Linux-ydin 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, Linux-ydin 2.6.38-8-generic (toipumistila)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, Linux-ydin 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, Linux-ydin 2.6.35-28-generic (toipumistila)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
menuentry "Windows NT/2000/XP (on /dev/sda2)" --class windows --class os {
```(Toipumistila is probably "Recovery mode" in English, my system is in Finnish)

---

### Post by Hedgehog1 on 2011-05-02
We need some information about your partitions so we can help.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by Narhinik on 2011-05-02
Attached a file what happened when I tried to boot the LiveCD. Did this happen because the files on disc has been broken or has my PC gone mad? This same CD was used to install ubuntu 2 days ago and there were no problems.

I guess I'll have to burn a new disc.

---

### Post by kdnoel on 2011-05-05
#                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2can.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   496,376,369   496,376,307   7 HPFS/NTFS
/dev/sda2         496,376,370   976,768,064   480,391,695   5 Extended
/dev/sda5         496,376,433   967,723,469   471,347,037  83 Linux
/dev/sda6         967,723,533   976,768,064     9,044,532  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1EE4DCBFE4DC99FB                       ntfs       Noel                          
/dev/sda2: PTTYPE="dos" 
/dev/sda5        baf642ba-5f75-43f9-9440-effd3ed8e070   ext4                                     
/dev/sda6        53395b7e-ee52-4e15-9afa-30a3f1f9cde6   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=20

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
search --no-floppy --fs-uuid --set=root baf642ba-5f75-43f9-9440-effd3ed8e070
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root baf642ba-5f75-43f9-9440-effd3ed8e070
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
	search --no-floppy --fs-uuid --set=root baf642ba-5f75-43f9-9440-effd3ed8e070
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=baf642ba-5f75-43f9-9440-effd3ed8e070 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root baf642ba-5f75-43f9-9440-effd3ed8e070
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=baf642ba-5f75-43f9-9440-effd3ed8e070 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root baf642ba-5f75-43f9-9440-effd3ed8e070
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=baf642ba-5f75-43f9-9440-effd3ed8e070 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root baf642ba-5f75-43f9-9440-effd3ed8e070
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=baf642ba-5f75-43f9-9440-effd3ed8e070 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
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
	search --no-floppy --fs-uuid --set=root baf642ba-5f75-43f9-9440-effd3ed8e070
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root baf642ba-5f75-43f9-9440-effd3ed8e070
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 1EE4DCBFE4DC99FB
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=baf642ba-5f75-43f9-9440-effd3ed8e070 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=53395b7e-ee52-4e15-9afa-30a3f1f9cde6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 254.2GB: boot/grub/core.img
 259.7GB: boot/grub/grub.cfg
 278.7GB: boot/initrd.img-2.6.35-28-generic
 280.2GB: boot/initrd.img-2.6.38-8-generic
 257.2GB: boot/vmlinuz-2.6.35-28-generic
 279.0GB: boot/vmlinuz-2.6.38-8-generic
 280.2GB: initrd.img
 278.7GB: initrd.img.old
 279.0GB: vmlinuz
 257.2GB: vmlinuz.old

---

### Post by kdnoel on 2011-05-05
Hedge
Didn't start a new thread but succeeded at posting my results... what next?

Thanks!

---

### Post by wilee-nilee on 2011-05-05
> **kdnoel said:**
> Hedge
Didn't start a new thread but succeeded at posting my results... what next?

Thanks!

I don't see Vista, look closer at the script, or look at the HD with gparted in Ubuntu, there is XP in sda1.

Please wrap that text using the instructions in my signature, it's difficult to read other wise. For example, I use the as a example, as it shows your only windows install, XP
```
sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM
```

So you had vista or xp is the question here, or both.

---

### Post by kdnoel on 2011-05-07
Xp is the other operating system.

Thanks for the input!

---

### Post by kansasnoob on 2011-05-07
> **kdnoel said:**
> Xp is the other operating system.

Thanks for the input!

You're scattering things about:

[http://ubuntuforums.org/showpost.php?p=10775072&postcount=7](http://ubuntuforums.org/showpost.php?p=10775072&postcount=7)

> Don't feel lonely... I upgraded via Internet and have lost my option to boot to Ubuntu or Xp.

I get an out of range message and then finally boot to Ubuntu.

I just noticed in the above signature a link to directions... both via live cd and internet update.

I'll go try it and see if it works.


I'm guessing the out-of-range error has to do with graphics. But you really need to start your own thread and explain your problem as best you can.

Also include the output of these commands:

```
lspci | grep VGA
```

```
uname -m
```

---

### Post by kansasnoob on 2011-05-07
If you're unsure how to start a new thread just go to this page:

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

Click on "New Thread" on the left hand side of the screen. I have a strong suspicion that I know what's wrong but I need to gather some info first ;)

---

### Post by kansasnoob on 2011-05-08
@ kdnoel,

This is a huge guess since you never replied any further but I suspect the same problem I spoke of here:

[http://ubuntuforums.org/showpost.php?p=10786957&postcount=12](http://ubuntuforums.org/showpost.php?p=10786957&postcount=12)

---

### Post by Narhinik on 2011-05-27
Here is the script, sorry that it took this long to answer. I moved into a new home and my ISP messed up my adress

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sde and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sde2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sde3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sde5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sde _____________________________________________________________________

Disk /dev/sde: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             63   261,555,057   261,554,995   7 NTFS / exFAT / HPFS
/dev/sde2         376,852,770   390,716,864    13,864,095   c W95 FAT32 (LBA)
/dev/sde3         261,556,222   376,852,479   115,296,258   5 Extended
/dev/sde5         261,556,224   372,051,967   110,495,744  83 Linux
/dev/sde6         372,054,016   376,852,479     4,798,464  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sde1        6A885BF3885BBBEF                       ntfs       
/dev/sde2        4B6E-6BC0                              vfat       HP_RECOVERY
/dev/sde5        776d1064-8cda-40c2-815f-da05002acb94   ext4       
/dev/sde6        9afbb9f3-96cc-4a89-87fe-63dfcdbecaf1   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sde2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
--------------------------------------------------------------------------------

=========================== sde5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 776d1064-8cda-40c2-815f-da05002acb94
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 776d1064-8cda-40c2-815f-da05002acb94
set locale_dir=($root)/boot/grub/locale
set lang=fi_FI
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=0
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
menuentry 'Ubuntu, Linux-ydin 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 776d1064-8cda-40c2-815f-da05002acb94
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=776d1064-8cda-40c2-815f-da05002acb94 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, Linux-ydin 2.6.38-8-generic (toipumistila)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 776d1064-8cda-40c2-815f-da05002acb94
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=776d1064-8cda-40c2-815f-da05002acb94 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, Linux-ydin 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 776d1064-8cda-40c2-815f-da05002acb94
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=776d1064-8cda-40c2-815f-da05002acb94 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, Linux-ydin 2.6.35-28-generic (toipumistila)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 776d1064-8cda-40c2-815f-da05002acb94
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=776d1064-8cda-40c2-815f-da05002acb94 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
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
    search --no-floppy --fs-uuid --set=root 776d1064-8cda-40c2-815f-da05002acb94
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 776d1064-8cda-40c2-815f-da05002acb94
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6A885BF3885BBBEF
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 4b6e-6bc0
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
--------------------------------------------------------------------------------

=============================== sde5/etc/fstab: ================================

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
UUID=776d1064-8cda-40c2-815f-da05002acb94 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9afbb9f3-96cc-4a89-87fe-63dfcdbecaf1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sde5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 128.859474182 = 138.361806848  boot/grub/core.img                             1
 165.219680786 = 177.403281408  boot/grub/grub.cfg                             1
 125.644580841 = 134.909841408  boot/initrd.img-2.6.35-28-generic              2
 128.078716278 = 137.523474432  boot/initrd.img-2.6.38-8-generic               2
 129.100013733 = 138.620084224  boot/vmlinuz-2.6.35-28-generic                 1
 127.208312988 = 136.588886016  boot/vmlinuz-2.6.38-8-generic                  1
 128.078716278 = 137.523474432  initrd.img                                     2
 125.644580841 = 134.909841408  initrd.img.old                                 2
 127.208312988 = 136.588886016  vmlinuz                                        1
 129.100013733 = 138.620084224  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sde2

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 22 51 76 16  |........?..."Qv.|
00000020  9f 8c d3 00 c9 34 00 00  00 00 00 00 02 00 00 00  |.....4..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 c0 6b 6e 4b 48  50 5f 52 45 43 4f 56 45  |..).knKHP_RECOVE|
00000050  52 59 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |RYFAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  c7 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 4e 54 4c 44 52 20 20  |.f..f.F..NTLDR  |
000001b0  20 20 20 20 0d 0a 4e 6f  20 53 79 73 74 65 6d 20  |    ..No System |
000001c0  44 69 73 6b 20 6f 72 0d  0a 44 69 73 6b 20 49 2f  |Disk or..Disk I/|
000001d0  4f 20 65 72 72 6f 72 0d  0a 50 72 65 73 73 20 61  |O error..Press a|
000001e0  20 6b 65 79 20 74 6f 20  72 65 73 74 61 72 74 0d  | key to restart.|
000001f0  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sde3

00000000  11 ff b0 16 fb 4a 7f b2  f7 be 3f 58 31 44 f7 01  |.....J....?X1D..|
00000010  ff c0 bb 73 56 11 82 45  72 59 ff c0 f9 c0 33 d0  |...sV..ErY....3.|
00000020  1e 75 51 98 35 70 00 5c  d0 13 fd c0 79 82 93 48  |.uQ.5p.\....y..H|
00000030  b9 ec 2d 7f 0e 80 00 7d  0e 04 fc d7 6a ff b2 90  |..-....}....j...|
00000040  72 7f 0e 7f 0e f1 36 7f  cf ef 31 64 b3 66 7f cf  |r.....6...1d.f..|
00000050  13 3a 54 50 15 15 67 b3  21 6f fb b2 7f 0e f1 7b  |.:TP..g.!o.....{|
00000060  77 cf 32 d0 39 f1 90 d8  61 30 1a fd 5b b9 b9 71  |w.2.9...a0..[..q|
00000070  1a b1 2e 08 6c 12 ab b1  2e e0 00 80 f0 24 73 b3  |....l........$s.|
00000080  f3 80 1a 06 00 f5 01 65  87 b1 10 ae 00 d0 7f 7f  |.......e........|
00000090  b3 7f 67 2e b0 18 45 90  29 15 31 03 15 f0 11 80  |..g...E.).1.....|
000000a0  80 00 f3 1a 95 20 0b f6  00 65 87 71 52 aa 46 6c  |..... ...e.qR.Fl|
000000b0  0b d3 b1 01 3d 24 b5 40  01 b1 3e ba c8 1a c0 18  |....=$.@..>.....|
000000c0  b1 a6 08 d8 b5 15 bf 60  b5 b1 60 4d d0 66 53 f2  |.......`..`M.fS.|
000000d0  32 71 1f 56 10 1d be 4e  30 6b 13 69 d1 16 13 01  |2q.V...N0k.i....|
000000e0  d1 89 4c 70 36 bd 31 ba  49 f0 01 93 93 11 38 c1  |..Lp6.1.I.....8.|
000000f0  84 40 f0 09 60 28 4c c0  d0 05 b0 07 f2 3e 2a 18  |.@..`(L......>*.|
00000100  ab 04 14 34 78 b5 69 1f  1b 0f 20 19 28 00 f3 79  |...4x.i... .(..y|
00000110  20 02 00 00 fc 02 13 d0  17 ff 08 bf 69 bf 69 3f  | ...........i.i?|
00000120  5b 3f 5b 6f 3f 5b bf 93  bf 93 11 69 5c 50 1d d1  |[?[o?[.....i\P..|
00000130  2e 34 35 b0 7b 38 b0 10  34 30 0f b3 93 e0 95 08  |.45.{8..40......|
00000140  b8 05 80 c0 16 1f 1b 56  19 1a 1c 70 0c d0 f1 00  |.......V...p....|
00000150  c0 0c 1f 1b 1f 14 19 24  f0 00 c0 f1 00 10 00 00  |.......$........|
00000160  55 f1 00 26 f0 00 b0 f1  00 18 f7 00 7d 0f 31 1c  |U..&........}.1.|
00000170  c0 40 f5 01 31 1c bc 35  f2 d1 1b f1 10 3d 1c 88  |.@..1..5.....=..|
00000180  d0 23 31 1c 13 1b 12 07  ff c2 70 65 55 86 ca b6  |.#1.......peU...|
00000190  00 20 00 46 00 49 00 4c  00 a0 45 00 53 00 5c 00  |. .F.I.L..E.S.\.|
000001a0  b0 2d 00 38 80 45 00 43  00 55 00 52 00 98 22 20  |.-.8.E.C.U.R.." |
000001b0  00 d8 4e 00 54 00 24 52  00 a2 4e 00 14 54 00 fe  |..N.T.$R..N..T..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 96 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 08  96 06 00 40 49 00 00 00  |...........@I...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sda sdb sdc sdd 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Narhinik on 2011-05-30
Sorry for bumping this but I actually need to use my windows next weekend so I'd be really thankful if this could be solved before Friday.

If not, I might have to look for another computer or re-install windows

---

### Post by Hedgehog1 on 2011-05-30
This is based on the combination of 'lost dual boot' and new video behavior in GRUB2 to take advantage of higher resolution (which breaks some folks).

Please power up you PC and let it boot into Ubuntu (you may already have done that!)

The issue these commands in the terminal:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


Now reboot and see if the GRUB menu is visible again and that you can boot into Ubuntu and Windows again.


***The Hedge***

:KS

---

### Post by Narhinik on 2011-05-30
That didn't help but I now do know what is wrong with my computer.


I changed GRUB_TIMEOUT to 10 (had it at 0) and I now can choose Vista from the menu.

Timeout was 0 because previously my computer booted to windows boot manager (don't know what its really called) where I got to choose Windows/Ubuntu.

(This screen is black with white text)


If I chose ubuntu from that menu it gave me the ubuntu (grub?) boot menu where I could choose ubuntu or to go back to windows boot menu.

[When I had timeout at 0 it didn't gave me the ubuntu boot menu so it went from Windows boot menu straight to Ubuntu log in screen]

(Ubuntu boot menu is purple with white text)


When I updated to 11.04 it changed these boot menus so Ubuntu is now first/primary menu so timeout=0 booted straight to ubuntu and now those two menus are just other way around.

Is there any way to get these menus back to the original order? It was much better that way.

To get an idea what I did to my bootloader after installing ubuntu next to windows: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)



Sorry if my English is hard to understand but I'm not so good to explain things even with my first language

---

