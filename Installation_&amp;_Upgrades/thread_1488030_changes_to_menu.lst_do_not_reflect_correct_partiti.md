---
title: "changes to menu.lst do not reflect correct partition"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by tzjin anthony ks on 2010-05-19
Hi, All.

I have Ubuntu Lucid, but this problem has been around since Feisty for me.

Here's what happens: My menu.lst file has the following line in it:

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
root        (hd0,2)
kernel        /vmlinuz-2.6.32-22-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro quiet splash vga=773 
initrd        /initrd.img-2.6.32-22-generic

Upon any kernel updates, or uninstalling old kernels that I no longer need, the hd(0,2) gets replaced by hd(0,0), which leads to not being able to boot, unless I manually reset the hd(0,0) back to hd(0,2). 

Is there any way around this?

Thanks.

Tzjin.

---

### Post by oldfred on 2010-05-19
Do you have something in sda1, perhaps an old boot partition?

To see entire system:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by drs305 on 2010-05-19
Also take a look at your device map in /boot/grub/device.map and see if it reflects your current setup. If it doesn't, edit it as root to make it reflect the proper setup. If you aren't sure, post it along with the boot info script information requested by *oldfred*.

---

### Post by tzjin anthony ks on 2010-05-19
I do have something on sda1 - it's the restore to factory defaults program. Here's the output in RESULTS.txt:

Thanks.

Tzjin.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Recovery: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 4443680 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2              96,390     4,305,419     4,209,030   b W95 FAT32
/dev/sda3    *      4,305,420     4,707,044       401,625  83 Linux
/dev/sda4           4,707,045   156,296,384   151,589,340   f W95 Ext d (LBA)
/dev/sda5           4,707,108     7,293,509     2,586,402  82 Linux swap / Solaris
/dev/sda6           7,293,573   156,296,384   149,002,812  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-051A                              vfat       DellUtility                   
/dev/sda2        C843-5850                              vfat       OS                            
/dev/sda3        2bf0d924-30c9-4d66-bd46-c8fd32516880   ext3       os_part                       
/dev/sda4: PTTYPE="dos" 
/dev/sda5        b91665c5-cfe7-4de2-a395-0eb9274531c0   swap                                     
/dev/sda6        de57202b-4cfd-4de3-8b3c-92c2267eb10a   ext3       os_part                       
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda3        /boot                    ext3       (rw,relatime)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: initrd.gz
    ??GB: vmlinuz

============================= sda3/grub/menu.lst: =============================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro

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
# defoptions=quiet splash vga=773

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
root        (hd0,2)
kernel        /vmlinuz-2.6.32-22-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro quiet splash vga=773 
initrd        /initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.32-22-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro  single
initrd        /initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
root        (hd0,2)
kernel        /vmlinuz-2.6.32-21-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro quiet splash vga=773 
initrd        /initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.32-21-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro  single
initrd        /initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, memtest86+
root        (hd0,2)
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        kernel /vmlinuz debug boot=dellfactory quiet
        initrd /initrd.gz


=================== sda3: Location of files loaded by Grub: ===================


   2.2GB: grub/menu.lst
   2.2GB: grub/stage2
   2.2GB: initrd.img-2.6.32-21-generic
   2.2GB: initrd.img-2.6.32-22-generic
   2.2GB: vmlinuz-2.6.32-21-generic
   2.2GB: vmlinuz-2.6.32-22-generic

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=b91665c5-cfe7-4de2-a395-0eb9274531c0 none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=2bf0d924-30c9-4d66-bd46-c8fd32516880  /boot ext3 defaults,relatime 0 0

=================== sda6: Location of files loaded by Grub: ===================


   3.8GB: initrd.img
   3.7GB: initrd.img.old
   3.7GB: vmlinuz
   3.7GB: vmlinuz.old

```

---

### Post by oldfred on 2010-05-19
You show no boot loader in the MBR - how do you boot? Do you use a external device? cd, floppy or USB with the boot?

I do not know for sure but then does a windows or lilo boot loader that then looks for the boot flag then load your grub in the sda3 boot partition's boot sector? and your install is in sda6.

This is not a standard install, but it looks like it works. I guess without grub in the MBR and a separate boot partition grub has difficulty finding the correct partition.

Most just have grub in the MBR and no boot partition which makes it a lot simpler and easier to maintain. I do not see why it would give you totally wrong partition information, I would expect either boot or install to be the choices.

---

### Post by tzjin anthony ks on 2010-05-19
This is one of the Dell Ubuntu machines - It's been like this since I bought it.

Care to elaborate on what you said, old fred?

---

### Post by oldfred on 2010-05-19
Then Dell must have some non-standard BIOS. Standard should be that BIOS transfers it loading to the primary master drive (now usually just another BIOS setting) which uses the MBR to continue booting. 

Do you have some special BIOS settings on setting device to boot (boot flag/active partition)? And allowing a partition to directly boot as opposed to the MBR?

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by drs305 on 2010-05-19
You are using 10.04 but apparently are still using Grub legacy. Unless you have had bad experiences with Grub2, unique requirements or it's a Dell thing, I would recommend installing Grub 2. 

You can install Grub2 via the LiveCD. The instructions are located in the G2 community doc. When installing from the CD, make sure you mount your /boot partition to /mnt/boot as mentioned in the instructions so G2 is aware of your configuration.

Here is the link if you are interested in upgrading:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by tzjin anthony ks on 2010-05-19
The BIOS settings don't seem to have anything except the boot order, which, along with CD and USB, has HDD as an option, with no sub-options that can be changed. Perhaps there may be something wrong with the bootscript?

I'd like to switch to G2, but that will have to wait until I hit a couple of slow days - there's w**k to be done on the laptop.

Tzjin.

---

### Post by confused57 on 2010-05-19
You might want to check groot in your menu.lst:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)
```

Be sure to leave the # in front of groot.

---

### Post by tzjin anthony ks on 2010-05-19
hmm.. my groot lines are:

```

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

```

So, in this case, single # does not mean comment, but double # does?

Tzjin.

---

### Post by drs305 on 2010-05-19
> **tzjin anthony ks said:**
> 
So, in this case, single # does not mean comment, but double # does?

Tzjin.

Yes. This is a special case within the "### BEGIN AUTOMAGIC KERNELS LIST" section of menu.lst.  

Think of this entire section as being *defined* by a comment symbol. To add a comment within this section an additional # symbol is required. Thus, a single # is acted upon, while a ## line is a comment.

---

### Post by tzjin anthony ks on 2010-05-19
Interesting. So, it seems like changing the groot command from (0,0) to (0,2) should fix my problem. Just out of curiosity, what will happen if i remove the # before the groot? If nothing, why use a single # at all?

Tzjin.

---

### Post by confused57 on 2010-05-19
Update-grub would not work properly:
[http://members.iinet.net.au/~herman546/p15.html#DEBIAN_AUTOMAGIC_KERNELS_LIST](http://members.iinet.net.au/~herman546/p15.html#DEBIAN_AUTOMAGIC_KERNELS_LIST)

---

### Post by tzjin anthony ks on 2010-05-19
Thanks, y'all.

---

