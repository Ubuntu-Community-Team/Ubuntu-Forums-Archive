---
title: "Debian doesn't boot while Ubuntu does?"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by Laxman_prodigy on 2010-03-20
Hi.

I have Ubuntu Karmic Koala installed and there was never ever such an issue. I was interested in trying Debian lenny and installed it today through netinstall.

Now, Debian lenny is the only OS I have installed in.

It says on booting, "No bootable device found - insert and press any key".

My board is Intel DP35DP. 

What should I do?:confused:

---

### Post by coffeecat on 2010-03-20
> **Laxman_prodigy said:**
> It says on booting, "No bootable device found - insert and press any key".

That sounds like a BIOS message. Did you install grub when you installed Debian? If there's no bootloader the BIOS won't be able to find a bootable device.

Alternatively, check the two cables to the hard drive. This could be a hardware problem.

---

### Post by Laxman_prodigy on 2010-03-20
> **coffeecat said:**
> That sounds like a BIOS message. Did you install grub when you installed Debian? If there's no bootloader the BIOS won't be able to find a bootable device.

Alternatively, check the two cables to the hard drive. This could be a hardware problem.


I did the netinstall and I think I saw something like "Installing Grub".

I have a live cd of sidux and working internet now. 

What should I do to know if Grub is not installed?

---

### Post by coffeecat on 2010-03-20
There are two things that "installing grub" might have referred to: that's installing the actual packages just as with any other app, and then installing grub to the mbr and configuring the config menu. Also, you need to know which version of grub Debian Lenny is using, grub legacy or grub2, although I should imagine it would be legacy grub.

With a live CD, have a look in /boot in the hard disc installation. Is there a /grub folder there? If there is, have a look in it. Is there a file called menu.lst or one called grub.conf? The legacy grub config file is usually called menu.lst, but some distros use grub.conf (as distinct from grub2's grub.cfg). Also, are there files called stage* - something or other?

While you're in a live CD session, open up a terminal and do:

```
sudo fdisk -l
```... just to make sure the hard drive hasn't got disconnected or otherwise disappeared. (That's fdisk lower-case L.)

---

### Post by Laxman_prodigy on 2010-03-20
> **coffeecat said:**
> There are two things that "installing grub" might have referred to: that's installing the actual packages just as with any other app, and then installing grub to the mbr and configuring the config menu. Also, you need to know which version of grub Debian Lenny is using, grub legacy or grub2, although I should imagine it would be legacy grub.

With a live CD, have a look in /boot in the hard disc installation. Is there a /grub folder there? If there is, have a look in it. Is there a file called menu.lst or one called grub.conf? The legacy grub config file is usually called menu.lst, but some distros use grub.conf (as distinct from grub2's grub.cfg). Also, are there files called stage* - something or other?

While you're in a live CD session, open up a terminal and do:

```
sudo fdisk -l
```... just to make sure the hard drive hasn't got disconnected or otherwise disappeared. (That's fdisk lower-case L.)

Thank you coffeecat.

Yes, there is /grub folder. Also, it has menu.lst. There are many files for eg. stage 1, stage 2 and other various files having someway or other that "stage" in them.

Here is the output of that command:
sidux@sidux:~$ sudo fdisk -l

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04c204c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3647    29294496   83  Linux
/dev/sda2            3648        4255     4883760   82  Linux swap / Solaris
/dev/sda3            4256       43777   317460465   83  Linux

---

### Post by Laxman_prodigy on 2010-03-20
But, it didn't asked me whether to install grub2 or legacy. Only that "No other operating system detected. So it is safe to install grub to MBR or something."

---

### Post by coffeecat on 2010-03-20
> **Laxman_prodigy said:**
> But, it didn't asked me whether to install grub2 or legacy. Only that "No other operating system detected. So it is safe to install grub to MBR or something."

Yes - it won't do any harm. It's possible installing grub to the mbr failed for some reason. You should be able to reinstall grub using the Sidux disc. Do you need any help? Which is your Debian root partition, sda1 or sda3? Also, check whether menu.lst is empty or has some entries in it. If it's empty, or just has commented lines, it will be necessary to run 'update-grub' to regenerate it.

---

### Post by Laxman_prodigy on 2010-03-20
> **coffeecat said:**
> Yes - it won't do any harm. It's possible installing grub to the mbr failed for some reason. You should be able to reinstall grub using the Sidux disc. Do you need any help? Which is your Debian root partition, sda1 or sda3? Also, check whether menu.lst is empty or has some entries in it. If it's empty, or just has commented lines, it will be necessary to run 'update-grub' to regenerate it.

Thank you for the support. Yes, please help me installing grub or reinstalling it. I need to get debian working.

The root partition is sda1. 

