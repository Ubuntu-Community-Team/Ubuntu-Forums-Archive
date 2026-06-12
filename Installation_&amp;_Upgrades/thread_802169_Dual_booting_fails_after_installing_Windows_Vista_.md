---
title: "Dual booting fails after installing Windows Vista Updates"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by jbullfrog on 2008-05-21
I cannot dual boot Vista and Ubuntu successfully.  Here is what I did.

1.  Completely erased all my partitions on my Dell 1400 laptop, so that all I had was unformatted space.

2. Created two 30 GB ntfs primary partions.

2.  Use my backup DVD with Vista Operating System and reinstalled Vista on the first 30 GB ntfs primary partition.  

(The second 30 GB ntfs primary parition was created as a drive that I could read and write to from both windows and ubuntu)

3.  Loaded up a cd with Ubuntu 8.04 Hardy Heron.

4.  Manually partitioned: 

created an extended partition
made a 10 GB root "/" ext3 partition
made a 38 GB "/ home" ext3 partition
made a 2 GB swap partition

5. Restarted the computer and booted Vista

6. Used Windows Update to download and install 55 updates.

7. Clicked Restart on the dialog window that appears after installing updates.

8. Got to the GRUB loader and selected Vista.

9. Vista started loading normally, but I never got to the splash screen where the Vista Pearl Icon appears.  Instead, a blue screen with small white font pops up for 1 second and the computer reboots back to the GRUB screen.

I am extremely lost and confused!  I have  installing Linux first, but after updating Windows Vista, the exact same problem occurs.  

Any one have any idea of what happened, and how I can solve it?

---

### Post by zvacet on 2008-05-21
```
sudo fdisk -l
``` 

```
cat /boot/grub.menu.lst
```

Post them here.

---

### Post by jbullfrog on 2008-05-21
When I installed the updates labeled "Important", I was still able to boot up no problem.

It was Only when I installed the 19 additional updates that I got that weird blue screen and the failure of Vista to load up.

---

### Post by jbullfrog on 2008-05-21
Here are the results

1) sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c19b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917        7832    31455270    7  HPFS/NTFS
/dev/sda3            7833       14593    54307732+   5  Extended
/dev/sda5            7833        9077    10000431   83  Linux
/dev/sda6            9078       14344    42307146   83  Linux
/dev/sda7           14345       14593     2000061   82  Linux swap / Solaris

2) cat /boot/grub.menu.lst 

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
# kopt=root=UUID=af7faad2-6b89-4e15-9cc0-b4b17865ea39 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=af7faad2-6b89-4e15-9cc0-b4b17865ea39 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=af7faad2-6b89-4e15-9cc0-b4b17865ea39 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by zvacet on 2008-05-21
You can replace you windows entries with 

title Windows Vista/Longhorn
rootnoverify   (hd0,0)
chainloader +1


save file and close it.After reboot you should be fine.If not look at [this]("http://users.bigpond.net.au/hermanzone/p15.htm") page for help,or wait for some expirienced user to help you.

---

### Post by jbullfrog on 2008-05-21
I got it to work!  Thanks so much.  [http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)
:popcorn:

---

