---
title: "Multiple Grubs and partitions of same HDD"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by Shobuz99 on 2011-03-03
I apologize for making a new thread for this, if it turns out I missed one that has my issue. 
I searched through with several different terms and couldn't find it.
I recently got a DELL Inspiron B120 laptop that had Windows 2000 on it as its sole OS. 
I'm refurbishing it to some degree. 
It needs a new LCD Screen and a Wireless Lan card; but that's not important here, I don't think.
I'm running it headless and connecting to my desktop through X11VNC.

I decided to put the live disk Ubuntu 10.04 on it and see if I liked it. I decided yes, and went for the install. 
Before it installed, it asked me how I wanted to partition the drive. 
It showed me examples, and I decided to keep the Windows 2000 on there, along with the little DELL diagnostics, etc. part 
and divide the 40GB drive up into pieces: 18GB for Win2k, 4GB for Dell, and 18GB for Ubuntu 10.04.
Once installed I wanted to change the timeout for the GRUB to longer than 3 seconds before it boots the top choice (which is Ubuntu). 
I noticed when I could catch it; that it was titled GNU Grub 1.98. 
I'm not really familiar with multiple GRUBs, so I didn't think about it. 
Then after a few days, I started getting updates for Ubuntu. 
The first one was the Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic from the original kernel 2.6.32-24-generic. 
Then it went to kernel 2.6.32-29-generic, and yesterday to kernel 2.6.32-30-generic.

That's fine; but the GRUB list is still saying 2.6.32-28-generic as the most recent. 
Also, the last update asked me if I wanted to create a menu.lst file.
I thought I had a GRUB.cfg file that had the list of boots...
But I answered yes anyway, and installed the GRUB menu.lst. 
I changed the timeout to 15 seconds in menu.lst; 
but the list is still showing as the GNU Grub 1.98 and the list of boots is still topped with 2.6.32-28-generic..??? 
I have no idea what's going on now; nor how to update it 
so that I use the GRUB with the menu.lst and delete or suspend the GNU Grub 1.98.
Help. Please.

Rick (shobuz99)

---

### Post by oldfred on 2011-03-03
If you got a menu.lst then you installed grub legacy. But grub.cfg is grub2.

So we can see what is where: 

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

Does it currently boot to the older kernel?

---

### Post by Shobuz99 on 2011-03-03
```
[CODE]
```[/CODE]> **oldfred said:**
> If you got a menu.lst then you installed grub legacy. But grub.cfg is grub2.

So we can see what is where: 

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

Does it currently boot to the older kernel?

ok. I think i did this correctly.

Here's the kernel it currently boots to:
Kernel command line: 
BOOT_IMAGE=/boot/vmlinuz-2.6.32-28-generic root=UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f ro quiet splash

Apparently, it's not 2.6.32.30... like what it says in the Grub Legacy menu.lst

Here are the results.txt of the boot info script;


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  According to the info in the boot sector, sda1 has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        32,129        32,067   6 FAT16
/dev/sda2    *         32,130    35,967,844    35,935,715   7 HPFS/NTFS
/dev/sda3          71,826,615    78,124,094     6,297,480  db CP/M / CTOS / ...
/dev/sda4          35,969,022    71,825,407    35,856,386   5 Extended
/dev/sda5          35,969,024    70,408,191    34,439,168  83 Linux
/dev/sda6          70,410,240    71,825,407     1,415,168  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D6-021C                              vfat       DellUtility                   
/dev/sda2        C848E7F548E7E064                       ntfs                                     
/dev/sda3                                               vfat       DellRestore                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f912c1c5-d4aa-4c2a-ae77-3851a213043f   ext4                                     
/dev/sda6        dcf89a0d-e533-4922-bb61-7a2255c34625   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINNT="Microsoft Windows 2000 Professional" /fastdetect

