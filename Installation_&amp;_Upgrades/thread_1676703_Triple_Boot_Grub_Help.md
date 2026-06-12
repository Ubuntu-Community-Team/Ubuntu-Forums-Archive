---
title: "Triple Boot Grub Help"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by snuggles166 on 2011-01-27
Hey guys, I'm tying to set up triple boot on my new netboot with Windows 7, Ubuntu 10.10, and Backtrack 4 R2.  I have everything installed but I can't seem to get backtrack to work with grub.

Here is my dump from bootinfo

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 R2 Codename Nemesis
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sda2         209,717,248   241,174,527    31,457,280  1b Hidden W95 FAT32
/dev/sda3         241,176,574   488,294,399   247,117,826   5 Extended
/dev/sda5         479,907,840   488,294,399     8,386,560  82 Linux swap / Solaris
/dev/sda6         419,907,033   479,893,679    59,986,647  83 Linux
/dev/sda7         241,176,576   419,905,535   178,728,960  83 Linux
/dev/sda4         488,294,400   488,396,799       102,400  ef EFI (FAT-12/16/32)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A6CE4C16CE4BDCE5                       ntfs                                     
/dev/sda2        86F4-D40A                              vfat                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        3a879f06-03df-479b-90ff-822b3ae08104   swap                                     
/dev/sda6        7bbbebfd-2f08-458d-a1f3-71d32640ceac   ext3                                     
/dev/sda7        0ae48c51-2c1f-4a02-82c6-257e5678e1a8   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/menu.lst: ===========================

# By default, boot the first entry.
default 0

# Boot automatically after 30 secs.
timeout 30

vga=0x317image=/boot/grub/bt4.xpm.gz


title                Start BackTrack FrameBuffer (1024x768)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
initrd                /boot/initrd.gz

title                Start BackTrack FrameBuffer (800x600)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x314
initrd                /boot/initrd800.gz

title                Start BackTrack Forensics (no swap)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
initrd                /boot/initrdfr.gz

title                Start BackTrack in Safe Graphical Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper xforcevesa rw quiet 
initrd                /boot/initrd.gz

title                Start Persistent Live CD
kernel                /boot/vmlinuz BOOT=casper boot=casper persistent rw quiet 
initrd                /boot/initrd.gz

title                Start BackTrack in Text Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd                /boot/initrd.gz

title                Start BackTrack Graphical Mode from RAM
kernel                /boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw quiet 
initrd                /boot/initrd.gz

title                Memory Test
kernel                /boot/memtest86+.bin

title                Boot the First Hard Disk
root                (hd0)
chainloader +1
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a76c7835-eb6f-459f-a891-496f16bc00eb

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

vga=0x317image=a76c7835-eb6f-459f-a891-496f16bc00eb/boot/grub/vga=0x317.xpm.gz

title        Ubuntu 8.10, kernel 2.6.34
uuid        a76c7835-eb6f-459f-a891-496f16bc00eb
kernel        /boot/vmlinuz-2.6.34 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro vga=0x317 
initrd        /boot/initrd.img-2.6.34
quiet

title        Ubuntu 8.10, kernel 2.6.34 (recovery mode)
uuid        a76c7835-eb6f-459f-a891-496f16bc00eb
kernel        /boot/vmlinuz-2.6.34 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro  single
initrd        /boot/initrd.img-2.6.34

title        Ubuntu 8.10, memtest86+
uuid        a76c7835-eb6f-459f-a891-496f16bc00eb
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=7bbbebfd-2f08-458d-a1f3-71d32640ceac /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3a879f06-03df-479b-90ff-822b3ae08104 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 244.6GB: boot/grub/menu.lst
 244.7GB: boot/grub/stage2
 244.6GB: boot/initrd.img-2.6.35.8
 244.7GB: boot/vmlinuz-2.6.35.8
 244.6GB: initrd.img
 244.7GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 0ae48c51-2c1f-4a02-82c6-257e5678e1a8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 0ae48c51-2c1f-4a02-82c6-257e5678e1a8
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 0ae48c51-2c1f-4a02-82c6-257e5678e1a8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0ae48c51-2c1f-4a02-82c6-257e5678e1a8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 0ae48c51-2c1f-4a02-82c6-257e5678e1a8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0ae48c51-2c1f-4a02-82c6-257e5678e1a8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 0ae48c51-2c1f-4a02-82c6-257e5678e1a8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 0ae48c51-2c1f-4a02-82c6-257e5678e1a8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a6ce4c16ce4bdce5
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 86f4-d40a
    chainloader +1
}
menuentry "Memory Test (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 7bbbebfd-2f08-458d-a1f3-71d32640ceac
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 7bbbebfd-2f08-458d-a1f3-71d32640ceac
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
#menuentry "Start BackTrack FrameBuffer (1024x768)" {
#    set gfxpayload=keep
#    linux    /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet #vga=0x317
#    initrd    /boot/initrd.gz
#    }
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=0ae48c51-2c1f-4a02-82c6-257e5678e1a8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3a879f06-03df-479b-90ff-822b3ae08104 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 194.4GB: boot/grub/core.img
 173.0GB: boot/grub/grub.cfg
 167.1GB: boot/initrd.img-2.6.35-22-generic
 123.8GB: boot/vmlinuz-2.6.35-22-generic
 167.1GB: initrd.img
 123.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 c0  3a 0e 00 f8 7f 00 00 fe  |........:.......|
000001d0  ff ff 05 fe ff ff 9c 35  a7 0a 16 53 93 03 00 00  |.......5...S....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```sda1 is my windows 7
sda2 is my asus recovery partition
sda3 is my logical with 5 6 7
sda4 is EFI for asus express gate
sda5 is swap
sda6 is bt4
sda7 is ubuntu
 
Thanks for any help you guys can give.  Not a total novice but I have idea where to go from here.

---

### Post by oldfred on 2011-01-27
I tried to help another user. But have not heard if it worked. You can copy my suggestion for him but change the set root to your partition sda6 or (hd0,6).

[http://ubuntuforums.org/showthread.php?t=1675875](http://ubuntuforums.org/showthread.php?t=1675875)

---

### Post by snuggles166 on 2011-01-27
Hi oldfred and thanks for responding.

I tried what you said on your other post and switched the 

```

set root='(hd0,msdos8)'

```

to both 

```
set root='(hd0,msdos6)'
```

and

```
set root='(hd0,6)'
```

and wrote it to the 40_custom.  Its adds it to the grub menu on boot but when selected both came up with the error of

```
error: file not found.
error: you need to load the kernel first.
Press any key to continue...
```

Any suggestions?

---

### Post by snuggles166 on 2011-01-28
Seems just about everybody throughout the internet is having a problem with this, all I've dug up are tons of unsolved posts =(

---

### Post by oldfred on 2011-01-28
That error is whenever it cannot find the kernel. The set root has to be from grub2, and normally the linux line has to be from the system being booted and probably with old grub nomenclature/partition definition. But Backtrack seems to be more like an ISO boot as it does not have a normal root= entry.

I have experimented with editing various lines on the grub menu with e to get puppy to work but have not tried backtrack. 

Is path correct, are partitions numbers correct. 

Another alternative is to install backtracks grub legacy to the backtrack partition. then you can chainload from grub2 to grub in the partition.

menuentry "Chainload Other Systems Grub Menu on sda6" {
set root=(hd0,6)
chainloader +1
}

---

### Post by snuggles166 on 2011-01-28
Thanks much for you help oldfred.

I reinstalled backtrack and this time installed its bootloader to its own partition, then I updated grub from ubuntu and all is well!

---

