---
title: "GRUB loading stage 1.5 error 15"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by missfroguk on 2010-11-02
Hi,

I have had ubuntu on my PC for 2 years without any problem. I am dual-booting between Ubuntu and Vista from a 2yr-old TOSHIBA laptop. The version of Ubuntu I was using is 9.10 (ok, should have updated a while back, mea culpa...)

Yesterday I couldn't load Ubuntu and I got a message ```
ALERT! /dev/disk/by-uuid/[long number] done not exist. Dropping to a shell!

``` 

I managed to sort out the problem thanks to this post 

[http://ubuntuforums.org/showthread.php?t=1355385]("http://ubuntuforums.org/showthread.php?t=1355385")
and used Ubuntu without any problem.

Now today I tried to switch the computer on again and I am getting the error message
```
GRUB loading stage 1.5

GRUB loading, please wait...
Error 15
```

Following the advice on the post above, I updated GRUB to GRUB2 last night. Maybe I shouldn't have...

The screen with the GRUB error message comes before the screen that would let me choose between Vista and Ubuntu and won't let me use a command prompt or anything. The only thing I seem to be able to access is if I press F2 at start up which takes me to the Setup utility screen or F12 which takes me to the Boot Manager.

Any help would be appreciated as, in effect, my computer is useless as it is now...

---

### Post by Quackers on 2010-11-02
Please boot from your Ubuntu Live cd/usb and after making sure you have an internet connection please go to the site below and download the boot script to your DESKTOP and run the script in a terminal using the command given on the first page of that site. This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. To get CODE tags click on New Reply and then on the # symbol in the toolbar.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by missfroguk on 2010-11-02
Thank you Quackers. I have tried to boot from the CD I first intalled Ubunutu from by selecting

```
Try Ubuntu without any changes to your computer
```

After hearing the Ubuntu start-up music, which I thought would be a good sign, this led me to a screen with a lot of horizontal orangy/grey stripes from which I couldn't move on (see picture of screen on link [http://www.flickr.com/photos/missfroguk/5141463718/]("http://www.flickr.com/photos/missfroguk/5141463718/")).

I then tried again but this time chose 
```
Check the integrity of the CD
```

which it did and it didn't find any errors.

Any suggestions? Does this problem ring any bell or is it just that I am not booting from the CD as I should?

Also, should I get the new Ubuntu version on a USB stick and try and boot from that, even though my installed version in an earlier one?
Thanks.

---

### Post by Quackers on 2010-11-03
Have you ever booted from the live cd before? I suspect trying from a usb may have the same outcome unfortunately, as it would appear to be a graphics problem.
I found this from a previous thread, you could try these options

Plug in the live CD - when booting, press any key and you should be presented with 6 options.
Press either F6 or tab (I think) - add
nomodeset nolapic
BEFORE quiet splash
press the option to boot.
Hopefully you will get to the desktop.
If you dont. Try booting with
nomodeset noapic
or
nomodeset noacpi
or
nomodeset acpi=off

---

### Post by missfroguk on 2010-11-03
> Plug in the live CD - when booting, press any key and you should be presented with 6 options.
Press either F6 or tab (I think) - add
nomodeset nolapic
BEFORE quiet splash


I did this and now I get a black screen with 
```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands
```

Still no sign of me being able to access a terminal to do what you suggested in your 1st post. Any idea what the next stage should be...?
Thanks

---

### Post by missfroguk on 2010-11-03
Ok, I have managed to boot Ubuntu from a USB stick. I think the problem I had with all the horizontal lines came from the CD.

So the RESULTS.txt file is as such:```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   315,318,263   312,244,216   7 HPFS/NTFS
/dev/sda3         315,318,272   471,540,247   156,221,976   7 HPFS/NTFS
/dev/sda4         471,555,945   625,137,344   153,581,400   5 Extended
/dev/sda5         471,556,008   625,137,344   153,581,337  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
22 heads, 34 sectors/track, 10469 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             52     7,831,551     7,831,500   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D4FE55B0FE558C1C                       ntfs       WinRE                         
/dev/sda2        642857B22857824A                       ntfs       Vista                         
/dev/sda3        08BC59E8BC59D0B4                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        ddd17b2d-9a20-49c5-844e-581156370926   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3433-3231                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda2/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=ddd17b2d-9a20-49c5-844e-581156370926

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