=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=root=UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f912c1c5-d4aa-4c2a-ae77-3851a213043f

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
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic
uuid		f912c1c5-d4aa-4c2a-ae77-3851a213043f
kernel		/boot/vmlinuz-2.6.32-30-generic root=UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f ro quiet splash 
initrd		/boot/initrd.img-2.6.32-30-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic (recovery mode)
uuid		f912c1c5-d4aa-4c2a-ae77-3851a213043f
kernel		/boot/vmlinuz-2.6.32-30-generic root=UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f ro  single
initrd		/boot/initrd.img-2.6.32-30-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-29-generic
uuid		f912c1c5-d4aa-4c2a-ae77-3851a213043f
kernel		/boot/vmlinuz-2.6.32-29-generic root=UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f ro quiet splash 
initrd		/boot/initrd.img-2.6.32-29-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-29-generic (recovery mode)
uuid		f912c1c5-d4aa-4c2a-ae77-3851a213043f
kernel		/boot/vmlinuz-2.6.32-29-generic root=UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f ro  single
initrd		/boot/initrd.img-2.6.32-29-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic
uuid		f912c1c5-d4aa-4c2a-ae77-3851a213043f
kernel		/boot/vmlinuz-2.6.32-28-generic root=UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f ro quiet splash 
initrd		/boot/initrd.img-2.6.32-28-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic (recovery mode)
uuid		f912c1c5-d4aa-4c2a-ae77-3851a213043f
kernel		/boot/vmlinuz-2.6.32-28-generic root=UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f ro  single
initrd		/boot/initrd.img-2.6.32-28-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-24-generic
uuid		f912c1c5-d4aa-4c2a-ae77-3851a213043f
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		f912c1c5-d4aa-4c2a-ae77-3851a213043f
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Chainload into GRUB 2
root		f912c1c5-d4aa-4c2a-ae77-3851a213043f
kernel		/boot/grub/core.img