**Here is what is in the menu.lst:** 

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda1 ro

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.26-2-amd64
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sda1 ro quiet
initrd        /boot/initrd.img-2.6.26-2-amd64

title        Debian GNU/Linux, kernel 2.6.26-2-amd64 (single-user mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.26-2-amd64

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Laxman_prodigy on 2010-03-20
Sorry for those smileys. I didn't put it there.

---

### Post by Laxman_prodigy on 2010-03-20
Coffeecat, are you there? 

I'm sorry but I have grown into impatience.

---

### Post by oldfred on 2010-03-20
For some reason it likes to convert eights to smileys. You can use the code tag (#) to wrap code tags around code and it will be ok.

If you want to see what did get installed in the MBR and what else is where this documents the entire boot configuration. I use it myself when changing things to keep track of where everything is.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by Laxman_prodigy on 2010-03-20
> **oldfred said:**
> For some reason it likes to convert eights to smileys. You can use the code tag (#) to wrap code tags around code and it will be ok.

If you want to see what did get installed in the MBR and what else is where this documents the entire boot configuration. I use it myself when changing things to keep track of where everything is.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

Thank you Oldfred.

Here is the output:
```
============================ Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04c204c1

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    58,589,054    58,588,992  83 Linux
/dev/sda2          58,589,055    68,356,574     9,767,520  82 Linux swap / Solaris
/dev/sda3          68,356,575   703,277,504   634,920,930  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e75aff86-2271-468e-8e0e-05653c4ba994   ext3                                     
/dev/sda2                                               swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /fll/sr0                 iso9660    (ro,relatime)
/dev/loop0       /fll/sidux               squashfs   (ro,relatime)
/dev/sda1        /media/disk1part1        ext3       (rw,nosuid,nodev,noatime)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda1 ro

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.26-2-amd64
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sda1 ro quiet
initrd        /boot/initrd.img-2.6.26-2-amd64

title        Debian GNU/Linux, kernel 2.6.26-2-amd64 (single-user mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.26-2-amd64

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda1: Location of files loaded by Grub: ===================


    .3GB: boot/grub/menu.lst
    .3GB: boot/grub/stage2
    .3GB: boot/initrd.img-2.6.26-2-amd64
    .3GB: boot/initrd.img-2.6.26-2-amd64.bak
    .3GB: boot/vmlinuz-2.6.26-2-amd64
    .3GB: initrd.img
    .3GB: vmlinuz
============================ Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04c204c1

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    58,589,054    58,588,992  83 Linux
/dev/sda2          58,589,055    68,356,574     9,767,520  82 Linux swap / Solaris
/dev/sda3          68,356,575   703,277,504   634,920,930  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e75aff86-2271-468e-8e0e-05653c4ba994   ext3                                     
/dev/sda2                                               swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /fll/sr0                 iso9660    (ro,relatime)
/dev/loop0       /fll/sidux               squashfs   (ro,relatime)
/dev/sda1        /media/disk1part1        ext3       (rw,nosuid,nodev,noatime)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda1 ro

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.26-2-amd64
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sda1 ro quiet
initrd        /boot/initrd.img-2.6.26-2-amd64

title        Debian GNU/Linux, kernel 2.6.26-2-amd64 (single-user mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.26-2-amd64

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda1: Location of files loaded by Grub: ===================


    .3GB: boot/grub/menu.lst
    .3GB: boot/grub/stage2
    .3GB: boot/initrd.img-2.6.26-2-amd64
    .3GB: boot/initrd.img-2.6.26-2-amd64.bak
    .3GB: boot/vmlinuz-2.6.26-2-amd64
    .3GB: initrd.img
    .3GB: vmlinuz
============================ Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04c204c1

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    58,589,054    58,588,992  83 Linux
/dev/sda2          58,589,055    68,356,574     9,767,520  82 Linux swap / Solaris
/dev/sda3          68,356,575   703,277,504   634,920,930  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e75aff86-2271-468e-8e0e-05653c4ba994   ext3                                     
/dev/sda2                                               swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /fll/sr0                 iso9660    (ro,relatime)
/dev/loop0       /fll/sidux               squashfs   (ro,relatime)
/dev/sda1        /media/disk1part1        ext3       (rw,nosuid,nodev,noatime)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda1 ro

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.26-2-amd64
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sda1 ro quiet
initrd        /boot/initrd.img-2.6.26-2-amd64

title        Debian GNU/Linux, kernel 2.6.26-2-amd64 (single-user mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.26-2-amd64

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda1: Location of files loaded by Grub: ===================


    .3GB: boot/grub/menu.lst
    .3GB: boot/grub/stage2
    .3GB: boot/initrd.img-2.6.26-2-amd64
    .3GB: boot/initrd.img-2.6.26-2-amd64.bak
    .3GB: boot/vmlinuz-2.6.26-2-amd64
    .3GB: initrd.img
    .3GB: vmlinuz
============================ Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04c204c1

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    58,589,054    58,588,992  83 Linux
/dev/sda2          58,589,055    68,356,574     9,767,520  82 Linux swap / Solaris
/dev/sda3          68,356,575   703,277,504   634,920,930  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e75aff86-2271-468e-8e0e-05653c4ba994   ext3                                     
/dev/sda2                                               swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /fll/sr0                 iso9660    (ro,relatime)
/dev/loop0       /fll/sidux               squashfs   (ro,relatime)
/dev/sda1        /media/disk1part1        ext3       (rw,nosuid,nodev,noatime)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda1 ro

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.26-2-amd64
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sda1 ro quiet
initrd        /boot/initrd.img-2.6.26-2-amd64

title        Debian GNU/Linux, kernel 2.6.26-2-amd64 (single-user mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.26-2-amd64 root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.26-2-amd64

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda1: Location of files loaded by Grub: ===================


    .3GB: boot/grub/menu.lst
    .3GB: boot/grub/stage2
    .3GB: boot/initrd.img-2.6.26-2-amd64
    .3GB: boot/initrd.img-2.6.26-2-amd64.bak
    .3GB: boot/vmlinuz-2.6.26-2-amd64
    .3GB: initrd.img
    .3GB: vmlinuz

```

---

### Post by Laxman_prodigy on 2010-03-20
@ Oldfred

Did I do right?

---

### Post by oldfred on 2010-03-20
I do not see anything particularly wrong. I did recently learn that some BIOS require a boot flag. Window has to have a boot flag and linux does not use it. I would put a boot flag on your sda1 to see it that solves the problem. You only can/should have one boot flag set per drive.

You can do it from gparted, disk utility or command line - but I am not sure if command line works from liveCD without having to chroot into system, so I would use gparted.

---

### Post by Laxman_prodigy on 2010-03-20
> **oldfred said:**
> I do not see anything particularly wrong. I did recently learn that some BIOS require a boot flag. Window has to have a boot flag and linux does not use it. I would put a boot flag on your sda1 to see it that solves the problem. You only can/should have one boot flag set per drive.

You can do it from gparted, disk utility or command line - but I am not sure if command line works from liveCD without having to chroot into system, so I would use gparted.

I have gparted in this Sidux Live CD but I have never used it. Also, I don't know about flag.

Please guide me.

---

### Post by coffeecat on 2010-03-20
I've been out doing other errands. I didn't abandon the thread. :wink:

Like oldfred, I can't see anything wrong. Your menu.lst looks just fine and the boot script says that grub is correctly installed to the mbr looking for stage 2 and menu.lst on sda1. Everything as it should be. You could try setting the boot flag, but neither grub nor Linux needs a boot flag. Fwiw, in Gparted (at least in the Ubuntu Karmic version of gparted), highlight the partition you want to set the boot flag for (sda1), then Partition > Manage Flags. Tick the boot flag box and then on the close button. You don't have to click on 'apply'.

---

### Post by Laxman_prodigy on 2010-03-20
> **coffeecat said:**
> I've been out doing other errands. I didn't abandon the thread. :wink:

Like oldfred, I can't see anything wrong. Your menu.lst looks just fine and the boot script says that grub is correctly installed to the mbr looking for stage 2 and menu.lst on sda1. Everything as it should be. You could try setting the boot flag, but neither grub nor Linux needs a boot flag. Fwiw, in Gparted (at least in the Ubuntu Karmic version of gparted), highlight the partition you want to set the boot flag for (sda1), then Partition > Manage Flags. Tick the boot flag box and then on the close button. You don't have to click on 'apply'.


Oh thank you coffeecat. That just solved it.

I was just itching to ask if that is normal. Why didn't it start of its own? Any ideas?

---

### Post by coffeecat on 2010-03-20
> **Laxman_prodigy said:**
> Oh thank you coffeecat. That just solved it.

I was just itching to ask if that is normal. Why didn't it start of its own? Any ideas?

Curious. I have no idea why that solved it. I have never used a boot flag on a Linux partition - usually because the Windows partition needs the boot flag and, as oldfred points out, you can only have one boot flag per drive.

It may be that the problem was somewhere else - perhaps a hardware issue as I suggested in my first post. If it was a loose cable you need to beware of this happening again. Unless oldfred has any better ideas.

Whatever - I'm glad it's working.

---

### Post by oldfred on 2010-03-20
I found out from one of meierfra's posts about the boot flag and have seen where some intel boards have that in their BIOS. Even though linux does not use it, the BIOS knows that windows needs a boot flag and does not allow booting even if there is no windows. It should be a bug in the BIOS but I am sure they say it is a feature.

---

### Post by Laxman_prodigy on 2010-03-20
@OldFred

"Thank you too."

---

