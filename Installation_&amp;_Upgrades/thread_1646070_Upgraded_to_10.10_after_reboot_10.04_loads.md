---
title: "Upgraded to 10.10 after reboot 10.04 loads"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by ERobishaw on 2010-12-15
Very strange.

I upgraded 10.04 to 10.10.  At the tail end of the install, the display locked.  After an hour or 2 I rebooted the box.

Came up to a command prompt (instead of starting the GUI automatically), started the GUI, everything seemed fine.  

**Ran 10.10 fine for 2 days.**  Installed apps, got my SVN environment set, started doing development work.

I got a lockup, had to reboot....
**Came back as 10.04.**

I have only one hard drive (/dev/sda), 4 partitions.

My new files all seem to be there, are accessible and valid. Just the OS version has reverted??!?!?!?

**How do I get back to 10.10** (without doing another update, install cycle)?  Surely it's there somewhere...

**Is it a GRUB issue?**
Looking at the grub list, only Ubuntu 10.04 is an option.
Looking at the /boot directory, there are several initrd.img files that are newer than the ones associated with 10.04 in the grub/menu.lst file (i.e., Ubuntu 10.04.1 = initrd...2.6.27, whereas there are other files in the boot directory like 2.6.26, 2.6.31 and 2.6.32)

Confused 
Eric

---

### Post by sikander3786 on 2010-12-15
Welcome to the forums :-)

Instead of guessing here, post the output of bootinfoscript as per instructions here. It might tell us about any on-going problems with Grub and also, which version of Ubuntu is there.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text between the generated code tags.

And it can't be downgraded to an older version. No way. Type in Terminal,

```
lsb_release -a
```

What does it report?

Are there multiple installs on your HDD?

---

### Post by ERobishaw on 2010-12-15
[B]Wow, thanks for the amazingly fast response...
[/B]as you can see below, there isn't even a 2.6.35 kernel on t he system, and yet promise you I was running 10.10 for 2 days, rebooted, and viola, gone. 



**lsb_release -a**
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:    10.04
Codename:    lucid

```

**Results.txt:**
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   150,641,504   150,641,442  83 Linux
/dev/sda2         150,641,505   156,296,384     5,654,880   5 Extended
/dev/sda5         150,641,568   156,296,384     5,654,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b493d1b9-5bdb-4306-9bdc-702b1c7a6464   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        47b884b1-5da8-4208-8a3c-50a279c88222   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


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
timeout        3

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
# kopt=root=UUID=b493d1b9-5bdb-4306-9bdc-702b1c7a6464 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b493d1b9-5bdb-4306-9bdc-702b1c7a6464

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic
uuid        b493d1b9-5bdb-4306-9bdc-702b1c7a6464
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=b493d1b9-5bdb-4306-9bdc-702b1c7a6464 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-26-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic (recovery mode)
uuid        b493d1b9-5bdb-4306-9bdc-702b1c7a6464
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=b493d1b9-5bdb-4306-9bdc-702b1c7a6464 ro  single
initrd        /boot/initrd.img-2.6.32-26-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-15-generic
uuid        b493d1b9-5bdb-4306-9bdc-702b1c7a6464
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=b493d1b9-5bdb-4306-9bdc-702b1c7a6464 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-15-generic (recovery mode)
uuid        b493d1b9-5bdb-4306-9bdc-702b1c7a6464
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=b493d1b9-5bdb-4306-9bdc-702b1c7a6464 ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-16-generic
uuid        b493d1b9-5bdb-4306-9bdc-702b1c7a6464
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b493d1b9-5bdb-4306-9bdc-702b1c7a6464 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid        b493d1b9-5bdb-4306-9bdc-702b1c7a6464
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b493d1b9-5bdb-4306-9bdc-702b1c7a6464 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.27-14-generic
uuid        b493d1b9-5bdb-4306-9bdc-702b1c7a6464
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=b493d1b9-5bdb-4306-9bdc-702b1c7a6464 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.27-14-generic (recovery mode)
uuid        b493d1b9-5bdb-4306-9bdc-702b1c7a6464
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=b493d1b9-5bdb-4306-9bdc-702b1c7a6464 ro  single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.27-7-generic
uuid        b493d1b9-5bdb-4306-9bdc-702b1c7a6464
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b493d1b9-5bdb-4306-9bdc-702b1c7a6464 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.27-7-generic (recovery mode)
uuid        b493d1b9-5bdb-4306-9bdc-702b1c7a6464
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b493d1b9-5bdb-4306-9bdc-702b1c7a6464 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        b493d1b9-5bdb-4306-9bdc-702b1c7a6464
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b493d1b9-5bdb-4306-9bdc-702b1c7a6464 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=47b884b1-5da8-4208-8a3c-50a279c88222 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  45.4GB: boot/grub/menu.lst
  45.4GB: boot/grub/stage2
  45.6GB: boot/initrd.img-2.6.27-14-generic
   4.9GB: boot/initrd.img-2.6.27-7-generic
  45.6GB: boot/initrd.img-2.6.28-16-generic
  45.7GB: boot/initrd.img-2.6.31-15-generic
  45.7GB: boot/initrd.img-2.6.32-26-generic
  45.3GB: boot/vmlinuz-2.6.27-14-generic
  45.4GB: boot/vmlinuz-2.6.27-7-generic
  45.4GB: boot/vmlinuz-2.6.28-16-generic
  45.6GB: boot/vmlinuz-2.6.31-15-generic
  45.7GB: boot/vmlinuz-2.6.32-26-generic
  45.7GB: initrd.img
  45.7GB: initrd.img.old
  45.7GB: vmlinuz
  45.6GB: vmlinuz.old



```

---

### Post by sikander3786 on 2010-12-15
Not strange enough. It is just showing that you've got Ubuntu Lucid 10.04.1 and not the Maverick 10.10.

And Grub Legacy is there giving a hint that it is an upgrade from a previous version. Might sound dumb but are you just sure you were running 10.04 previously and upgraded to 10.10? Or are you missing something that it was 9.10 and upgraded to 10.04?

Or might be you just got regual updates for 10.04 and got upgraded to 10.04.1?

---

### Post by ERobishaw on 2010-12-15
Reasonable questions, but I absolutely positively got to 10.10.  I even installed some software that required 10.10.

I guess I'll go back through the process. Nuts that's strange.

Eric

---

