---
title: "Grub e windows xp"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by linsspinho on 2008-01-27
hello people, i am here for the first time, as i did not find any answer to my problem, i´ll tell what happen: i have xp on
first partition then i installed Ubuntu 7.10 15 days ago on 2ª primary partition, when i was start windows xp for the first 
time, after ubuntu installation, grub came in and i chose xp, then window xp started but suddenly it showed a blue screen 
that could not read then 
restart, i did not got desperated, so i tried again, this time its started well, but that happens every time after i use 
ubuntu. that´s so annoying, i know something is wrong and isn´t a very big problem to fix. i´ve installed so many diferents distros 
with differents bootloaders and never got problems like this one. I think there is a small problem when you choose a  partition to 
install the boot loader on ubuntu, ´cos i chose the same partition that ubuntu is installed, 2º primary,but grub, i´m not 
sure, chose whatever its wants, or "thinks" is better for ubuntu, as it chose 4º primary fat 32 partition. I am saying this
because to fix this problem i´ve tried to install bootmagic, but its did not find grub or ubuntu to load. I have some 
experience with dual booting, i know some of primary, active, extend partitions, and i´ve seen on grub configuration file 
that there is a command, i think, makeactive isn´t work well and when windows xp detects that, its restarts to make its 
partition active, i dont know. i need help. thanks in advance. 

mainboard - gigabyte
processor - athlon 64 3200+
memory - 1gb
video on board
hard drive - ide Wd 80gb
window xp pro

---

### Post by Pumalite on 2008-01-27
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by linsspinho on 2008-01-27
thanks for been so fast!!!!

here is sudo fdisk -lu

Disco /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total de 156301488 setores
Units = setores of 1 * 512 = 512 bytes
Disk identifier: 0xe7cc21a8

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/hda1   *          63    56452409    28226173+   7  HPFS ou NTFS
/dev/hda2        56452410    77079869    10313730   83  Linux
/dev/hda3        77079870   135813509    29366820    f  Win95 (LBA) Partição Extendida
/dev/hda4       135813510   156296384    10241437+   c  W95 FAT32 (LBA)
/dev/hda5        77079933   134431919    28675993+   b  W95 FAT32
/dev/hda6       134431983   135813509      690763+  82  Linux swap / Solaris

Disco /dev/hdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total de 78242976 setores
Units = setores of 1 * 512 = 512 bytes
Disk identifier: 0xf9fbf9fb

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/hdb1   *          63    27953099    13976518+   7  HPFS ou NTFS
/dev/hdb2        27953100    78236549    25141725    f  Win95 (LBA) Partição Extendida
/dev/hdb5        27953163    78236549    25141693+   b  W95 FAT32

Disco /dev/sda: 999 MB, 999555072 bytes
134 heads, 12 sectors/track, 1214 cylinders, total de 1952256 setores
Units = setores of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1   *          63     1952255      976096+   6  FAT16






here is cat /boot/grub/menu.lst



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
default         4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         5

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
# kopt=root=UUID=83ea77a2-3e01-4486-93d3-579589bd27e0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=83ea77a2-3e01-4486-93d3-579589bd27e0 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=83ea77a2-3e01-4486-93d3-579589bd27e0 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by Pumalite on 2008-01-27
Which one do you want to boot?

'# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
__________________'

---

### Post by linsspinho on 2008-01-27
Hi Pumalite, thanks again!

i want to boot on xp in 80gb hardrive

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

but,  i can not understand your point.  Or you did not understand my point. Or maybe you trying to see how much of linux's knowlege i have(very basic). Or maybe i did not provide all information for you.  Ok  let me give you some more info:  

It is true that i forgot to explain that i had a 2º hard drive, and, also its has a windows xp installation on it, and i had this before i installed ubuntu, and i use one of its two partition as backup for several  files, but i dont wanna boot on this one because its xp installation is from another motherboard that i still have, but is out of a case(tower), and it doesn't work in my current motherboard so i dont intent to boot on it. 

as you can see, on my menu.lst i've changed  the default entry to 4, but initially it was 0(ubuntu), i thought that would fix the problem.

also, when windows xp starts after grub its shows that green loading bar(not the white one), then comes the blue screen  e goes so fast, restarting. 

I think windows xp is so sensitive.  I dont know if grub need to make its partition active to get  the boot, seems that grub isn't hidding its partition or not making xp active, like bootmagic used to do with my others distro.

i'll try more info later
thanks

---

### Post by Pumalite on 2008-01-27
Backup your menu.lst:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
gksudo gedit /boot/grub/menu.lst
Erase this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Modify this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
To this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1
Make your kernel line:
(hd0,1)
Save, exit, reboot.

---

### Post by linsspinho on 2008-01-27
Before i tell you the results, let me tell you what exactly happens;

before the changes you asked me to do: 

grub loads -> windows xp is choosen -> the litle green progress bar is shown(everything seems ok)->
the blue screen appear very fast - then restart -> grub loads again- then comes the Windows XP advanced options menu(the one you press F8, but i dont press anything) i choose normal mode - the windows xp start ok!

after the changes you made:

grub loads - windows xp is choosen -> then comes the Windows XP advanced options menu(the one you press F8, but i dont press anything) i choose normal mode the litle green progress bar is shown(everything seems ok)->the blue screen appear very fast - then restart

thanks for trying!!

---

### Post by linsspinho on 2008-01-27
i forgot two tell you that i am using ubuntu 64bit,  maybe  there is a relation because  mostly i do not turn off the computer, i reboot and choose windows. maybe there is nothing to do with...:confused: 

i'll try something else

thanks

---

### Post by Pumalite on 2008-01-27
You have three boot flags: hda1, hdb1 and sda1. You need only one. Try reinstalling Grub to hda1 (hd0):
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Usse Gparted to remove flags from hdb1 and sda1

---

