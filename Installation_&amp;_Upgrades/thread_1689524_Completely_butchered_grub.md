---
title: "Completely butchered grub"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by khronoslynx on 2011-02-16
I recently had a problem in my netbook: absolutely nothing would load (mbr got borked); I was forced to open it up and remove my hdd, plug it into my other computer and install ubuntu on it from there. However, when I finally got my netbook up and running (put the hard drive back inside etc) I reinstalled grub and ran update-grub to get the correct entry for my system (at least, I thought it would do this).

I know have a grub that boots into command-line mode every time, and I cannot get it to boot back into my system (even using the Grub2 Basics thread).

Using:
set root=(hd0,msdos1) #(the location of my /boot partition)
linux /vmlinuz<my version> root=/dev/sda1 
initrd /initrd.img<my version>
boot

I got pushed into what looked like a initramfs terminal, and couldn't do anything from there.
By replacing "/dev/sda1' in the 'linux /vmlinuz...' command with "/dev/sda3" (the location of my / partition), the system booted into the ubuntu splash screen but seemed to hang with the output of /dev/sda3 clean (bunch of other stuff afterwards, looked like block counts) and /dev/sda4 clean (on the next line).

I have no clue what to do to get this working, short of pulling my netbook apart to get at the harddrive again :/. Anyone have any advice?

My partition scheme is:
sda1: /boot
sda2: swap
sda3: /
sda4: /home

Thanks!

---

### Post by presence1960 on 2011-02-16
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by amsterdamharu on 2011-02-16
You were on the right track here

set root=(hd0,msdos1) #(the location of my /boot partition)
linux /vmlinuz<my version> root=[COLOR=Red]/dev/sda3 ro single[/COLOR] 
initrd /initrd.img<my version>
boot

That should take you in recovery, it might be some hardware issue when you get into recovery choose dpkg reconfigure but make sure you have cable Internet when you do that.

If you don't have cable Internet then you could try
linux /vmlinuz<my version> root=[COLOR=Red]/dev/sda3 nosplash
[/COLOR]You installed Ubuntu on another computer using this harddisk, maybe the other computer detected heads and cylinders differently that the one it is in now making the data on the disk corrupt. It might just want to do an fscheck so let it finish what it's doing. To see what it does you can press control + alt + F1,F2,F3... to go through different tty's

---

### Post by khronoslynx on 2011-02-17
Using @Amsterdamharu's advice I got my ubuntu install (the one on the disk) booted into a recovery terminal, and from there ran the boot script you linked me presence1960.

Here's the output (Note: /dev/sdb is the flash drive I used to transfer over the boot script):

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       391,167       389,120  ef EFI (FAT-12/16/32)
/dev/sda2    *        391,168     8,204,287     7,813,120  82 Linux swap / Solaris
/dev/sda3           8,204,288    37,500,927    29,296,640  83 Linux
/dev/sda4          37,500,928   488,394,751   450,893,824  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 501 MB, 501219328 bytes
255 heads, 63 sectors/track, 60 cylinders, total 978944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       978,893       978,831   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        26751954-5846-4acc-8a6f-2b8829ffb4be   ext2                                     
/dev/sda2        fee8e736-aabf-4473-b958-cb0fbac017cc   swap                                     
/dev/sda3        c259392f-e611-4cb8-8907-f6b4b1b5ae8d   ext4                                     
/dev/sda4        454a7e96-e7fc-42be-b093-b986c770a57a   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7F76-1BF9                              vfat       FIXER                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda4        /home                    ext4       (rw)
/dev/sdb1        /mnt                     vfat       (rw)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set c259392f-e611-4cb8-8907-f6b4b1b5ae8d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 26751954-5846-4acc-8a6f-2b8829ffb4be
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 26751954-5846-4acc-8a6f-2b8829ffb4be
	linux	/vmlinuz-2.6.35-19-generic root=UUID=c259392f-e611-4cb8-8907-f6b4b1b5ae8d ro   quiet splash
	initrd	/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 26751954-5846-4acc-8a6f-2b8829ffb4be
	echo	'Loading Linux 2.6.35-19-generic ...'
	linux	/vmlinuz-2.6.35-19-generic root=UUID=c259392f-e611-4cb8-8907-f6b4b1b5ae8d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 26751954-5846-4acc-8a6f-2b8829ffb4be
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 26751954-5846-4acc-8a6f-2b8829ffb4be
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+, experimental multiboot)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 26751954-5846-4acc-8a6f-2b8829ffb4be
	multiboot	/memtest86+_multiboot.bin
}
menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 26751954-5846-4acc-8a6f-2b8829ffb4be
	multiboot	/memtest86+_multiboot.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
	insmod part_gpt
	insmod hfsplus
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 0ef54b7584bfc229
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 0ef54b7584bfc229 uuid
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
menuentry "Mac OS X (64-bit) (on /dev/sda2)" {
	insmod part_gpt
	insmod hfsplus
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 0ef54b7584bfc229
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 0ef54b7584bfc229 uuid
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
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda5)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set dba74a50-950c-415c-8e58-d4217b04ece1
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=dba74a50-950c-415c-8e58-d4217b04ece1 ro quiet splash nomodeset video=uvesafb:mode_option=1280x800-32,mtrr=3,scroll=ywrap
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda5)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set dba74a50-950c-415c-8e58-d4217b04ece1
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=dba74a50-950c-415c-8e58-d4217b04ece1 ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set dba74a50-950c-415c-8e58-d4217b04ece1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=dba74a50-950c-415c-8e58-d4217b04ece1 ro quiet splash nomodeset video=uvesafb:mode_option=1280x800-32,mtrr=3,scroll=ywrap
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set dba74a50-950c-415c-8e58-d4217b04ece1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=dba74a50-950c-415c-8e58-d4217b04ece1 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-19-generic
    .0GB: vmlinuz-2.6.35-19-generic

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set c259392f-e611-4cb8-8907-f6b4b1b5ae8d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set c259392f-e611-4cb8-8907-f6b4b1b5ae8d
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

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=c259392f-e611-4cb8-8907-f6b4b1b5ae8d /               ext4    errors=remount-ro 0       1
/dev/sdb1       /boot           ext2    defaults        0       2
# /home was on /dev/sdb4 during installation
UUID=454a7e96-e7fc-42be-b093-b986c770a57a /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=7260ec4d-b54d-4b3f-aa7d-44c944523b0d none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=fee8e736-aabf-4473-b958-cb0fbac017cc none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  15.0GB: boot/grub/core.img
   6.7GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 3c 90 42 53 44 20 20  34 2e 34 00 02 10 01 00  |.<.BSD  4.4.....|
