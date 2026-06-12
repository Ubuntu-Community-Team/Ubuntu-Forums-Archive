---
title: "Ubuntu won't boot"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by Dream. on 2008-08-27
I can tripple boot xp/vista/ubuntu but when I try and boot into ubuntu I get a msg saying that I can't boot from the hard disk, and to insert system disk.

Can someone please help!

Edit: It was all working fine

---

### Post by sandysandy on 2008-08-27
from ubuntu live CD terminal post output of [COLOR="Blue"]

sudo fdisk -lu
[/COLOR]
and [COLOR="Blue"]cat /boot/grub/menu.lst[/COLOR]

how many hard disk are there, RAM size. when did the problem occur - after installation of which OS, give sequence of installing triple boot.
regards

---

### Post by Dream. on 2008-08-28
Here's my output...

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes 

Device Boot                Start         End      Blocks   Id  
System
/dev/sda1   *          63    78140159    39070048+   7  HPFS/NTFS


Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes  

Device Boot                Start         End      Blocks   Id  
System
/dev/sdb1              63    77063804    38531871   83  
Linux
/dev/sdb2         77063805    78156224      546210   82  Linux swap / Solaris


Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes   

Device Boot                   Start         End      Blocks   Id  
System
/dev/sdc1                 63   225777509   112888723+   7  
HPFS/NTFS
/dev/sdc2       225777510   451057004   112639747+   7  
HPFS/NTFS
/dev/sdc3       451057005   539125334    44034165    7  
HPFS/NTFS
/dev/sdc4       539125335   625137344    43006005   83  


Linux

ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

3 HDD's
1024MB RAM
Installed XP, then ubuntu, then installed vista.
All worked fine until I tried to boot into ubuntu the other day.

Thanks.

---

### Post by Dream. on 2008-08-31
anyone?

---

### Post by vishalrao on 2008-08-31
i think you should have installed ubuntu last :)

but try the steps in this link and see if they help?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

or you might just need to reinstall ubuntu...

---

### Post by sandysandy on 2008-08-31
> **Dream. said:**
> anyone? Installed XP, then ubuntu, then installed vista.
All worked fine until I tried to boot into ubuntu the other day.


what is ur bootmanager. is it GRUB. if so did u install GRUB after VISTA install, as vista would have erased GRUB from MBR and put its own bootloader in place of GRUB.

go thru these these threads carefully:)

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

regards

---

### Post by caljohnsmith on 2008-09-01
So when you start up your computer, do you get the Grub menu or a Vista boot menu? If you want to use Grub, Grub can easily boot XP, Vista, and Ubuntu. If you want to use Vista's boot manager, you can get a program like EasyBCD to help configure its boot menu. I would recommend Grub though. If you decide to go with Grub, boot up your Live CD again and do the following so we can see your menu.lst:
```
sudo mount /dev/sdb1 /mnt
cat /mnt/boot/grub/menu.lst
```

---

### Post by Dream. on 2008-09-02
I get the vista boot menu, I used Easy BCD to edit the vista boot menu, so I get the option of booting into XP, Vista or Ubuntu.

It all worked fine for many months.

Here is my output...

ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
#      password --md5 $1$oMAS23U0/$aU2WJ96JGP7GJ3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=94aeb599-d4f5-404a-90ef-ea2015620908 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=94aeb599-d4f5-404a-90ef-ea2015620908 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=94aeb599-d4f5-404a-90ef-ea2015620908 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by caljohnsmith on 2008-09-02
So which do you want to use for your overall boot manager--Grub or Vista? If you go with Vista you'll have to figure out how to use EasyBCD to get your Ubuntu booting OK. If you want to go with Grub, we can help you set up your menu.lst so you can boot all three OSs. Since I've never messed with EasyBCD, of course I would just go with Grub.

---

