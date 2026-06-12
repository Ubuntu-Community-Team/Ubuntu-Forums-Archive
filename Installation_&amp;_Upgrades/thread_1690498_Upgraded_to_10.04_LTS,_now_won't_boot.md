---
title: "Upgraded to 10.04 LTS, now won't boot"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by elementzero on 2011-02-18
So I was on 8.04, and I decided to hit the upgrade button on the gui to  upgrade to 10.04.  Well the upgrade went fine and all...until I  rebooted.  Now I get this

--------------------------------------------------------------------
Starting up ...
mount: mounting none on /dev failed: No such device
udevd[984]: error getting socket: Invalid argument

error initializing netlink socket
udevd[984]: error initializing netlink socket

libudev: udev_monitor_new_from_netlink: error getting socket: Invalid argument
Segmentation fault
There appears to be one or more degraded LVM volumes, and your root  device may depend on the LVM volumes being online.  One or more of the  following LVM volumes are degraded:
read_urandom: /dev/urandom: open failed: No such file or directory
Gave up waiting for root deive.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda1 does not exist.  Dropping to a shell!

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
----------------------------------------------

FYI if I do ls /dev I get this

console     pts     tty2     tty4     tty6
null           tty1    tty3    tty5  

I found some other posts and tried adding the rootdelay=35 and acpi=off  but those did not fix it.  This is a virtual machine running on VMWare  ESXi 4.1 if that helps.

Anybody have any ideas as to what to do next?

---

### Post by sikander3786 on 2011-02-18
Welcome to the forums :-)

Seems like there is LVM setup.

Anyhow, please boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would give us a better overview of your current system and thus help us advise more efficiently.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readibility purposes.

---

### Post by elementzero on 2011-02-18
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
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

Disk /dev/sda: 123.0 GB, 122951485440 bytes
255 heads, 63 sectors/track, 14948 cylinders, total 240139620 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x408aef50

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,050,984   234,050,922  83 Linux
/dev/sda2         234,050,985   240,107,489     6,056,505   5 Extended
/dev/sda5         234,051,048   240,107,489     6,056,442  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0c35525b-97bc-4a8f-87c9-d41a8a82b2b6   ext3                                     
/dev/sda5                                               swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
# kopt=root=UUID=433f9167-11ee-4927-978b-626ff3a0acb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 8.04, kernel 2.6.24-18-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-18-generic root=/dev/sda1 ro quiet splash
initrd        /boot/initrd.img-2.6.24-18-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-18-generic root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.24-18-generic

# (removed by Converter) title        Ubuntu 8.04, kernel 2.6.24-16-generic
# (removed by Converter) root        (hd0,0)
# (removed by Converter) kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=433f9167-11ee-4927-978b-626ff3a0acb3 ro quiet splash
# (removed by Converter) initrd        /boot/initrd.img-2.6.24-16-generic
# (removed by Converter) quiet
# (removed by Converter) 
# (removed by Converter) title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
# (removed by Converter) root        (hd0,0)
# (removed by Converter) kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=433f9167-11ee-4927-978b-626ff3a0acb3 ro single
# (removed by Converter) initrd        /boot/initrd.img-2.6.24-16-generic
# (removed by Converter) 
# (removed by Converter) title        Ubuntu 8.04, memtest86+
# (removed by Converter) root        (hd0,0)
# (removed by Converter) kernel        /boot/memtest86+.bin
# (removed by Converter) quiet
# (removed by Converter) 
### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdg1
/dev/sda1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hdg5
/dev/sda5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  97.0GB: boot/grub/menu.lst
  97.1GB: boot/grub/stage2
  97.1GB: boot/initrd.img-2.6.24-18-generic
  97.1GB: boot/initrd.img-2.6.24-18-generic.bak
  97.1GB: boot/initrd.img-2.6.24-18-generic.old.0
  97.1GB: boot/initrd.img-2.6.32-28-generic
  97.1GB: boot/vmlinuz-2.6.24-18-generic
  97.1GB: boot/vmlinuz-2.6.32-28-generic
  97.1GB: initrd.img
  97.1GB: initrd.img.old
  97.1GB: vmlinuz
  97.1GB: vmlinuz.old


