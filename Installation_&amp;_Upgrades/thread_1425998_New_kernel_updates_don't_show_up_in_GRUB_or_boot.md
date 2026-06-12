---
title: "New kernel updates don't show up in GRUB or boot"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by WayneL on 2010-03-09
Hi,
I'm currently running Karmic 9.10 in dual boot with Windows 2000. My computer has automatically updated and installed kernels 2.6.31-17, -19 and -20 (They show up in Synaptic as installed). 

However, the newest kernel choice in my GRUB menu is 2.6.31-16-generic (followed by -15 and -14). These all start without any errors.

Question: Why haven't the newer updates shown up in GRUB for booting purposes?

Could it be a question that I didn't answer correctly some time back about accepting or not accepting an update or change in GRUB?

How can this be changed? The new kernels do not show up in Start-Up Manager either.

Thanks!
Wayne

---

### Post by zvacet on 2010-03-10
In terminal type


```
sudo update-grub
```

---

### Post by WayneL on 2010-03-10
I tried "update-grub," and its  response was to show the missing kernels were being updated in GRUB (GRUB 1.97 beta4).

However, on restart, the new kernels did not show up; I still had access to the same ones: 16, 15 and 14. The new kernels didn't show up in the StartUp Manager selections either.

Again to say: Everything works just fine with kernel -16-generic. So it's not like the system is not functioning. 

Thanks!
Wayne

---

### Post by jamere on 2010-03-10
You are not alone...I have the same problem and questions.:confused:

---

### Post by drs305 on 2010-03-10
Wayne, Welcome to the Ubuntu forums.

Would you run meierfra.'s boot info script so we can take a look.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

Please post the results between code tags, which you can call up by clicking on the **#** icon in the post's menu.

---

### Post by WayneL on 2010-03-10
Thanks so much!
OK, script worked fine. It's a great tool!
Here are the results:
Wayne
--------------------------------------------------

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3642df86

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,232,124   156,232,062   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.5 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders, total 40020624 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12fc12fb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     2,923,829     2,923,767  82 Linux swap / Solaris
/dev/sdb2           2,923,830    40,017,914    37,094,085   5 Extended
/dev/sdb5           2,923,893    40,017,914    37,094,022  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004d0f3

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   312,544,574   312,544,512   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E680CF2480CEFA57                       ntfs       C-Drive                       
/dev/sdb1        0629bb22-66a1-42b8-b9a6-aeefe64806a5   swap                                     
/dev/sdb5        ee2123d8-2817-4013-a5d3-de6a44cee0ee   ext4                                     
/dev/sdc1        90A83781A837653E                       ntfs       Photos                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/Photos            fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect


=========================== sdb5/boot/grub/menu.lst: ===========================

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
default saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ee2123d8-2817-4013-a5d3-de6a44cee0ee

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

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		ee2123d8-2817-4013-a5d3-de6a44cee0ee
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		ee2123d8-2817-4013-a5d3-de6a44cee0ee
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		ee2123d8-2817-4013-a5d3-de6a44cee0ee
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		ee2123d8-2817-4013-a5d3-de6a44cee0ee
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		ee2123d8-2817-4013-a5d3-de6a44cee0ee
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		ee2123d8-2817-4013-a5d3-de6a44cee0ee
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		ee2123d8-2817-4013-a5d3-de6a44cee0ee
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		ee2123d8-2817-4013-a5d3-de6a44cee0ee
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		ee2123d8-2817-4013-a5d3-de6a44cee0ee
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		ee2123d8-2817-4013-a5d3-de6a44cee0ee
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		ee2123d8-2817-4013-a5d3-de6a44cee0ee
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		ee2123d8-2817-4013-a5d3-de6a44cee0ee
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		ee2123d8-2817-4013-a5d3-de6a44cee0ee
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		ee2123d8-2817-4013-a5d3-de6a44cee0ee
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set ee2123d8-2817-4013-a5d3-de6a44cee0ee
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ee2123d8-2817-4013-a5d3-de6a44cee0ee
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ee2123d8-2817-4013-a5d3-de6a44cee0ee
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ee2123d8-2817-4013-a5d3-de6a44cee0ee
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ee2123d8-2817-4013-a5d3-de6a44cee0ee
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ee2123d8-2817-4013-a5d3-de6a44cee0ee
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set ee2123d8-2817-4013-a5d3-de6a44cee0ee
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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
menuentry "Microsoft Windows 2000 Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e680cf2480cefa57
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

