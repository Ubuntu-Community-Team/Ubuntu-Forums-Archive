---
title: "Dual boot Windows 7 64bit and Ubuntu 10.04 64bit"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by choosemyfate on 2010-07-21
I have been through so many tutorials it's unbelievable..
If anyone could help me with this it would be great.

When I do an **sudo update-grub** Windows 7 does not appear on the boot menu.
I updated to Grub 1.98.
I tried adding it manually using **sudo gedit /etc/grub.d/11_Windows**

I used this tutorial and it did not add the item
[http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)
It didn't even show up in the menu or anything.
It does appear in the /boot/grub/grub.cfg file though.
```

### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows 7&#8243; {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

```Honestly I would really like this to work.
So please help.

Please be descriptive as I am sort of beginner.
I know a lot of basic programming in linux but not much with the install crap.

Thanks,
Matthew

---

### Post by oldfred on 2010-07-21
I have only added entries to 40_custom. But I have seen where you should copy 40_custom to make a new files so perhaps you need the header info?

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

I would think if it is in your grub.cfg it should show unless you have more than one install and are editing the wrong one.

---

### Post by choosemyfate on 2010-07-21
> **oldfred said:**
> I have only added entries to 40_custom. But I have seen where you should copy 40_custom to make a new files so perhaps you need the header info?

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

I would think if it is in your grub.cfg it should show unless you have more than one install and are editing the wrong one.

Can you tell me exactly where in the code I should put that?
Giving you this...

```
#! /bin/sh -e
echo “Adding Windows 7” >&2
cat << EOF
menuentry “Windows 7&#8243; {
set root=(hd0,3)
chainloader +1
}
EOF

```Oh and I found a script to give you some more info.
Hopefully this will help. And once again thank you for replying. 
I do appreciate it.
[B]
More info[/B]

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 274943 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 274943 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   476,375,444   476,375,382  83 Linux
/dev/sda2         476,375,445   488,375,999    12,000,555  82 Linux swap / Solaris
/dev/sda3    *    488,376,320   976,771,071   488,394,752   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        db2bcf60-7823-4707-a674-2b3dd4ed0f1e   ext4                                     
/dev/sda2        734000e3-ad60-4955-a37f-4c4854693cb6   swap                                     
/dev/sda3        7C000C7B000C3EA0                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=db2bcf60-7823-4707-a674-2b3dd4ed0f1e

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

title Windows 7
rootnoverify (hd0,0)
chainloader +2

##title Windows 7
##root (hd0,0)
##makeactive
##chainloader +1


title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

##title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
##uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
##kernel    /boot/vmlinuz-2.6.32-21-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro quiet splash 
##initrd        /boot/initrd.img-2.6.32-21-generic
##quiet

##title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
##uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
##kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro  single
##initrd        /boot/initrd.img-2.6.32-21-generic

##title        Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
##uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
##kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro quiet splash 
##initrd        /boot/initrd.img-2.6.31-20-generic
##quiet

##title        Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
##uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
##kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro  single
##initrd        /boot/initrd.img-2.6.31-20-generic

title        Chainload into GRUB 2
root        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
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
search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry “Windows 7&#8243; {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=734000e3-ad60-4955-a37f-4c4854693cb6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
    .4GB: boot/grub/grub.cfg
  90.4GB: boot/grub/menu.lst
   4.0GB: boot/initrd.img-2.6.31-20-generic
   4.1GB: boot/initrd.img-2.6.32-21-generic
   4.0GB: boot/initrd.img-2.6.32-22-generic
   3.8GB: boot/vmlinuz-2.6.31-20-generic
  23.0GB: boot/vmlinuz-2.6.32-21-generic
   3.0GB: boot/vmlinuz-2.6.32-22-generic
   4.0GB: initrd.img
   4.1GB: initrd.img.old
   3.0GB: vmlinuz
  23.0GB: vmlinuz.old
```

---

### Post by spydeyrch on 2010-07-21
> **choosemyfate said:**
> I have been through so many tutorials it's unbelievable..
If anyone could help me with this it would be great.

When I do an **sudo update-grub** Windows 7 does not appear on the boot menu.


I am asumming that whatyou really mean is:

```

sudo update-grub2

```

If not, then try running that. I have done it several times and it has found it just fine. Ubuntu 10.04 uses the new GRUB2 andnot the legacy GRUB. In all pre-10.04, you would use:

```

sudo update-grub

```

to update grub or edit the menu.list

But now with grub2, you have to use a different command.

But I bet that you already knew that so I will stop my rambling.

-Spydey :KS

---

### Post by choosemyfate on 2010-07-21
> **spydeyrch said:**
> I am asumming that whatyou really mean is:

```