title		Ubuntu 10.04.2 LTS, memtest86+
uuid		f912c1c5-d4aa-4c2a-ae77-3851a213043f
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set f912c1c5-d4aa-4c2a-ae77-3851a213043f
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
search --no-floppy --fs-uuid --set f912c1c5-d4aa-4c2a-ae77-3851a213043f
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f912c1c5-d4aa-4c2a-ae77-3851a213043f
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f912c1c5-d4aa-4c2a-ae77-3851a213043f
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f912c1c5-d4aa-4c2a-ae77-3851a213043f
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f912c1c5-d4aa-4c2a-ae77-3851a213043f
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f912c1c5-d4aa-4c2a-ae77-3851a213043f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f912c1c5-d4aa-4c2a-ae77-3851a213043f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07d6-021c
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows 2000 Professional (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c848e7f548e7e064
	drivemap -s (hd0) ${root}
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
UUID=f912c1c5-d4aa-4c2a-ae77-3851a213043f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=dcf89a0d-e533-4922-bb61-7a2255c34625 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  27.4GB: boot/grub/core.img
  22.9GB: boot/grub/grub.cfg
  22.8GB: boot/grub/menu.lst
  27.7GB: boot/initrd.img-2.6.32-24-generic
  27.7GB: boot/initrd.img-2.6.32-28-generic
  27.7GB: boot/initrd.img-2.6.32-29-generic
  27.8GB: boot/initrd.img-2.6.32-30-generic
  27.6GB: boot/vmlinuz-2.6.32-24-generic
  19.9GB: boot/vmlinuz-2.6.32-28-generic
  27.7GB: boot/vmlinuz-2.6.32-29-generic
  27.7GB: boot/vmlinuz-2.6.32-30-generic
  27.8GB: initrd.img
  27.7GB: initrd.img.old
  27.7GB: vmlinuz
  27.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 0d 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 80  0d 02 00 a0 15 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2011-03-03
If you can boot you can do this without the chroot. Note that while both grubs are uninstalled you cannot boot until you finish the reinstall of grub2.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Shobuz99 on 2011-03-04
> **oldfred said:**
> If you can boot you can do this without the chroot. Note that while both grubs are uninstalled you cannot boot until you finish the reinstall of grub2.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

oldfred,
For some reason, I'm confused by what you're saying.
Do you mean that I should have rebooted the machine after I installed from the live disk; 
while the live disk was still in the cdrom drive? Is that why "both grubs are uninstalled"?? 
I did reboot; but I don't remember now, if I removed the CD or not beforehand.

Or are you referring to uninstalled as something different?

Also, Are you saying that I should proceed from Step 2 of that procedure, and skip the beginning because I can already boot up the machine ok?

Sorry for my density here.

Edit: Also, I didn't say this before, but I want the Grub 2 removed and not put back. 
I just want to use the Grub Legacy. Or do I have to use Grub 2??

Rick (shobuz99)

---

### Post by oldfred on 2011-03-04
I am assuming you can boot your install not the liveCD. If you cannot boot your install then you have to use the liveCD to uninstall & reinstall grub including the chroot procedure.

You have grub2 installed to the MBR of sda.

We suggest you use grub2, but if you have an older simple system grub legacy will still work. Either way you have to uninstall both grubs and reinstall one. Grub legacy has not been updated for years and as such does not have support for a lot of the newer configurations. Ubuntu added to its copy of grub 0.97 support for ext4, but other distributions may or may not have even made that tweak. Many other things in grub legacy are just not maintained anymore. 

The grub-common is used by both grub & grub2. The name for grub2 is grub-pc. So you have to reinstall grub or grub-pc and grub-common.

---

### Post by Shobuz99 on 2011-03-04
> **oldfred said:**
> I am assuming you can boot your install not the liveCD. If you cannot boot your install then you have to use the liveCD to uninstall & reinstall grub including the chroot procedure.

You have grub2 installed to the MBR of sda.

We suggest you use grub2, but if you have an older simple system grub legacy will still work. Either way you have to uninstall both grubs and reinstall one. Grub legacy has not been updated for years and as such does not have support for a lot of the newer configurations. Ubuntu added to its copy of grub 0.97 support for ext4, but other distributions may or may not have even made that tweak. Many other things in grub legacy are just not maintained anymore. 

The grub-common is used by both grub & grub2. The name for grub2 is grub-pc. So you have to reinstall grub or grub-pc and grub-common.

OldFred,
Thank you. I can boot my install. 
So that means I still have to uninstall both Grubs and reinstall Grub 2, correct?
So when I received the update for 2.6.32.30, I should NOT have
answered the question "Create menu.lst?" as a 'Yes'...correct?
Or didn't that matter? I say that, because I don't recall deliberately installing Grub Legacy. 
I use it on my Desktop; but wasn't aware of what Grub was being installed by the Live CD on this laptop. 
Apparently, it is Grub 2. 
That's fine and I'll keep it; however, now that I've received updates, starting from  2.6.32.24 to 2.6.32.30 as recently; 
will all that be lost when I uninstall both Grubs and reinstall Grub 2? 
Also, the reason this all came about was I wanted to simply change the boot order and change the timeout from 3 sec to 15 sec in the Grub. 
That's when I discovered it was not Grub legacy.

Thank you for all your continued help.
Rick (shobuz99)

---

### Post by oldfred on 2011-03-04
I have not seen it ask to create a menu.lst. So somewhere grub legacy got involved.

Timeout is in this for grub2
```
gksudo gedit /etc/default/grub
```
Then 
```
sudo update-grub
```

Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by Shobuz99 on 2011-03-04
> **oldfred said:**
> I have not seen it ask to create a menu.lst. So somewhere grub legacy got involved.

Timeout is in this for grub2
```
gksudo gedit /etc/default/grub
```
Then 
```
sudo update-grub
```

Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

I'm happy to report that all went well, and I now have Grub 2 or grub-pc working. 
No more grub legacy and the current version is correct at the top of the list. Thank you for your expert help.
One final question:
If I want to re-order what is listed when Grub appears; what grub file do I edit for that? 
I'm familiar with Grub Legacy's menu.lst format; but not with what file and how to change the order, in grub-pc.

Thank you very much.
Rick (shobuz99)

---

### Post by oldfred on 2011-03-04
Changing menu order is not so easy in grub2. I copied everything I wanted into 40_custom & edited it, but that did not change order. If you want windows first you have to copy a 40_custom to 06_custom and put windows into that. 

If you save the file you create with the custom entry to, say, 09_custom, it will not be over written and will be at the beginning of your menu
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries)

and from Herman's site if your name it 06_custom to be near the top of grub.cfg:
When you are finished putting all of your custom boot entries in your /etc/grub.d/06_custom file, it needs to be chmodded to make it executable,
sudo chmod 755 /etc/grub.d/06_custom
Use a command something like this to change the file permissions to make your file executable.

Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even with grub2.
the quick and easy to make a default boot:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

Link with several of links below:
How to edit bootloader? Feb 2011
[http://ubuntuforums.org/showthread.php?t=1694681](http://ubuntuforums.org/showthread.php?t=1694681)

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by Shobuz99 on 2011-03-04
> **oldfred said:**
> Changing menu order is not so easy in grub2. I copied everything I wanted into 40_custom & edited it, but that did not change order. If you want windows first you have to copy a 40_custom to 06_custom and put windows into that. 

If you save the file you create with the custom entry to, say, 09_custom, it will not be over written and will be at the beginning of your menu
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries)

