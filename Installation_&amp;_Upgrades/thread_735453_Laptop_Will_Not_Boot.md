---
title: "Laptop Will Not Boot"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by pdreger on 2008-03-25
I'm setting up a laptop for a nephew. It's a Dell Latitude X200. Here's the specs for the HW:

256K Ram (more on order)
80GB Hard Drive (Seagate Momentus 5400.2 Model ST98823A) PATA drive

I've checked the jumpers on the drive and it's set to Master. And the BIOS is set to boot off the hard drive.

I am NOT dual booting anything else. 

This is a brand new drive and hasn't been formatted with anything else

When I do lshw -C DISK I get
description: SCSI Disk
product: ST98823A
vendor: ATA
physical id: 0.0.0
logical name: /dev/sda
version: 3.06
serial: 5PK25KZV
size: 74GB
capabilities: partitioned partitioned:dos
configuration: ansiversion=5

Here's what gparted live cd says about config:
PArtion       Filesystem   Size          Flags
/dev/hda1   ext3            9.77GB    boot
/dev/hda2   linux-swap  1GB        
/dev/hda3   ext3            63gb

When I fdisk -l I get
Disk /dev/sda: 80.0 GB
Device         Boot      Start   End      System
/dev/sda1     *            1       1275    Linux
/dev/sda2                 1276    1402   Linux swap / Solaris
/dev/sda3                  1403   9729   Linux

I've done the grub reset process described elsewhere in the forum.


I can boot up the Live CD and when I select Boot of the First HArd Drive I get the grub menu and everything starts correctly. 

When I remove the LiveCD and try to boot off the drive nothing happens but the drive light comes on and stays on.

BTW: This used to have a 30GB Toshiba drive in it and I was able to install and boot from the drive but then that drive died and I replaced it with the 80GB drive. I also had a 160GB drive that I tried but had the same results as with the 80GB drive.  

I've been searching the forum and google for a week now. I've tried every solution mentioned and have reinstalled from the Live CD at least 10 times now but they all end the same. 

Any suggestions or help greatly appreciated.

---

### Post by Pumalite on 2008-03-25
You cannot boot a Live CD with 256 of RAM, unless you make a 500 MB /swap partition ahead of time. For your RAM I'd recommend Xubuntu Alternate CD for speed. (lighter Desktop):
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by pdreger on 2008-03-25
Thanks, but it does boot off the live CD. I can actually run the OS when I use the Live CD. I can then select install when the OS comes up and have the installation run to completion.

I can also start the live CD, select the boot from first hard drive option and it'll boot off the hard drive then as well. I can even remove the Live CD once the GRUB menu shows up and have the OS boot completely. 

 It's when I remove the Live CD and then try to boot off the hard drive that it no longer boots.

And I said in my post, I had the OS running on the same machine with the same RAM but on a 30G drive. When the 30G drive died I replaced it with a 80G drive and then my problems started.

---

### Post by Pumalite on 2008-03-25
From the Live CD, at the Terminal, post:
sudo fdisk -lu

---

### Post by pdreger on 2008-03-26
Here's the output of fdisk -lu
zack@zack-laptop:~$ sudo fdisk -lu
[sudo] password for zack:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000309e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   154850534    77425236   83  Linux
/dev/sda2       154850535   156296384      722925    5  Extended
/dev/sda5       154850598   156296384      722893+  82  Linux swap / Solaris

---

### Post by Pumalite on 2008-03-26
While on the Live CD, mount your partition:
sudo mkdir /media/sda1
sudo mount -t ext3 /dev/sda1 /media/sda1
Post the output of:
cat /media/sda1/boot/grub/menu.lst

---

### Post by pdreger on 2008-03-26
Here's the output as requested. Thanks for all the help.

zack@zack-laptop:~$ cat /media/sda1/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=aa4df74e-3ed9-485f-a40a-3feb48de9b8a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=quiet splash vga=785 locale=en_US

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
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=aa4df74e-3ed9-485f-a40a-3feb48de9b8a ro quiet splash vga=785 locale=en_US
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=aa4df74e-3ed9-485f-a40a-3feb48de9b8a ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Pumalite on 2008-03-26
Your menu.lst is what the doctor ordered. Obviously your installation recognized your hard drive and it seems to have installed fine. We are left with the Xserver. Do you see the Grub menu at boot?

---

### Post by ipatec on 2008-03-26
I'm having the same problem.. I have a Dell Inspiron 6400 laptop...I boot the CD and any options do nothing. The only one that works is Boot from main HDD... any advice?

---

### Post by Pumalite on 2008-03-26
Burn a new CD. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on iso, burn at 4x or less on CD-R, Check CD integrity after burn and before install.
Post your specs and tell me what iso you are using.

---

### Post by pdreger on 2008-03-26
If I boot straight off the hard drive nothing happens. Screen stays black and disk spins continuously..

If I boot of the Gparted LiveCD and then select the option to Boot MBR on first hard disk I then get the grub menu and then the OS boots. Same if I boot of the Ubuntu LiveCD and select boot off first hard drive.

I've heard some talk about their being a problem with gparted and different disk controllers where some portion of the 1st partition gets zero-filled. Could that be happening here?

---

### Post by pdreger on 2008-03-26
I don't have access to the ISO I used but I have run a "Check CD" from the Live CD and it reports that the CD is good. I created the current Live CD  using the instructions you referenced and used the tools identified there to create the CD. I'll burn another image tonight and we'll see what happens.

---

### Post by pdreger on 2008-03-28
OK, After 2 more days of research I think I understand the source of the problem. It appears that the hard drive I'm using is "stuck" in slave mode .

I've come to this conclusion after trying to get the drive to boot under 3 different OS on 2 different machines. Here's what I've tested:
 - GOS on Dell X200
 - Xbuntu on Dell X200
- WinXP on Dell x200
 - GOS on ThinkPad T60
 - Xbuntu on Thinkpad T60
 - Win XP on ThinkPad T60

In none of these cases will the OS boot. directly off the hard drive I can, in the cases of the Linux based OS, boot up a LiveCD, Select the Boot from the First Hard Drive option and have the OS boot.

I borrowed a 40GB Toshiba drive and had no problem getting either GOS or Xbuntu to boot on the X200. Toshiba was the OEM for the machine so no surprise there.

I also have a 160GB drive from the Seagate that I'm going to try on the Dell X200 to see if there is something about the Seagate / Dell combination . I've done some research with Google to determine if there is anything about a Seagate/Dell problem but I haven't run across anything. 

If anyone else has any experiences with hard drives stuck in "slave" mode please let me know. Otherwise I'm considering the OS won't boot problem closed as a hardware issue.

---