proc            /proc           proc    defaults        0       0
UUID=ee2123d8-2817-4013-a5d3-de6a44cee0ee /               ext4    errors=remount-ro 0       1
UUID=0629bb22-66a1-42b8-b9a6-aeefe64806a5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/core.img
   8.7GB: boot/grub/grub.cfg
   7.2GB: boot/grub/menu.lst
   3.2GB: boot/initrd.img-2.6.31-14-generic
   5.7GB: boot/initrd.img-2.6.31-15-generic
   8.5GB: boot/initrd.img-2.6.31-16-generic
  18.1GB: boot/initrd.img-2.6.31-17-generic
   8.6GB: boot/initrd.img-2.6.31-19-generic
  19.4GB: boot/initrd.img-2.6.31-20-generic
   2.2GB: boot/vmlinuz-2.6.31-14-generic
   3.4GB: boot/vmlinuz-2.6.31-15-generic
   2.4GB: boot/vmlinuz-2.6.31-16-generic
  10.5GB: boot/vmlinuz-2.6.31-17-generic
   7.4GB: boot/vmlinuz-2.6.31-19-generic
  18.4GB: boot/vmlinuz-2.6.31-20-generic
  19.4GB: initrd.img
   8.6GB: initrd.img.old
  18.4GB: vmlinuz
   7.4GB: vmlinuz.old
```

---

### Post by drs305 on 2010-03-10
The boot info script shows you are using Grub 2. It does show Grub 2 installed to the sda MBR while the grub files are installed on the Ubuntu partition on sdb (sdb5). 

I assume you did an upgrade from Grub legacy to Grub 2 since menu.lst still exists (and is being updated with the new kernels). 

As long as you are using Grub 2 (you should see version 1.97 or higher at the top of the Grub menu during boot), I would recommend you rename menu.lst (since update-grub sees it) and then reinstall Grub 2 to sdb.

```

sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo grub-install /dev/sdb
sudo update-grub

```

See if the menu is properly constructed after running update-grub.

If it still isn't working correctly, you could try purging grub (legacy) completely to ensure no traces of it are left behind:
```
sudo apt-get purge grub
```

One other note: By installing Grub 2 on sdb, you may notice it takes longer for the Grub 2 menu to display. To speed things up, changing the computer's BIOS to make the Ubuntu device boot first will speed things up.

Check your /boot/grub/grub.cfg file contents before rebooting to make sure everything still looks correct - pointing to the correct UUID, hd1,5, etc.

---

### Post by WayneL on 2010-03-11
Hello,
I did the first three steps you suggested, and in sudo update-grub, it saw that I had no menu.lst (after we renamed it in the first step), and asked me if I wanted to create it. I said "Yes." Should I have said yes? In any case, it did, and it looked like it might have added the extra items, but the final result is still the same as it was before--not showing the latest three choices. Same is true for the Start-Up Manager selection choices.

If I had said NO to the question, would I still have had a menu on boot? And would it still have included the Windows 2000 choice?

Thanks very much!
Wayne

---

### Post by drs305 on 2010-03-11
> **WayneL said:**
> Hello,
I did the first three steps you suggested, and in sudo update-grub, it saw that I had no menu.lst (after we renamed it in the first step), and asked me if I wanted to create it. I said "Yes." Should I have said yes? In any case, it did, and it looked like it might have added the extra items, but the final result is still the same as it was before--not showing the latest three choices. Same is true for the Start-Up Manager selection choices.

If I had said NO to the question, would I still have had a menu on boot? And would it still have included the Windows 2000 choice?

Thanks very much!
Wayne

The grub-install command was apparently still trying to put Grub legacy back on your machine if it was asking about "menu.lst".

Let's just start over and purge Grub. This isn't going to hurt your machine unless you lose power and can't complete the process.
```