and from Herman's site if your name it 06_custom to be near the top of grub.cfg:
When you are finished putting all of your custom boot entries in your /etc/grub.d/06_custom file, it needs to be chmodded to make it executable,
sudo chmod 755 /etc/grub.d/06_custom
Use a command something like this to change the file permissions to make your file executable.

Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even with grub2.
the quick and easy to make a default boot:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

Link with several of links below:
How to edit bootloader? Feb 2011
[http://ubuntuforums.org/showthread.php?t=1694681](http://ubuntuforums.org/showthread.php?t=1694681)

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub
OldFred,
Thank you very very much for all the great information.
I have marked as solved.

Rick (shobuz99)

---

### Post by rewyllys on 2011-05-25
I've just encountered a somewhat similar problem. 

My situation is this:  The original pair of hard drives in my desktop computer (which are arranged in a RAID array) contains an installation of Windows Vista.  About two years ago, I added a 1.5-TB hard drive and installed Ubuntu 9.04 on it, with separate partitions for swap and /home. By the first of this month, this installation had progressed to Ubuntu 11.04.  A few days ago, I installed Linux Mint 11rc on another partition on the 1.5TB drive; it uses the existing swap and /home partitions.  GRUB2's default choice of operating system is set as Mint.

Today, I attempted to add Xubuntu 11.04 to still another partition, again using the existing swap and /home partitions.  But when, at the end of installation process, I tried to boot into Xubuntu, I encountered a problem: viz., in GRUB2's display of available OS choices, when I choose the Xubuntu partition, the response is the following:

```

udevd-work[83]: inotify_add_watch(6, /dev/dm-0, 10) failed: No such file or directory

```which after a few seconds disappears and is replaced by this:

```

BusyBox v1.17.1 (Ubuntu1:1.17.1-10 ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)

```For convenience, here is a table of all the partitions on my desktop, as seen by GParted:

```

/dev/mapper/isw_fejhbcdec_RAID1             (465.76 GiB)
/dev/sda                NTFS        931.51 GiB    external storage        
/dev/sdb                NTFS        465.76 GiB    (Windows Vista on RAID)
/dev/sdc                FAT32        15.06 GiB    (flash drive)
/dev/sdh                NTFS        465.76 GiB    (Windows Vista on RAID)
/dev/sdj                        1.3 TiB
/dev/sdj1                ext4        39.07 GiB    / (Linux Mint 11rc)
/dev/sdj2                linux-swap        19.53 GiB
/dev/sdj3                ext4        39.06 GiB    / (Ubuntu 11.04)
/dev/sdj4                extended    
     /dev/sdj5                ext4    39.07 GiB    / (Xubuntu 11.04)
     /dev/sdj6                NTFS    39.07 GiB        (shared data)
     /dev/sdj7                ext4    1.19 TiB    /home

```And here is the output from the Boot Info Script (many thanks to OldFred:)):

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 966e6d53-de27-4fa5-9944-1e996c718c43 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdi.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdj and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/isw_fejhbcdec_RAID1 
    and looks at sector 1 of the same hard drive for core.img. core.img is at 
    this location and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 966e6d53-de27-4fa5-9944-1e996c718c43 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

sdi1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdj1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 11 Katya
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdj2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdj3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdj3 
                       and looks at sector 221888117 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdj4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdj5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdj6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdj6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdj7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

isw_fejhbcdec_RAID11: __________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_fejhbcdec_RAID12: __________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   955,112,444   955,112,382   7 NTFS / exFAT / HPFS
/dev/sda2         955,112,445   976,751,999    21,639,555   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.2 GB, 16173236224 bytes
255 heads, 63 sectors/track, 1966 cylinders, total 31588352 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    31,588,351    31,588,289   c W95 FAT32 (LBA)


Drive: sdi _____________________________________________________________________

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdi1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdj _____________________________________________________________________

Disk /dev/sdj: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdj1    *          2,048    81,947,564    81,945,517  83 Linux
/dev/sdj2         163,863,000   204,828,749    40,965,750  82 Linux swap / Solaris
/dev/sdj3          81,948,672   163,862,527    81,913,856  83 Linux
/dev/sdj4         204,828,811 2,930,272,064 2,725,443,254   f W95 Extended (LBA)
/dev/sdj5         204,828,813   286,760,249    81,931,437  83 Linux
/dev/sdj6         286,760,313   368,691,749    81,931,437   7 NTFS / exFAT / HPFS
/dev/sdj7         368,691,813 2,930,272,064 2,561,580,252  83 Linux


