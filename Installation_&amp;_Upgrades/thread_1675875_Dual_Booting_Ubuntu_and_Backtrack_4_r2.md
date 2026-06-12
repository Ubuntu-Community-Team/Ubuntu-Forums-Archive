---
title: "Dual Booting Ubuntu and Backtrack 4 r2"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by Balmer25 on 2011-01-26
Installed XP and ubuntu 10.10 on my netbook and have also installed BT4 r2 on separate partitions. I chose not to install the bootloader for BT4 r2 and used "sudo update-grub2" to locate Backtrack 4 which it has. 
At boot I can choose both XP and Ubuntu and they will boot fine, how ever when I choose BT4 (listed as ubuntu 8.10) the following message appears:
"zImage does not support 32bit boot"
Can someone please help me so that I can boot backtrack please
Thanks
(Sorry if this is in the wrong category, also I am a complete Noob when it comes to Linux so please give detailed clear instructions thanks :) )

---

### Post by oldfred on 2011-01-26
So we can see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Balmer25 on 2011-01-27
Okay, I ran the script this is the content of the results.txt:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 R2 Codename Nemesis
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sda4          61,433,854   312,580,095   251,146,242   5 Extended
/dev/sda5         307,515,392   312,580,095     5,064,704  82 Linux swap / Solaris
/dev/sda6          61,433,856   122,863,615    61,429,760  83 Linux
/dev/sda7         181,456,896   307,513,343   126,056,448   7 HPFS/NTFS
/dev/sda8         122,865,183   181,454,174    58,588,992  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        FE60CA7960CA3863                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        4db62c2b-f02c-4644-85e2-9d0cc07084b4   swap                                     
/dev/sda6        06ef9677-4e7d-47f7-a0f2-4d6cac890068   ext4                                     
/dev/sda7        6E6895CF0AA00E5F                       ntfs                                     
/dev/sda8        9f697e1b-db9f-4ade-9c6d-512877e9b5f0   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=600)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Noob Edition" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 06ef9677-4e7d-47f7-a0f2-4d6cac890068
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 06ef9677-4e7d-47f7-a0f2-4d6cac890068
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 06ef9677-4e7d-47f7-a0f2-4d6cac890068
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=06ef9677-4e7d-47f7-a0f2-4d6cac890068 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 06ef9677-4e7d-47f7-a0f2-4d6cac890068
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=06ef9677-4e7d-47f7-a0f2-4d6cac890068 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 06ef9677-4e7d-47f7-a0f2-4d6cac890068
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=06ef9677-4e7d-47f7-a0f2-4d6cac890068 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 06ef9677-4e7d-47f7-a0f2-4d6cac890068
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=06ef9677-4e7d-47f7-a0f2-4d6cac890068 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 06ef9677-4e7d-47f7-a0f2-4d6cac890068
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 06ef9677-4e7d-47f7-a0f2-4d6cac890068
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Noob Edition (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set fe60ca7960ca3863
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Memory Test (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 9f697e1b-db9f-4ade-9c6d-512877e9b5f0
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 9f697e1b-db9f-4ade-9c6d-512877e9b5f0
	linux /boot/memtest86+.bin 
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=06ef9677-4e7d-47f7-a0f2-4d6cac890068 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4db62c2b-f02c-4644-85e2-9d0cc07084b4 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  42.4GB: boot/grub/core.img
  33.9GB: boot/grub/grub.cfg
  32.7GB: boot/initrd.img-2.6.35-22-generic
  32.7GB: boot/initrd.img-2.6.35-24-generic
  42.4GB: boot/vmlinuz-2.6.35-22-generic
  42.3GB: boot/vmlinuz-2.6.35-24-generic
  32.7GB: initrd.img
  32.7GB: initrd.img.old
  42.3GB: vmlinuz
  42.4GB: vmlinuz.old

=========================== sda8/boot/grub/menu.lst: ===========================

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

title		Ubuntu 8.10, kernel 2.6.34
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/vmlinuz-2.6.34 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro vga=0x317 
initrd		/boot/initrd.img-2.6.34
quiet

title		Ubuntu 8.10, kernel 2.6.34 (recovery mode)
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/vmlinuz-2.6.34 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro  single
initrd		/boot/initrd.img-2.6.34

title		Ubuntu 8.10, memtest86+
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=9f697e1b-db9f-4ade-9c6d-512877e9b5f0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4db62c2b-f02c-4644-85e2-9d0cc07084b4 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


  79.1GB: boot/grub/menu.lst
  79.1GB: boot/grub/stage2
  79.1GB: boot/initrd.img-2.6.35.8
  79.1GB: boot/vmlinuz-2.6.35.8
  79.1GB: initrd.img
  79.1GB: vmlinuz

```
Thanks for any help

---

### Post by oldfred on 2011-01-27
In the backtrack menu.lst you have Backtrack and Ubuntu 8.10. I have tried to convert one of the Backtrack entries to grub2 style for you to copy into 40_custom.

Copy to:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub



```
menuentry "Start BackTrack FrameBuffer (1024x768)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    set gfxpayload=keep
    linux    /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
    initrd    /boot/initrd.gz
    }

```If this works then you can copy it and edit to match the other Backtrack entries. Not sure if the vga entry will be a problem. Grub2 does not use it anymore, but it looks like Backtrack expects it.

---

### Post by 5arco on 2011-03-24
I have exactly the same situation (apart from Win 7 instead of XP) and the same error message when attempting to boot into BT4.

I've run the script suggested and this is the output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 R2 Codename Nemesis
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,663   303,628,499   303,218,837   f W95 Ext d (LBA)
/dev/sda5             409,664   210,130,199   209,720,536   7 HPFS/NTFS
/dev/sda6         210,130,263   303,628,499    93,498,237  83 Linux
/dev/sda3         303,634,432   309,925,887     6,291,456  82 Linux swap / Solaris
/dev/sda4         309,925,888   625,137,663   315,211,776  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        80E4EDCFE4EDC80C                       ntfs       SYSTEM                        
/dev/sda2: PTTYPE="dos" 
/dev/sda3        56184cec-d6df-4896-9a30-4f264602b5f8   swap                                     
/dev/sda4        d155bd06-eb62-4eca-a119-b7203b6ab353   ext4                                     
/dev/sda5        01CBE9AF12075490                       ntfs                                     
/dev/sda6        a7ea5c2d-ee19-46ba-b339-0c15a5b15339   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=600)


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

title		Ubuntu 8.10, kernel 2.6.34
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/vmlinuz-2.6.34 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro vga=0x317 
initrd		/boot/initrd.img-2.6.34
quiet

title		Ubuntu 8.10, kernel 2.6.34 (recovery mode)
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/vmlinuz-2.6.34 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro  single
initrd		/boot/initrd.img-2.6.34

title		Ubuntu 8.10, memtest86+
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a7ea5c2d-ee19-46ba-b339-0c15a5b15339 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=56184cec-d6df-4896-9a30-4f264602b5f8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 131.8GB: boot/grub/menu.lst
 131.8GB: boot/grub/stage2
 131.7GB: boot/initrd.img-2.6.35.8
 131.8GB: boot/vmlinuz-2.6.35.8
 131.7GB: initrd.img
 131.8GB: vmlinuz

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set d155bd06-eb62-4eca-a119-b7203b6ab353
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set d155bd06-eb62-4eca-a119-b7203b6ab353
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
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set d155bd06-eb62-4eca-a119-b7203b6ab353
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=d155bd06-eb62-4eca-a119-b7203b6ab353 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set d155bd06-eb62-4eca-a119-b7203b6ab353
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=d155bd06-eb62-4eca-a119-b7203b6ab353 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set d155bd06-eb62-4eca-a119-b7203b6ab353
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d155bd06-eb62-4eca-a119-b7203b6ab353 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set d155bd06-eb62-4eca-a119-b7203b6ab353
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d155bd06-eb62-4eca-a119-b7203b6ab353 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set d155bd06-eb62-4eca-a119-b7203b6ab353
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set d155bd06-eb62-4eca-a119-b7203b6ab353
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 80e4edcfe4edc80c
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda5)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 01cbe9af12075490
	chainloader +1
}
menuentry "Memory Test (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a7ea5c2d-ee19-46ba-b339-0c15a5b15339
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a7ea5c2d-ee19-46ba-b339-0c15a5b15339
	linux /boot/memtest86+.bin 
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda4       /               ext4    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 184.6GB: boot/grub/core.img
 296.6GB: boot/grub/grub.cfg
 159.9GB: boot/initrd.img-2.6.35-22-generic
 159.9GB: boot/initrd.img-2.6.35-28-generic
 184.7GB: boot/vmlinuz-2.6.35-22-generic
 184.7GB: boot/vmlinuz-2.6.35-28-generic
 159.9GB: initrd.img
 159.9GB: initrd.img.old
 184.7GB: vmlinuz
 184.7GB: vmlinuz.old
```

I would appreciate any assistance in this matter.

EDIT: I've tried your suggestion above but changing the msdos8 to msdos6 to match my own however it still fails to boot and returns the same error message:  zImage does not support 32 bit..try `linux16'

EDIT2: I ran sudo update-grub to push the modified 40 custom file to grub.cfg and I now see a different option within grub. I get a different error message though:
```
error: file not found.
error: you need to load the kernal first.

press any key to continue.
```

---

### Post by oldfred on 2011-03-25
Your old grub menu.lst has two entries neither of which looks correct. One is missing root and the other uses UUID but has the wrong UUID??

So which did you copy. Please post your 40_custom.

Your files are and  you have to match or use :

 131.7GB: boot/initrd.img-2.6.35.8
 131.8GB: boot/vmlinuz-2.6.35.8

 131.7GB: initrd.img
 131.8GB: vmlinuz

Note that these are not in /boot so the entry is like this for these two lines

linux   /vmlinuz Boot.....
initrd    /initrd.img

---

### Post by 5arco on 2011-03-26
Indeed you are correct. Since my posting I looked over the grub.cfg file thoroughly and made multiple entries in the 40_custom. The UUID's were incorrect as you said and on closer inspection I found the correct ones to replicate the appropriate entry to successfully boot.

My 40_custom entry now looks like this:

```

menuentry "BackTrack 4 R2 (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a7ea5c2d-ee19-46ba-b339-0c15a5b15339
	linux 	/boot/vmlinuz-2.6.35.8 root=UUID=a7ea5c2d-ee19-46ba-b339-0c15a5b15339 ro quiet vga=0x317
	initrd	/boot/initrd.img-2.6.35.8
}

```

Still tweaking the options somewhat (the laptop has an obscure native resolution, everything is a bit stretched) in conjunction with the vesa file within Backtrack, but it boots and works fine.

Thanks for the help though, I wouldn't have known what to look for if not for this thread.

---

### Post by oldfred on 2011-03-26
I saved these old links to translate VGA modes:

VGA conversions:
[http://wiki.archlinux.org/index.php/Gensplash](http://wiki.archlinux.org/index.php/Gensplash)
[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

---

