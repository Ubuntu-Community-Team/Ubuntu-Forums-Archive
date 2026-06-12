---
title: "Upgrade Natty failed after wrong action. HD not found."
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by maria-n on 2011-04-20
Hi,

I decided to upgrade to Natty, so far never had any problems when upgrading (since Dapper). I left my PC though, during install, as no one ever touches mine, however hubby found this the perfect occasion to use it this time, ignored the upgrade-messages and opened Chrome, with all its twenty tabs. 

When I returned, Chrome had no control-buttons, closed it from task-bar, which prompted the PC to restart, giving a few error-messages and ending with HD not found, skip or restore manually...and this situations pertains.

I would rather not lose the contents of my drive, so I'd be happy to learn how to restore the drive!

Thanks beforehand for any help!


After searching a few other threads, I've obtained the boot info summary:



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
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
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   390,716,864   390,716,802  83 Linux
/dev/sda2         390,716,865   398,524,454     7,807,590  82 Linux swap / Solaris
/dev/sda3         398,524,455   476,664,614    78,140,160  83 Linux
/dev/sda4         476,664,615   625,137,344   148,472,730   5 Extended
/dev/sda5         476,664,678   625,137,344   148,472,667  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        993c35e2-4bd9-47b0-99db-b99c499f8552   ext3                                     
/dev/sda2        19b31595-80c1-4658-955c-be4dde529561   swap                                     
/dev/sda3        4fa01a56-a763-46e3-8b54-c4c2e47a9e68   ext3                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        1abdbd70-cb7e-4083-bb90-9579d418d408   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
# kopt=root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro

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

title        Ubuntu 10.10, kernel 2.6.35-28-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-28-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro  single
initrd        /boot/initrd.img-2.6.35-28-generic

title        Ubuntu 10.10, kernel 2.6.35-27-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-27-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-27-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-27-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro  single
initrd        /boot/initrd.img-2.6.35-27-generic

title        Ubuntu 10.10, kernel 2.6.35-26-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-26-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-26-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-26-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-26-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro  single
initrd        /boot/initrd.img-2.6.35-26-generic

title        Ubuntu 10.10, kernel 2.6.35-25-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-25-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro  single
initrd        /boot/initrd.img-2.6.35-25-generic

title        Ubuntu 10.10, kernel 2.6.35-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-24-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro  single
initrd        /boot/initrd.img-2.6.35-24-generic

title        Ubuntu 10.10, kernel 2.6.35-23-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-23-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-23-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-23-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro  single
initrd        /boot/initrd.img-2.6.35-23-generic

title        Ubuntu 10.10, kernel 2.6.32-25-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic
quiet

title        Ubuntu 10.10, kernel 2.6.32-25-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.10, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 10.10, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro  single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 10.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=4fa01a56-a763-46e3-8b54-c4c2e47a9e68 /usr            ext3    relatime        0       2
# /dev/sda2
UUID=19b31595-80c1-4658-955c-be4dde529561 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 138.0GB: boot/grub/menu.lst
 137.8GB: boot/grub/stage2
 137.9GB: boot/initrd.img-2.6.24-16-generic
 137.8GB: boot/initrd.img-2.6.24-16-generic.bak
 137.9GB: boot/initrd.img-2.6.32-25-generic
 137.9GB: boot/initrd.img-2.6.35-23-generic
 137.9GB: boot/initrd.img-2.6.35-24-generic
 137.9GB: boot/initrd.img-2.6.35-25-generic
 137.9GB: boot/initrd.img-2.6.35-26-generic
 137.8GB: boot/initrd.img-2.6.35-27-generic
 138.0GB: boot/initrd.img-2.6.35-28-generic
 137.8GB: boot/vmlinuz-2.6.24-16-generic
 137.9GB: boot/vmlinuz-2.6.32-25-generic
 137.9GB: boot/vmlinuz-2.6.35-23-generic
 137.9GB: boot/vmlinuz-2.6.35-24-generic
 137.8GB: boot/vmlinuz-2.6.35-25-generic
 137.9GB: boot/vmlinuz-2.6.35-26-generic
 137.9GB: boot/vmlinuz-2.6.35-27-generic
 138.0GB: boot/vmlinuz-2.6.35-28-generic
 137.8GB: boot/vmlinuz-2.6.38-8-generic
 138.0GB: initrd.img
 137.8GB: initrd.img.old
 138.0GB: vmlinuz
 137.9GB: vmlinuz.old