Drive: isw_fejhbcdec_RAID1 _____________________________________________________________________

Disk /dev/mapper/isw_fejhbcdec_RAID1: 500.1 GB, 500104826880 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976767240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_fejhbcdec_RAID11   *             63   955,112,444   955,112,382   7 NTFS / exFAT / HPFS
/dev/mapper/isw_fejhbcdec_RAID12        955,112,445   976,751,999    21,639,555   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/isw_fejhbcdec_RAID1p1 0CE09AC5E09AB504                       ntfs       HP
/dev/mapper/isw_fejhbcdec_RAID1p2 949CA48C9CA46A86                       ntfs       FACTORY_IMAGE
/dev/sda                                                isw_raid_member 
/dev/sdb1        9404-0FFD                              vfat       SYSRESCCD
/dev/sdg                                                isw_raid_member 
/dev/sdi1        DA3C17C53C179C17                       ntfs       
/dev/sdj1        ef86d10d-4ff6-4ab6-ad90-9e321c0d9345   ext4       
/dev/sdj2                                               swap       
/dev/sdj3        6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b   ext4       
/dev/sdj5        935171b9-d7fc-496d-ac6b-056d41c1696c   ext4       
/dev/sdj6        327234A972347427                       ntfs       WindowsM
/dev/sdj7        4b9d1fe9-f445-41c8-b1bb-e45eda6a8e58   ext4       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_fejhbcdec_RAID1
isw_fejhbcdec_RAID1p1
isw_fejhbcdec_RAID1p2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/SYSRESCCD         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdi1        /media/DA3C17C53C179C17  fuseblk    (rw,nosuid,nodev,allow_other,blksize=1024,default_permissions)
/dev/sdj1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdj7        /home                    ext4       (rw,commit=0)


============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default rescuecd
append initrd=initram.igz scandelay=5
timeout 300
prompt 1
display f1boot.msg
F1 f1boot.msg
F2 f2images.msg
F3 f3params.msg
F4 f4arun.msg
F5 f5troubl.msg
F6 f6pxe.msg
F7 f7net.msg
label rescue64
  kernel rescue64
  append initrd=initram.igz scandelay=5
label altker32
  kernel altker32
  append initrd=initram.igz video=ofonly scandelay=5
label altker64
  kernel altker64
  append initrd=initram.igz video=ofonly scandelay=5
label vmlinuz2
  kernel altker32
  append initrd=initram.igz video=ofonly scandelay=5
label vesa
  kernel rescuecd
  append initrd=initram.igz forcevesa scandelay=5
label fr
  kernel rescuecd
  append initrd=initram.igz setkmap=fr scandelay=5
label uk
  kernel rescuecd
  append initrd=initram.igz setkmap=uk scandelay=5
label us
  kernel rescuecd
  append initrd=initram.igz setkmap=us scandelay=5
label nokeymap
  kernel rescuecd
  append initrd=initram.igz setkmap=us scandelay=5
label minishell
  kernel rescuecd
  append initrd=initram.igz scandelay=5 minishell=/bin/ash
label rescuehd
  kernel rescuecd
  append init=/sbin/init
label reschd32
  kernel rescuecd
  append init=/sbin/init
label reschd64
  kernel rescue64
  append init=/sbin/init
label freedos
  kernel memdisk
  append initrd=freedos.img floppy
label memtest
  kernel memdisk
  append initrd=memtestp.img floppy
label ranish
  kernel memdisk
  append initrd=ranish.img floppy
label aida
  kernel memdisk
  append initrd=aida.img floppy
label ntpass
  kernel memdisk
  append initrd=ntpass.img floppy c=3 h=64 s=32
label gag
  kernel memdisk
  append initrd=gag.img floppy
label dban
  kernel memdisk
  append initrd=dban.img floppy
label mhdd
  kernel memdisk
  append initrd=mhdd.img floppy
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux.cfg                                   1