00000010  02 00 02 00 00 f0 ef 00  20 00 36 00 00 00 00 00  |........ .6.....|
00000020  8f ef 0e 00 00 00 29 f9  1b 76 7f 46 49 58 45 52  |......)..v.FIXER|
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 fa 31  |      FAT16   .1|
00000040  c0 8e d0 bc 00 7c fb 8e  d8 e8 00 00 5e 83 c6 19  |.....|......^...|
00000050  bb 07 00 fc ac 84 c0 74  06 b4 0e cd 10 eb f5 30  |.......t.......0|
00000060  e4 cd 16 cd 19 0d 0a 4e  6f 6e 2d 73 79 73 74 65  |.......Non-syste|
00000070  6d 20 64 69 73 6b 0d 0a  50 72 65 73 73 20 61 6e  |m disk..Press an|
00000080  79 20 6b 65 79 20 74 6f  20 72 65 62 6f 6f 74 0d  |y key to reboot.|
00000090  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Thanks for the help so far!

---

### Post by amsterdamharu on 2011-02-18
Did you choose  choose dpkg reconfigure in recovery mode?

What output do you get when you boot "normally" with the following options:
linux /vmlinuz<my version> root=[COLOR=Red]/dev/sda3 nosplash

[/COLOR]You might comment out the line
```
/dev/sdb1       /boot           ext2    defaults        0       2
```in your /etc/fstab
In recovery mode execute the following command:
```
sudo nano /etc/fstab
```Change
```
/dev/sdb1       /boot           ext2    defaults        0       2
```to
```
[COLOR=Red]#[/COLOR]/dev/sdb1       /boot           ext2    defaults        0       2
```Press control + x, then y and enter
Now try to create grub.cfg with the following command:
```
sudo update-grub
```Now you should be able to boot into your Ubuntu normally, if not then please boot up normally, when you see the grub menu press e to edit the menu entry and remove quiet splash. Some output should be given and as stated before control + alt + F1,F2 ... might give you some output too that will explain what is going on.

---

### Post by khronoslynx on 2011-02-19
Alright, so running the whole shebang (including linux /vmlinuz<version> =/dev/sda3 nosplash) got me booted back into a terminal.

