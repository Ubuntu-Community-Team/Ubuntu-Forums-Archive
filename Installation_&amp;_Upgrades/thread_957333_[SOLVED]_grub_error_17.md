---
title: "[SOLVED] grub error 17"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by dmanbuhnik on 2008-10-24
Hi,

i'm trying to install linux mint (don't hate me :) ) but i'm running into trouble with it (that is not related to specific dis. but for grub (=all linux dis))

my hard-disks layout:
on ICH10R -
2*74GB Raptors @ RAID0 @ NTFS (using fakeraid with ICH10R) - windows xp 64bit
250GB WD @ NTFS - my data
80GB WD for linux (right now i have 4GB for swap at the end of the disk, and the rest with EXT3 for "/")

boot order is:
1) CD/DVD burner
2) 80GB WD
3) RAID0

i'm using LIVEUSB to install the system (i have 60GB 2.5'' one with UBUNTU 8.10 64bit and 16GB SanDisk Cruzer with Linux Mint 5 64bit)

after i install Mint i get after boot the "grub error 17" msg
i tried to change in the menu.lst the (hdX,0) from 0 to 5 and no-go
in device.map file i can see that /dev/sdd is mapped to (hd3) (which was the first value after install of grub)

what am i missing here?

fdisk -l output:
```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x894f894f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18078   145211503+   7  HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00240000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00060e77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdd: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa0caa0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9228    74123878+  83  Linux
/dev/sdd2            9229        9726     4000185   82  Linux swap / Solaris

Disk /dev/sde: 60.0 GB, 60011642368 bytes
255 heads, 63 sectors/track, 7295 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1da86956

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        7296    58605088+   c  W95 FAT32 (LBA)

```

device.map output:
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde
```

menu.lst output:
```
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
default		0

gfxmenu=/etc/grub/message.elyssa

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=/dev/sdd1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

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
##      altoptions=(recovery mode) single
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

title		Linux Mint x64, kernel 2.6.24-16-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint x64, kernel 2.6.24-16-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdd1 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint x64, kernel memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

if you could help me boot to my Mint/Ubuntu that would be great, and then i could move to the next thing which is adding Windows Xp entry in grub

Thx in advance for the help

---

### Post by caljohnsmith on 2008-10-24
So do you get the Grub error before seeing a menu on start up (or seeing "Press ESC to see menu"), or do you get the error 17 after selecting Ubuntu to boot from the boot menu? 

In order find out which MBR your Grub is installed to, please also post the output of:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdd count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sde count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
And for whichever of the drives above return "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify your setup.

---

### Post by dmanbuhnik on 2008-10-24
the error is the only thing i get after i boot from my 80GB WD (sdd)

"GRUB" was return from /dev/sdd (which is good due to the fact that i tell the installer to put it there)
(all other returned with "Missing operating system" except for sdb which is the 2nd HD that has my RAID0)

sudo dd if=/dev/sdd bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff01                                   
0000002

this is the output from the 2nd command

thx again

---

### Post by caljohnsmith on 2008-10-24
OK, that's great news that only sdd returned "GRUB", because it means you have Grub installed to the Ubuntu drive which is most ideal. But the second dd command tells me that Grub is looking on sdd2 for its boot files, rather than sdd1 where your Ubuntu partition is, so that's why you are getting the error 17. The solution should be really easy, just boot your Live CD and do:
```
sudo grub
grub> root (hd3,0)
grub> setup (hd3)
grub> quit
```
When you reboot, you should at least get the Grub menu on start up, and hopefully choosing Ubuntu will work. If not, let me know, and we can modify your Grub's menu.lst to boot Ubuntu. Let me know how it goes. :)

---

### Post by dmanbuhnik on 2008-10-24
:KS
that did the trick
(i had to edit to (hd0,0) but that was easy from the grub menu)

Thx for the help!

---

### Post by dmanbuhnik on 2008-10-25
ok, i need help with the windows enrty in menu.lst

i didn't manage to added it correctly to the menu.lst
any help?

Thx

---

### Post by caljohnsmith on 2008-10-25
Since Windows is on another drive, and since we don't know where that drive is in the BIOS boot order, we can't know for sure how to boot it from Grub at this point. Therefore usually the easiest solution is to just list all the possible combos for Windows in your menu.lst, try them on start up, and once you find which one works you can delete the other entries. First open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom of the file add:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title	   Windows XP (hd3)
root       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1

title	   Windows XP (hd4)
root       (hd4,0)
map        (hd0) (hd4)
map        (hd4) (hd0)
chainloader +1
```
One of those entries should work to boot Windows, assuming you don't have any issues with Windows at this point. If none of them work, let me know exactly what happens on start up when you try each one. Otherwise let me know how it goes. :)

---

### Post by dmanbuhnik on 2008-10-29
sorry for the long delay (work)

it work (the first 1)
Thx for all the help

---