=========================== sdj1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdj,msdos1)'
search --no-floppy --fs-uuid --set=root ef86d10d-4ff6-4ab6-ad90-9e321c0d9345
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdj,msdos1)'
search --no-floppy --fs-uuid --set=root ef86d10d-4ff6-4ab6-ad90-9e321c0d9345
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
insmod part_msdos
insmod ext2
set root='(/dev/sdj,msdos1)'
search --no-floppy --fs-uuid --set=root ef86d10d-4ff6-4ab6-ad90-9e321c0d9345
insmod png
if background_image /boot/grub/linuxmint.png; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sdj,msdos1)'
search --no-floppy --fs-uuid --set=root ef86d10d-4ff6-4ab6-ad90-9e321c0d9345
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

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
menuentry 'Linux Mint 11 64-bit, 2.6.38-8-generic (/dev/sdj1)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos1)'
    search --no-floppy --fs-uuid --set=root ef86d10d-4ff6-4ab6-ad90-9e321c0d9345
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=ef86d10d-4ff6-4ab6-ad90-9e321c0d9345 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Linux Mint 11 64-bit, 2.6.38-8-generic (/dev/sdj1) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos1)'
    search --no-floppy --fs-uuid --set=root ef86d10d-4ff6-4ab6-ad90-9e321c0d9345
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=ef86d10d-4ff6-4ab6-ad90-9e321c0d9345 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos1)'
    search --no-floppy --fs-uuid --set=root ef86d10d-4ff6-4ab6-ad90-9e321c0d9345
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos1)'
    search --no-floppy --fs-uuid --set=root ef86d10d-4ff6-4ab6-ad90-9e321c0d9345
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdj3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos3)'
    search --no-floppy --fs-uuid --set=root 6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b ro vga=795 quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdj3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos3)'
    search --no-floppy --fs-uuid --set=root 6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b ro single vga=795
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdj5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos5)'
    search --no-floppy --fs-uuid --set=root 65cb3faa-6752-4a0a-8e94-a19d758ddba8
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=65cb3faa-6752-4a0a-8e94-a19d758ddba8 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdj5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos5)'
    search --no-floppy --fs-uuid --set=root 65cb3faa-6752-4a0a-8e94-a19d758ddba8
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=65cb3faa-6752-4a0a-8e94-a19d758ddba8 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Windows Vista (loader) (on /dev/mapper/isw_fejhbcdec_RAID1p1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd5,msdos1)'
    search --no-floppy --fs-uuid --set=root 0CE09AC5E09AB504
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/mapper/isw_fejhbcdec_RAID1p2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd5,msdos2)'
    search --no-floppy --fs-uuid --set=root 949CA48C9CA46A86
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

=============================== sdj1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdj1 during installation
UUID=ef86d10d-4ff6-4ab6-ad90-9e321c0d9345 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdj7 during installation
UUID=4b9d1fe9-f445-41c8-b1bb-e45eda6a8e58 /home           ext4    defaults        0       2
/dev/sdj2       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdj1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  16.201404572 = 17.396125696   boot/grub/core.img                             1
   2.956333160 = 3.174338560    boot/grub/grub.cfg                             1
   0.672851562 = 0.722468864    boot/initrd.img-2.6.38-8-generic               2
  16.133792877 = 17.323528192   boot/vmlinuz-2.6.38-8-generic                  1
   0.672851562 = 0.722468864    initrd.img                                     2
  16.133792877 = 17.323528192   vmlinuz                                        1

=========================== sdj3/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(/dev/sdj,msdos3)'
search --no-floppy --fs-uuid --set=root 6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdj,msdos3)'
search --no-floppy --fs-uuid --set=root 6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b
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
    set root='(/dev/sdj,msdos3)'
    search --no-floppy --fs-uuid --set=root 6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b ro  vga=795  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos3)'
    search --no-floppy --fs-uuid --set=root 6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b ro single  vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos3)'
    search --no-floppy --fs-uuid --set=root 6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos3)'
    search --no-floppy --fs-uuid --set=root 6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 11 64-bit, 2.6.38-8-generic (/dev/sdj1) (on /dev/sdj1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos1)'
    search --no-floppy --fs-uuid --set=root ef86d10d-4ff6-4ab6-ad90-9e321c0d9345
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=ef86d10d-4ff6-4ab6-ad90-9e321c0d9345 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Linux Mint 11 64-bit, 2.6.38-8-generic (/dev/sdj1) -- recovery mode (on /dev/sdj1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos1)'
    search --no-floppy --fs-uuid --set=root ef86d10d-4ff6-4ab6-ad90-9e321c0d9345
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=ef86d10d-4ff6-4ab6-ad90-9e321c0d9345 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdj5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos5)'
    search --no-floppy --fs-uuid --set=root 935171b9-d7fc-496d-ac6b-056d41c1696c
    linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sdi5 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdj5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdj,msdos5)'
    search --no-floppy --fs-uuid --set=root 935171b9-d7fc-496d-ac6b-056d41c1696c
    linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sdi5 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Windows Vista (loader) (on /dev/mapper/isw_fejhbcdec_RAID1p1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd5,msdos1)'
    search --no-floppy --fs-uuid --set=root 0CE09AC5E09AB504
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/mapper/isw_fejhbcdec_RAID1p2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd5,msdos2)'
    search --no-floppy --fs-uuid --set=root 949CA48C9CA46A86
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

