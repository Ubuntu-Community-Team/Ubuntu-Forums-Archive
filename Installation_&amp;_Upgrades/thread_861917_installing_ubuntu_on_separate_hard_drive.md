---
title: "installing ubuntu on separate hard drive?"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by discostu668 on 2008-07-17
hi there,

i'm trying to get ubuntu (8.04.1) to work but for whatever reason, i can't get it to boot.  i am attempting to set up a dual boot system using separate hard drives.

i want to install the OS onto a separate 200gb internal sata hard drive (non-raid) on my dell dimension 9150 (pentium D 830 3.0ghz dual core, 4gb of ram, nvidia geforce 7600gt, dlink wda-1320 wireless adapter, creative labs x-fi xtreme audio).  i have windows (vista home premium sp1) already installed onto a striped raid0 array, but i do not want to partition my windows drive(s) because i want to avoid corruption.  

my installation attempts have consisted of:

the first partitioning option is selected (guided, use entire disk) and i select my third hd (sdc) to install.  on step #7 i click the 'advanced' button and deselect the grub boot installer.  once it finishes installing, i reboot and in the bios, i have choose to boot to the sata drive i've just installed ubuntu onto - however, it just boots right into windows.  i have tried installing with the boot loader option checked, but i get grub error 21 upon booting and i have to fix the mbr in order to boot into windows again.  unless i'm simply installing the boot loader to the wrong location?  

anyways, is there something i'm doing wrong? i don't think this should be a difficult thing to accomplish.  i've read a couple of things on this, but the solutions are far too advanced/convoluted for me to wrap my head around.  all i want is to simply install ubuntu onto my extra sata drive and boot into it without any complicated patching.   

thanks in advance!

---

### Post by logos34 on 2008-07-17
Install grub to the MBR of the ubuntu drive:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

so, for instance, if 

find /boot/grub/stage1

outputs '(hd2,0)' 

then you want to do:

root (hd2,0)
setup (hd**2**) -->puts grub on the MBR of the linux drive, /dev/sdc.  '(hd0)' will put it on first raid drive

Now toggle the boot disk in the Bios to your ubuntu drive.
> 
  i have tried installing with the boot loader option checked, but i get grub error 21 upon bootingFor future reference: here you would want to replace the default '(hd0)' with **'/dev/sdc'** or whatever the linux drive is.  But you would have to also edit the menu.lst 'root' lines to (hd**0**,x) because as soom as you switch the Bios to boot from the linux disk, the latter is seen as '(hd0)'

---

### Post by discostu668 on 2008-07-17
logos34,

i will try that as soon as i get home.

thanks for your help!

---

### Post by discostu668 on 2008-07-18
logos34,

tried it.  selected to boot from my linux drive in the bios.  grub loads and i get "error 21: selected drive does not exist".

---

### Post by logos34 on 2008-07-18
Boot the live cd, mount your root partition, and post your menu.lst:

sudo mkdir /media/sdc1

sudo mount -t ext3 /dev/sdc1 /media/sdc1 (or whatever root # is)

sudo gedit /media/sdc1/boot/grub/menu.lst

Also, include the output of 
[B]
sudo fdisk -l[/B]

---

### Post by Sef on 2008-07-18
Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by discostu668 on 2008-07-22
logos34,

this is the menu.lst output:

Disk /dev/sda: 160.0 GB, 160000000000 bytes 
255 heads, 63 sectors/track, 19452 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xd0f4738c 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       38904   312493056    7  HPFS/NTFS 
 
Disk /dev/sdb: 160.0 GB, 160000000000 bytes 
255 heads, 63 sectors/track, 19452 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x7ffdfbf8 
 
Disk /dev/sdb doesn't contain a valid partition table 
 
Disk /dev/sdc: 203.9 GB, 203928109056 bytes 
255 heads, 63 sectors/track, 24792 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x423e114a 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1   *           1       23782   191028883+  83  Linux 
/dev/sdc2           23783       24792     8112825    5  Extended 
/dev/sdc5           23783       24792     8112793+  82  Linux swap / Solaris 
 
Disk /dev/sdd: 2063 MB, 2063597568 bytes 
16 heads, 32 sectors/track, 7872 cylinders 
Units = cylinders of 512 * 512 = 262144 bytes 
Disk identifier: 0x00000000 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdd1               1        7872     2015216    e  W95 FAT16 (LBA) 

----------------------

this is the fdisk -l output:

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=8e85b4ef-318e-4e96-a462-2216110561b0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8e85b4ef-318e-4e96-a462-2216110561b0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8e85b4ef-318e-4e96-a462-2216110561b0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by logos34 on 2008-07-22
ok, looks like I was on the right track in post #2 above.  You want to set sdc as the Bios boot drive and use 'root (hd**0**,0)'.  The error 21, though, indicates that grub is having trouble finding stage2 on the drive.  

try this:

unplug the flash drive.

Boot the live cd and check sudo fdisk -l to make sure root is still seen as sdc1.  If so, mount as above.

Then,

 sudo gedit /media/sdc1/boot/grub/menu.lst

Change the all 'root' lines, as well as 'groot' line near the top, to (hd**0**,0)

Put a comment in front of 'hiddenmenu' option:

>  ## hiddenmenu
 # Hides the menu by default (press ESC to see the menu)
[COLOR=Red]**#**[/COLOR]hiddenmenuThen reinstall grub to mbr of /dev/sdc:[B]

sudo grub-install --root-directory=/media/sdc1 /dev/sdc[/B]

Give that a shot.  Further suggestions here:
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

### Post by discostu668 on 2008-07-29
that did it.  thanks so much for all of your help!

---