sudo update-grub2

```If not, then try running that. I have done it several times and it has found it just fine. Ubuntu 10.04 uses the new GRUB2 andnot the legacy GRUB. In all pre-10.04, you would use:

```

sudo update-grub

```to update grub or edit the menu.list

But now with grub2, you have to use a different command.

But I bet that you already knew that so I will stop my rambling.

-Spydey :KS

You know what. As silly as that sounds. I haven't done that. lol.
I was just thinking that maybe there was a different command.
But when I was doing the other command it seemed to be updating the right file.
But Imma give it another go.

Thank you so much for replying.

---

### Post by spydeyrch on 2010-07-21
The only thing that I am worried about is that because you have tried a few other options and played around with different files, I am concerned that perhaps it won't work the right way. Lets just cross our fingers and hope that it does. Something that I would do, if possible in your case, is re-install ubuntu. Then right from the get-go, run:

```

sudo update-grub2

```

This will then update your grub menu and add windows 7. I have done is tons-o'-times and it has always worked. ;)

Let us know how it goes. :D

-Spydey :KS

---

### Post by choosemyfate on 2010-07-21
> **spydeyrch said:**
> The only thing that I am worried about is that because you have tried a few other options and played around with different files, I am concerned that perhaps it won't work the right way. Lets just cross our fingers and hope that it does. Something that I would do, if possible in your case, is re-install ubuntu. Then right from the get-go, run:

```

sudo update-grub2

```This will then update your grub menu and add windows 7. I have done is tons-o'-times and it has always worked. ;)

Let us know how it goes. :D

-Spydey :KS

Okay so the update-grub2 is the same function as update-grub.
It updates the grub.cfg file just as the other one does.
I'm trying to avoid reinstalling ubuntu.
Thats the whole reason I installed ubuntu first and then windows 7
And now I can get windows 7 to boot.
So low and behold I get told one thing then have to do things another way.
I feel if I reinstalled ubuntu I would end up where I'm at again for nothing.
It would be much better if I could just figure out this small issue.
I don't even like windows but most games only run in it.

Thanks tho!

---

### Post by spydeyrch on 2010-07-21
> **choosemyfate said:**
> Okay so the update-grub2 is the same function as update-grub.
It updates the grub.cfg file just as the other one does.
I'm trying to avoid reinstalling ubuntu.
Thats the whole reason I installed ubuntu first and then windows 7
And now I can get windows 7 to boot.
So low and behold I get told one thing then have to do things another way.
I feel if I reinstalled ubuntu I would end up where I'm at again for nothing.
It would be much better if I could just figure out this small issue.
I don't even like windows but most games only run in it.

Thanks tho!

Ok, so from what I understand, you installed ubuntu first then windows second. Is that correct?

I don't have much experience fixing grub when the two OS are installed in that order.

Do you have any important files/folders/data in both ubuntu and win7 right now? Have you installed any of your games yet in win7?

We still might be able to get it working but at the least, it will take a reinstall of ubuntu, which really doesn't take that long, like maybe 20 mins. Like I said, I don't have much experience if ubuntu is installed first then windows. So I won't be able to help you too much with the bootscript and other things like that.

What I can tell you is that i have always installed win7 first then ubuntu and it has always worked fine for me, no issues. And I have done it several times on many different machine configs.

Let me know if you would like more detail. :D

-Spydey :KS

P.S. Is it a laptop or a desktop? Multi-HDD system or single HDD with multi partition setup? (I know I could look at the readout of the bootscript but I am lazy right now. Sorry.)

---

### Post by oldfred on 2010-07-21
You have installed grub into the windows boot sector which has essential windows boot info.

Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda3[/COLOR] and

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

It also looks like you deleted the windows 100MB boot/recovery partition as the remaining windows partition does not have all the boot files.

You have this:
/Windows/System32/winload.exe

and should have this:
/bootmgr /Boot/BCD /Windows/System32/winload.exe

I do not think the testdisk will recover these files, but you may have to do that first to get windows to repair it.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by choosemyfate on 2010-07-22
> **oldfred said:**
> You have installed grub into the windows boot sector which has essential windows boot info.

Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda3[/COLOR] and

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

It also looks like you deleted the windows 100MB boot/recovery partition as the remaining windows partition does not have all the boot files.

You have this:
/Windows/System32/winload.exe

and should have this:
/bootmgr /Boot/BCD /Windows/System32/winload.exe

I do not think the testdisk will recover these files, but you may have to do that first to get windows to repair it.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

Thanks so much man.
I'm going to run through all this today and see if I can get it going.
I really appreciate it.
I will let you know my results.

---