=============================== sdj3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdj3 during installation
UUID=6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdj7 during installation
UUID=4b9d1fe9-f445-41c8-b1bb-e45eda6a8e58 /home           ext4    defaults        0       2
/dev/sdj2       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdj3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  75.210708618 = 80.756883456   boot/grub/core.img                             1
  71.285228729 = 76.541931520   boot/grub/grub.cfg                             1
  44.369895935 = 47.641812992   boot/initrd.img-2.6.38-8-generic               1
  75.208988190 = 80.755036160   boot/vmlinuz-2.6.38-8-generic                  1
  44.369895935 = 47.641812992   initrd.img                                     1
  75.208988190 = 80.755036160   vmlinuz                                        1

=========================== sdj5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdi,msdos5)'
search --no-floppy --fs-uuid --set=root 65cb3faa-6752-4a0a-8e94-a19d758ddba8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdi,msdos5)'
search --no-floppy --fs-uuid --set=root 65cb3faa-6752-4a0a-8e94-a19d758ddba8
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
    set root='(/dev/sdi,msdos5)'
    search --no-floppy --fs-uuid --set=root 65cb3faa-6752-4a0a-8e94-a19d758ddba8
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sdi5 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdi,msdos5)'
    search --no-floppy --fs-uuid --set=root 65cb3faa-6752-4a0a-8e94-a19d758ddba8
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sdi5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdi,msdos5)'
    search --no-floppy --fs-uuid --set=root 65cb3faa-6752-4a0a-8e94-a19d758ddba8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdi,msdos5)'
    search --no-floppy --fs-uuid --set=root 65cb3faa-6752-4a0a-8e94-a19d758ddba8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 11 64-bit, 2.6.38-8-generic (/dev/sdj1) (on /dev/sdi1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdi,msdos1)'
    search --no-floppy --fs-uuid --set=root ef86d10d-4ff6-4ab6-ad90-9e321c0d9345
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=ef86d10d-4ff6-4ab6-ad90-9e321c0d9345 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Linux Mint 11 64-bit, 2.6.38-8-generic (/dev/sdj1) -- recovery mode (on /dev/sdi1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdi,msdos1)'
    search --no-floppy --fs-uuid --set=root ef86d10d-4ff6-4ab6-ad90-9e321c0d9345
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=ef86d10d-4ff6-4ab6-ad90-9e321c0d9345 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdi3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdi,msdos3)'
    search --no-floppy --fs-uuid --set=root 6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b ro vga=795 quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdi3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdi,msdos3)'
    search --no-floppy --fs-uuid --set=root 6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=6d3c6dcd-bdea-43fe-b9d9-da368ab23b2b ro single vga=795
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Windows Vista (loader) (on /dev/mapper/isw_fejhbcdec_RAID1p1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd5,msdos1)'
    search --no-floppy --fs-uuid --set=root 0CE09AC5E09AB504
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/mapper/isw_fejhbcdec_RAID1p2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd5,msdos2)'
    search --no-floppy --fs-uuid --set=root 949CA48C9CA46A86
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

=============================== sdj5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdi5 during installation
UUID=935171b9-d7fc-496d-ac6b-056d41c1696c /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdi7 during installation
UUID=4b9d1fe9-f445-41c8-b1bb-e45eda6a8e58 /home           ext4    defaults        0       2
/dev/sdi2       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdj5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 105.804525852 = 113.606744576  boot/grub/core.img                             1
 123.840116978 = 132.972313088  boot/grub/grub.cfg                             1
  99.216864109 = 106.533296640  boot/initrd.img-2.6.38-8-generic               2
 105.802805424 = 113.604897280  boot/vmlinuz-2.6.38-8-generic                  1
  99.216864109 = 106.533296640  initrd.img                                     2
 105.802805424 = 113.604897280  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sdb1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 10 26 00  |.X.MSDOS5.0...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 ff e1 01 31 3c 00 00  00 00 00 00 02 00 00 00  |....1<..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 fd 0f 04 94 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 42 4f  |..............BO|