```

---

### Post by sikander3786 on 2011-02-18
So you are using Grub Legacy (default for 8.04) and I'm not much experience with that. I have requested some senior members to take a look at your problem. Please hang in there.

---

### Post by elementzero on 2011-02-22
bump

---

### Post by drs305 on 2011-02-22
I've forgotten a lot about Grub legacy and I have never used LVM, but perhaps this input will be helpful.

You say the upgrade to 10.04 went ok, but when I look at the menu.lst the only two entries appear to refer to 8.04. 

If you can get to the Grub menu during boot, press ESC to halt the boot and then "e" to edit the menuentry.

Highlight the first menu entry, press "e" and select the "kernel" line and then press "e" again to edit that line. Change the reference to "2.6.24-16-generic" to "2.6.32-28-generic".
Once you have made the change, ENTER and repeat with the *initrd* line.

Press "b" to boot and see if this helps. It won't solve any LVM issue but it should at least try to boot the 10.04 kernel. It's about the only thing I can recommend with my limited knowledge of your specific situation.

---

### Post by elementzero on 2011-02-22
I thought that might be the case too, but it seems that the bigger problem is that the machine doesn't seem to see my hard drive at all.  I tried changing the grub file like you said but when I hit b to run it all I get ir 

> 
Error 15: File not found


I ran the live cd and mounted the drive and all the files are intact, so I know the drive is not dead, just dunno how to get this thing to boot now.

---

### Post by drs305 on 2011-02-22
Since you were using 8.04, Grub apparently doesn't see the files but you can once you have booted into an OS, I suspect it's a BIOS limitation.

There is a decent chance your BIOS is older and can only see the first 37GB (or less) of the drive. If you can enter BIOS during boot, check the reported drive size. If it's less than 97GB your BIOS can't see your Grub files.  Note: Once the system is booted (or via LiveCD), the OS can handle the larger disks and your files are 'seen'.

If you want to keep your current installation, your options are to enable large disks via a BIOS setting (see if there is LBA setting), upgrade the BIOS (best bet) or create a separate boot partition within the initial limits of the BIOS (or a separate flash drive which would need to be inserted during each boot).

---

### Post by elementzero on 2011-02-22
This is running on VMWare Hardware Version 7.   There is an option in the BIOS for larger disks, but this has already been set to 'Other' (I tried DOS, didn't work either).   There isn't really a BIOS I can update it to since it's a virtual BIOS and Hardware Version 7 is the latest.

---

### Post by elementzero on 2011-02-22
If the grub is the reason this is occuring, should I attempt to replace it doing something liek this?

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by drs305 on 2011-02-22
I wrote that guide and purging/reinstalling Grub2 solves a lot of problems. 

If you can't boot into your normal installation the purge/replace has to be accomplished via a LiveCD. I don't know how you do that in VMware.

If you can figure out how to run the purge/install commands in VMWare, you would purge grub-common (and grub) and install grub-pc (and grub-common).  *grub-pc* is Grub2.

I would expect the menus created by Grub2 would be more robust and reliable than Grub legacy but don't know if it would solve your issue or not.

---

### Post by elementzero on 2011-02-23
Ok, yeah I know how to run the LiveCD in VMWare (had to do it in order to do that boot script earlier int he thread).

I'll go ahead and purge the old grub and install the grub2 and we'll see how that goes.

---

### Post by elementzero on 2011-02-23
Alright that fixed it.  The system boots up fine now (although the keyboard didn't work at first, but I guess that's a different issue [http://communities.vmware.com/thread/261454](http://communities.vmware.com/thread/261454)).

Thanks for the help, and that grub updating guide is awesome btw :)

---