What I did next was edit /etc/fstab to point to the correct partitions (previously it pointed to their UUIDs which didn't seem to work). Then I ran ```
sudo update-grub
```

Rebooting and running through the process again I got Ubuntu booted and running **except** grub still booted into the command line. Do either of you know how to fix this?

---

### Post by amsterdamharu on 2011-02-19
I think the UUID worked fine actually:

```
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        26751954-5846-4acc-8a6f-2b8829ffb4be   ext2                                     
/dev/sda2        fee8e736-aabf-4473-b958-cb0fbac017cc   swap                                     
/dev/sda3        c259392f-e611-4cb8-8907-f6b4b1b5ae8d   ext4                                     
/dev/sda4        454a7e96-e7fc-42be-b093-b986c770a57a   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7F76-1BF9                              vfat       FIXER                         
/dev/sdb: PTTYPE="dos" 

```Your fstab
```

proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation [COLOR=Red]is sda3 according to blkid[/COLOR]
UUID=c259392f-e611-4cb8-8907-f6b4b1b5ae8d /               ext4    errors=remount-ro 0       1
# [COLOR=Red]the next line makes no sense since sdb1 is not ext2 and probably doesn't contain grub boot files[/COLOR] so I commented it out
#/dev/sdb1       /boot           ext2    defaults        0       2
# /home was on /dev/sdb4 during installation [COLOR=Red]is sda4 according to blkid[/COLOR]
UUID=454a7e96-e7fc-42be-b093-b986c770a57a /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation the [COLOR=Red]next line makes no sense either, there is no such partition with that id[/COLOR] commented it out
# UUID=7260ec4d-b54d-4b3f-aa7d-44c944523b0d none            swap    sw              0       0
# swap was on /dev/sdb2 during installation [COLOR=Red]next line is ok, swap is on sda2[/COLOR]
UUID=fee8e736-aabf-4473-b958-cb0fbac017cc none            swap    sw              0       0

```I suggest you use the fstab as I posted it here and then try again.

You can edit it when you boot of a live cd and then mount your Ubuntu partition with the following commands:
```
sudo mount /dev/sda3 /mnt
gksu geany /mnt/etc/fstab&
```

---

### Post by amsterdamharu on 2011-02-19
You might have missed this the first 2 times I posted it so I put it in red this time:
 [COLOR=Red]Some output should be given and as stated before control + alt + F1,F2  ... might give you some output too that will explain what is going on.[/COLOR]
If no more info is given all we can do is guesswork.

The one thing I can be sure of now is that your fstab isn't correct.

---

### Post by khronoslynx on 2011-02-20
Sorry about missing your ctl-alt-F# points; I got distracted and forgot to check it. After logging into my system and checking both terminals I had no output. They asked me for login name and password, then afterwards didn't give me any extra information.

I have a question about the fstab you posted amsterdamharu; Shouldn't it have the UUID and the other options listed for the /boot partition? I noticed yours doesn't have them listed.

I'm thinking of just booting it off the install usb again (if I can get it to do so from the grub CL) and reinstalling to fix this... What would you recommend?

---

### Post by khronoslynx on 2011-02-20
Alright, so I can't even get the grub command prompt to see my Flash Drive (its formatted as FAT). I've used set prefix=(hd0,msdos1)/grub

and loaded both the linux and fat modules, yet can't get it to list when using ls
EDIT: rebooted and it shows up, but booting brings me into busybox prompt

---

### Post by YesWeCan on 2011-02-20
> **khronoslynx said:**
> However, when I finally got my netbook up and running (put the hard drive back inside etc) I reinstalled grub and ran update-grub to get the correct entry for my system (at least, I thought it would do this).
How did you reinstall grub...running off usb?
Did you use something like 'grub-install --root-directory=/dev/sda3 /dev/sda'
Is this the same live usb that you used to install ubuntu in the first place?

---

### Post by amsterdamharu on 2011-02-20
The fstab I posted is what it should be, select the whole thing in the code box and copy paste it.
Grub doesn't use the fstab but when Ubuntu boots it needs it to setup root partition, home and swap.

Your install is working fine but it looks like gnome is not starting, you get a command prompt login screen, try the following command:
```
startx
```That will probably tell you some driver isn't loaded/found. To see what video card you have you can execute the command:
```
sudo lspci
```I don't know if you tried dpkg reconfigure in restore mode before because that could fix your problem. You need a cable Internet connection for that.

---

### Post by YesWeCan on 2011-02-20
> **khronoslynx said:**
> Alright, so running the whole shebang (including linux /vmlinuz<version> =/dev/sda3 nosplash) got me booted back into a terminal.

What I did next was edit /etc/fstab to point to the correct partitions (previously it pointed to their UUIDs which didn't seem to work). Then I ran ```
sudo update-grub
```

Rebooting and running through the process again I got Ubuntu booted and running **except** grub still booted into the command line. Do either of you know how to fix this?
Which command line are you talking about? Grub has one. BusyBox has one. Ubuntu has one (when it fails to start x windows).

If you got it to boot into Ubuntu on sda then you are in business.
Edit /etc/default/grub and add 'nomodeset' to the commands, after 'nosplash'. This will probably fix the windows problem.
run sudo update-grub
run sudo grub-install /dev/sda
reboot

---

### Post by khronoslynx on 2011-02-21
This would be the Grub commandline, sorry for the ambiguity. And grub was reinstalled from the command line of my ubuntu install (probably incorrectly). Gnome runs fine, that's not the issue.

and I used 'grub-install  /dev/sda' I do believe

---

### Post by amsterdamharu on 2011-02-22
Edited this post because after careful reading my reply didn't make sense.

I have to agree on trying to purge and re install grub as the next post suggests.

Sorry for misunderstanding your previous reply, I thought the grub menu showed up after you did an update-grup.

---

### Post by ultrageeky on 2011-02-22
You can reinstall grub using a LiveCD. Had to do  this a few days ago to get an old installation working. Detailed instructions are at [HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread?t=1581099")

---

### Post by YesWeCan on 2011-02-22
> **khronoslynx said:**
> This would be the Grub commandline, sorry for the ambiguity. And grub was reinstalled from the command line of my ubuntu install (probably incorrectly). Gnome runs fine, that's not the issue.

and I used 'grub-install  /dev/sda' I do believe

Intuitively, you would think that Grub is an application that you install in one place on a disk and when it runs it inspects your disks and generates a boot menu. Simple.

No.

For reasons which elude me it is located in a very small part of your disk...too small to accommodate it completely. So it needs to access image files in /boot/grub. The "--root-directory=" option of grub-install tells it where to look for the grub directory and where to put image files.

---

### Post by khronoslynx on 2011-02-22
@YesWeCan: my /boot directory is located on /dev/sda1. However, running 'sudo grub-install --root-directory=/dev/sda1 /dev/sda' returns 'mkdir: cannot create directory '/dev/sda1': Not a directory'

---

### Post by YesWeCan on 2011-02-22
Do you have the disk mounted?

Scratch that. Not relevant.

Scratch that too! /dev/sda1 must be mounted. Best to follow the instructions in the "Reinstalling Grub2" section here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by khronoslynx on 2011-02-22
I can't get my netbook to see when I have the live USB inserted though (at the Grub command line). When I type 'ls' all it lists is the built in HDD (hd0)

---

### Post by amsterdamharu on 2011-02-22
If you have a separate boot directory in sda1 I think you should put that in the fstab as well. Currently separate boot is not indicated in fstab so sda3 is assumed.

---

### Post by khronoslynx on 2011-02-22
Boot directory is listed in the fstab already; I added it

---

### Post by YesWeCan on 2011-02-23
> **khronoslynx said:**
> I can't get my netbook to see when I have the live USB inserted though (at the Grub command line). When I type 'ls' all it lists is the built in HDD (hd0)

I do not understand...grub command line? You need to boot off the usb then follow those instructions. I don't think the grub command line is involved.

---

### Post by khronoslynx on 2011-02-23
Telling my netbook to boot from USB, for some reason, kicks me back to the Grub Command line. That's what I meant; sorry for the confusion

---

### Post by amsterdamharu on 2011-02-23
Could you boot up with the commands in grub command and execute the following command?

```
mount
```
It should show you that /dev/sda1 is mounted as /boot, if not then you didn't correctly edit the fstab and you need to post it here again.

Then uninstall and re install grub as suggested before but without the chroot:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

```
sudo apt-get purge grub2 grub-pc
sudo apt-get install grub-pc
sudo update-grub
```

---

### Post by khronoslynx on 2011-02-23
The next problem comes from being unable to access the internet: the ethernet connection always fails, and I need to compile the wireless driver from scratch but don't have the required dependencies to do so, and can't get them because it's stranded from the internet

---

### Post by amsterdamharu on 2011-02-24
Maybe you can post what network card you are using. Wireless/wired usb or pci?

If it's usb please post the output of the following command:
```
sudo lsusb
```if it's pci please post the output of the following command:
```
sudo lspci -vv
```You need to post only the part of your network card.
Can you post the output of the following command as well (if it's wireless)?
```
rfkill list
ifconfig -a
sudo jockey-text
```If rfkill says it's not installed you can install it with the following command:
```
sudo apt-get install rfkill
```At least grub is working as it should now I assume. Your other computer is mac was it? If it can start from usb you can run a live session on the mac and then install packages and all it's dependencies, after doing so you'll find the packages in /var/cache/apt/archives/ you can copy them to your mac harddrive and then to the usb stick and finally to the /var/cache/apt/archives/ on your Ubuntu install. When you apt-get install the same package from Ubuntu the files in archives should be used. Maybe better not to use apt-get update on both machines so you'll get the same versions of the packages. When your network is up you can update then.

But you need to know what you need first.

---

### Post by khronoslynx on 2011-02-24
Problem seemed to be my LiveUSB; I made a new one and have a working install.

Thanks for the help!

---