000001b0  4f 54 4d 47 52 20 69 73  20 6d 69 73 73 69 6e 67  |OTMGR is missing|
000001c0  ff 0d 0a 44 69 73 6b 20  65 72 72 6f 72 ff 0d 0a  |...Disk error...|
000001d0  50 72 65 73 73 20 61 6e  79 20 6b 65 79 20 74 6f  |Press any key to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  00 ac c1 ce 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on isw_fejhbcdec_RAID11


Unknown BootLoader on isw_fejhbcdec_RAID12



========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf sdh 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
unlzma: Decoder error
hexdump: /dev/mapper/isw_fejhbcdec_RAID11: No such file or directory
hexdump: /dev/mapper/isw_fejhbcdec_RAID11: No such file or directory
hexdump: /dev/mapper/isw_fejhbcdec_RAID12: No such file or directory
hexdump: /dev/mapper/isw_fejhbcdec_RAID12: No such file or directory

```At present, I can boot into only Linux Mint and Ubuntu 11.04.  What should I do to be able to boot into Xubunt 11.04 also?

---

### Post by oldfred on 2011-05-26
Lots of grub2 entires. I do not understand RAID, but it looks like the only grub that boots is the one on your non-RAID drive. The others seem to refer to UUIDs that now do not exist.

menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdj5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='([COLOR=Red]/dev/sdj,msdos5[/COLOR])'
    search --no-floppy --fs-uuid --set=root [COLOR=Red]935171b9-d7fc-496d-ac6b-056d41c1696c[/COLOR]
    linux /boot/vmlinuz-2.6.38-8-generic root=[COLOR=Red]/dev/sdi5[/COLOR] ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}

All of the red above have to match. It looks like when you installed Kubuntu, it saw it as sdi not sdj. You should be able to boot just by changing the /dev/sdi5 to /dev/sdj5 as the UUID and set root are all sdj's partition from the boot script. But if as booting it is not sdj then you have to edit the set root and or search also.

When booting at the grub menu select e and then edit the i to j in the Kubuntu entry. It should boot.

Run this in Kubuntu to update its grub.cfg.
sudo update-grub

If it does not see the drive as sdj then you need to change from drive to UUID in the linux line. The grub os-prober in Ubuntu uses the grub.cfg in Kubuntu to add its entry, so that is why an inconsistency.

I also do not like sharing /home. The actual settings are small compared to your hard drive. My /home is about 1GB and 3/4's of that is my /wine with Picasa which I have not moved to my data partition yet. If you want some settings the same just copy to your other installs /home. You have most of your data not in /home anyway. I use a /data for all my data that would normally be in /home. Some do not like that but it works when all are Debian based as the user & group ids are the same.

---

### Post by rewyllys on 2011-05-30
> **oldfred said:**
> . . . . 
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdj5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='([COLOR=Red]/dev/sdj,msdos5[/COLOR])'
    search --no-floppy --fs-uuid --set=root [COLOR=Red]935171b9-d7fc-496d-ac6b-056d41c1696c[/COLOR]
    linux /boot/vmlinuz-2.6.38-8-generic root=[COLOR=Red]/dev/sdi5[/COLOR] ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}

All of the red above have to match. It looks like when you installed Kubuntu, it saw it as sdi not sdj. You should be able to boot just by changing the /dev/sdi5 to /dev/sdj5 as the UUID and set root are all sdj's partition from the boot script. But if as booting it is not sdj then you have to edit the set root and or search also.

When booting at the grub menu select e and then edit the i to j in the Kubuntu entry. It should boot.

Run this in Kubuntu to update its grub.cfg.
sudo update-grub
. . . .

I also do not like sharing /home. The actual settings are small compared to your hard drive. My /home is about 1GB and 3/4's of that is my /wine with Picasa which I have not moved to my data partition yet. If you want some settings the same just copy to your other installs /home. You have most of your data not in /home anyway. I use a /data for all my data that would normally be in /home. Some do not like that but it works when all are Debian based as the user & group ids are the same.

Please pardon my slow response -- lots of family guests for the Memorial Day Weekend have interfered with my getting to my computers.
Once again, OldFred, many thanks to you.:popcorn:
You spotted the problem, viz., the inconsistency.  I tried to handle the problem using your first suggestion, that of using the "e" option in the boot menu, but that failed.  Then I followed your second suggestion, running "sudo update-grub", and that finally worked.

I'd appreciate your expanding on why you "do not like sharing /home".  Doing so has worked for me so far, but your comment makes me worry that I'm running risks that I don't understand.

Thanks again!

---