sudo apt-get purge grub grub-pc grub-common

```
As you run this, it will warn that you will be left with an unbootable system. That's ok as you will be adding it back in the next step. Tab to "Yes" and ENTER.
```
sudo apt-get install grub-pc grub-common
```
As this runs, you will be asked if you want to add anything to the Grub 2 command lines. Accept the defaults by pressing TAB to highlight "OK" and continue.

When you get to the list of devices, use up/down to highlight "sdb", press the space bar to select it, and then tab to "OK" and press ENTER.

If it doesn't see your Windows install as it creates the initial grub.cfg run "sudo update-grub" after boot and it should find your Windows install.

[COLOR="DarkRed"]**ADDED:**[/COLOR] My attempts have been directed toward fixing your system and not just the menu itself. There is something wrong with your Grub installation since updates keep beging directed to Grub legacy's menu.lst. There is a band-aid fix that might work in updating your grub.cfg menu, since the command is directed specifically toward grub.cfg. You could try running the following to see if it forces an update to grub.cfg:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
If this works you may decide to simply live with what you have and run this command instead of update-grub. There would still be a systemic problem with your grub installation but depending on your risk tolerance this fix may be enough for you until your next install.

---

### Post by WayneL on 2010-03-11
OK, I purged grub and reinstalled it as you suggested. Now everything is PERFECT!  All kernels show up--and Windows 2000 as well--on the grub menu.


When asked whether I wanted to accept the Local or Maintainer's version of configuration, I selected Local. I guess this was the right decision. I was faced with this question when I upgraded or installed the latest version of Ubuntu, and I wasn't sure which way to answer the question.


Thanks so much!


One other question: Is there any easy tool to use to remove the old kernels I no longer use from the hard drive plus remove them from grub? I used to edit the menu list in earlier days (before karmic).

Thanks again!
Wayne

---

### Post by drs305 on 2010-03-11
> **WayneL said:**
> OK, I purged grub and reinstalled it as you suggested. Now everything is PERFECT!  All kernels show up--and Windows 2000 as well--on the grub menu.


When asked whether I wanted to accept the Local or Maintainer's version of configuration ... and I wasn't sure which way to answer the question.

Is there any easy tool to use to remove the old kernels I no longer use from the hard drive plus remove them from grub? I used to edit the menu list in earlier days (before karmic).


Congratulations!

As far as accepting the maintainer's version, I usually accept it. The reason is that it will include updates which the developers have included in one of the Grub 2 files. For instance, the latest update included a "beep" option when the grub menu appears. Now obviously this is a minor thing, but it could be something even more helpful.

One reason for keeping your current version would be if you had heavily modified your configuration files. These modifications would be removed once the maintainer's version is installed. What I do is make copies of my modifications elsewhere and just plug them back in after the update.

In recent years there has been a great improvement in the upgrade process. You are now given several options to review what the changes are and then make an informed decision. 

As to the kernel issue, I wrote a guide a while back about the number of kernels displayed and how to change that number. It expanded to discuss StartUp-Manager. But for you, the important section is the "Removing Older Kernels" section. There I discuss the various methods to remove them. I recommend installing Ubuntu-Tweak and explain how to use it.

Here is the link:  [URL="http://ubuntuforums.org/showthread.php?t=818177"] HOWTO: StartUp Manager & Kernel Display Options
[/URL]

---

### Post by WayneL on 2010-03-11
Thanks so much. You've been very helpful. I usually operate this machine about 60% of the time on Linux and 40% on Windows. I tried several early versions of Linux and have settled on Ubuntu because I believe it's easy to use, and the Linux community is second to none in its support.

Wayne

---