```

---

### Post by mörgæs on 2011-04-20
If this machine has been upgraded since Dapper, it indeed deserves a fresh install... 

Can you see your hard drive if booting with a live CD?

---

### Post by maria-n on 2011-04-20
Haha, no that's not the case, just meant to say that I'm not entirely new to the process. 

I think this one had a new install when Jaunty or Karmic were released.


Yes, the hard drive is visible.

---

### Post by Mark Phelps on 2011-04-20
Didn't like the Natty beta when I tried it, but from what I've read, it's the buggiest beta in a long time.  This, plus the unfortunate fact that Ubuntu STILL does not have a version roll-back capability built in, should tell folks to AVOID upgrading to beta versions ....

But having done that, since the upgrade got borked mid-stream, you may have no recourse now other than a complete reinstall -- especially if you were running Jaunty or Karmic (not Maveric).

Sorry ...

---

### Post by maria-n on 2011-04-20
I believe the install would largely have been completed when he went to Chrome - he opened Chrome in Natty, so it was that far that that was possible, but I could see some messages open in the task-bar which he ignored, perhaps for another restart or so.



The upgrade was from Maverick.

---

### Post by bapoumba on 2011-04-20
What does your sources.list look like ?
```
cat /etc/apt/sources.list
```

Did you have ppa or third party repos activated ?

---

### Post by maria-n on 2011-04-20
I now have only the sources list of the live-dvd I'm using, I don't think you mean that though?

Can I still get the sources of my hd, in spite that when I boot it's not being found? 

I think I was having third party enabled because of the NVidia driver, but if I remember well, that was disabled in the start of the upgrade-process (with my consent)

---

### Post by bapoumba on 2011-04-20
Hmm, I should not answer when I'm reading several threads at a time..
Of course, if it does not find your drive, fixing is going to be quite difficult from the live cd or dvd.

If what you posted reflects the actual drive, sda1 is bootable and you have no separate /home partition.

Whatever you decide, you should back up everything personal (that means your /home and maybe what you placed in /usr), because reinstalling from a dvd is going to write over your files. That may be an opportunity to set up a separate /home and maybe an additional partition for other stuff (I place music and work files in different partitions).
Are sda4 and 5 your windows partitions ?

---

### Post by maria-n on 2011-04-20
Thanks for the replies so far!

sda 4 and 5 are not for win, but were meant for experimenting with other Linux-distro's (though I am lazy ;) )

From the live-dvd I can see all my old files on my HD, so I should be able to preserve them indeed.

But how do I make sda1 bootable again? If there is a nice thread with clear instructions, I could work from there...

---

### Post by bapoumba on 2011-04-20
sda is bootable. I'm not sure your natty install is usable at all. If you can wait for someone else to give input or another advice, that would be better.
So backup anything that you cannot afford to loose.
Maybe one of these extra partition could be your future /home :)

---

### Post by ezsit on 2011-04-20
Looks like your grub menu.1st file does not have a boot stanza for this kernel: 137.8GB: boot/vmlinuz-2.6.38-8-generic. Under the boot stanzas, your latest one is:

title        Ubuntu 10.10, kernel 2.6.35-28-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-28-generic
quiet

I wonder if adding these stanzas to the top of the list:

title        Ubuntu 11.04, kernel 2.6.38-8-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro quiet splash 
initrd        /boot/initrd.img-2.6.38-8-generic
quiet

title        Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=993c35e2-4bd9-47b0-99db-b99c499f8552 ro  single
initrd        /boot/initrd.img-2.6.38-8-generic

would do the trick. I do not know enough about grub2 to know if that is the proper way to fix the problem. You may need to wait for someone else.

---

### Post by mörgæs on 2011-04-20
I believe so much is uncertain about the system that the best solution is a fresh install, also if is has 'only' been running from 9.04 or 9.10. It takes one hour, and you know for sure that it will solve the problem.

Trying to troubleshoot takes... well, you tell me :-)

---

### Post by maria-n on 2011-04-22
Thanks again for the replies!

Looks indeed wise to save the important files and do a fresh install, as I would do that in any case about every two years.

It would have been interesting to try and save the old one and add something to the boot files like mentioned above, but I guess it's not worth the trouble and probably above my level anyway ;)

---