title		Chainload into GRUB 2
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Ubuntu 9.10, kernel 2.6.31-22-generic
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio quiet splash
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio quiet splash
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio quiet splash
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio quiet splash
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio quiet splash
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio quiet splash
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio quiet splash
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio quiet splash
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio quiet splash
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.27-15-generic
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio quiet splash
initrd		/boot/initrd.img-2.6.27-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-15-generic (recovery mode)
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio single
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 9.10, memtest86+
uuid		ddd17b2d-9a20-49c5-844e-581156370926
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio  quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro single ROOTFLAGS=syncio
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio  quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro single ROOTFLAGS=syncio
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro single ROOTFLAGS=syncio
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio  quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro single ROOTFLAGS=syncio
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio  quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro single ROOTFLAGS=syncio
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio  quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro single ROOTFLAGS=syncio
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio  quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro single ROOTFLAGS=syncio
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro single ROOTFLAGS=syncio
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio  quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro single ROOTFLAGS=syncio
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.27-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.27-15-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro ROOTFLAGS=syncio  quiet splash
	initrd	/boot/initrd.img-2.6.27-15-generic
}
menuentry "Ubuntu, Linux 2.6.27-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ddd17b2d-9a20-49c5-844e-581156370926
	linux	/boot/vmlinuz-2.6.27-15-generic root=UUID=ddd17b2d-9a20-49c5-844e-581156370926 ro single ROOTFLAGS=syncio
	initrd	/boot/initrd.img-2.6.27-15-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 642857b22857824a
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ddd17b2d-9a20-49c5-844e-581156370926 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 318.1GB: boot/grub/core.img
 318.2GB: boot/grub/grub.cfg
 318.1GB: boot/grub/menu.lst
 318.1GB: boot/initrd.img-2.6.27-15-generic
 318.1GB: boot/initrd.img-2.6.28-16-generic
 318.1GB: boot/initrd.img-2.6.31-14-generic
 318.1GB: boot/initrd.img-2.6.31-15-generic
 318.0GB: boot/initrd.img-2.6.31-16-generic
 318.1GB: boot/initrd.img-2.6.31-17-generic
 318.1GB: boot/initrd.img-2.6.31-19-generic
 318.2GB: boot/initrd.img-2.6.31-20-generic
 318.1GB: boot/initrd.img-2.6.31-21-generic
 318.2GB: boot/initrd.img-2.6.31-22-generic
 318.0GB: boot/vmlinuz-2.6.27-15-generic
 318.1GB: boot/vmlinuz-2.6.28-16-generic
 318.1GB: boot/vmlinuz-2.6.31-14-generic
 318.1GB: boot/vmlinuz-2.6.31-15-generic
 318.1GB: boot/vmlinuz-2.6.31-16-generic
 318.0GB: boot/vmlinuz-2.6.31-17-generic
 318.1GB: boot/vmlinuz-2.6.31-19-generic
 318.1GB: boot/vmlinuz-2.6.31-20-generic
 318.2GB: boot/vmlinuz-2.6.31-21-generic
 318.2GB: boot/vmlinuz-2.6.31-22-generic
 318.2GB: initrd.img
 318.1GB: initrd.img.old
 318.2GB: vmlinuz
 318.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 80 00 34 00 00 00  |........?...4...|
00000020  cc 7f 77 00 d2 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 31 32 33 34 20  20 20 20 20 20 20 20 20  |..)1234         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 1c 7f 37 00  66 ba 00 00 00 00 bb 00  |}.f...7.f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



``` 

I hope this helps and I'm looking forward to be able to use my favourite OS again!

---

### Post by oldfred on 2010-11-04
Error 15 is often a conflict between old grub & grub2. Although grub legacy was supposed to let you boot and then boot into grub2. (As your menu.lst shows)

You also have wubi in your windows partiiton. Were/are you using wubi?

You have an install of Ubuntu in sda5, but no swap partition.

If your main install is sda5, you should uninstall grub legacy & grub2 and cleanly reinstall grub2. If your real install is the wubi install then you need a windows boot loader in the MBR.

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by missfroguk on 2010-11-06
Solved! It was pretty simple once I knew what to do. I went on the first link oldfred suggested, booted ubuntu from a usb and typed these commands in the terminal.

```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
```

When I rebooted from the drive, it worked! Thank you to Quackers and oldfred for your help.

Two last questions: 
1 - I am not using wubi and I don't know why I have got that in my files. Is it safe to just delete the files or should I leave them and forget about them?
2 - As I said in my first post, I am currently using Ubuntu 9.10. The problems started after I installed the latest updates. I saw there were 24 updates waiting for me this time and I am a little anxious to download them. Would you advise I did or should I simply upgrade to 10.10? Do you anticipate any problems if I upgrade or update considering this "bleep" in my otherwise pain-free relationship with Ubuntu?

Thanks again for everything!

---

### Post by Quackers on 2010-11-06
Very nice, well done :-)

1 - Strange, but I don't think they'll do any harm where they are.
2 - Back up your home folder then run the updates. If you are thinking of upgrading an way, what's the harm? With regard to upgrading lots of people on here recommend a new install rather than upgrading as sometimes problems can ensue. It may be worth downloading 10.04 (as it's a LTS) or 10.10 and burning it to disc, then using "try Ubuntu" to make sure everything works before you change.

---

### Post by oldfred on 2010-11-06
Wubi is intended to be uninstalled from windows. But if that does not work I think you can just delete it but you may have bits and pieces left.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

If you had some video issues with liveCD, you may also with new install. I had to use the nomodeset for both liveCD and first boot, but once my Nvidia drivers were installed I have had no issues.

---

