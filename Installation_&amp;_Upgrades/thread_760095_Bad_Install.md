---
title: "Bad Install?"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by PortraitOfKarma on 2008-04-19
Okay, I need some help installing Ubuntu 7.10.  I burnt the image onto a disk, and I've loaded it.  When I open up "install", I go through the whole thing until the partitioner opens up.  At that point, I am confused.

I did the "Guided- use entire disk option" twice now. I think the problem may lie in the fact that I have 3 physical hard drives in my computer.  A 80 GB in the Master (IDE3/hde), another 80GB under Slave(IDE3/hdf), and a 200GB under Master (IDE4/hdg).  What option should I use when partitioning my hard drives?  I completely want to delete what was left of Microsoft XP, as I already backed everything up.

The reason I've had to install twice is because the first time, my CD tray wasn't ejecting after the install completed, and the second time because it did, but I got the "Grub Error 2" problem when booting up after the install.

I can be reached via AIM: Labeledloser212, [email]ventblvd@yahoo.com[/email], or just reply here.

Thanks in advance!

---

### Post by Pumalite on 2008-04-19
Post:
sudo fdisk -l
(boot your Live CD)

---

### Post by PortraitOfKarma on 2008-04-19
I hope I did it right, this is my very first experience ever with Linux.

```
Disk /dev/hde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd65ddc8d

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        9352    75119908+  83  Linux
/dev/hde2            9353        9729     3028252+   5  Extended
/dev/hde5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/hdf: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x2b3be507

Disk /dev/hdf doesn't contain a valid partition table

Disk /dev/hdh: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd478afe

   Device Boot      Start         End      Blocks   Id  System
/dev/hdh1   *           1       24321   195358401    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

---

### Post by Pumalite on 2008-04-19
Mount the partition:
sudo mkdir /media/hde1
sudo mount -t ext3 /dev/hde1 /media/hde1
Post:
cat /media/hde1/boot/grub/menu.lst

---

### Post by PortraitOfKarma on 2008-04-19
```
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
# kopt=root=UUID=12c011ea-ba99-4bdf-83f4-44dcef6305fd ro

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
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=12c011ea-ba99-4bdf-83f4-44dcef6305fd ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=12c011ea-ba99-4bdf-83f4-44dcef6305fd ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~$ 

```

---

### Post by Pumalite on 2008-04-19
Before I continue: what about hda, hdb and hdc?

---

### Post by PortraitOfKarma on 2008-04-19
What do you mean by hda, hdb, and hdc?

---

### Post by Pumalite on 2008-04-19
Normally, first drive is sda or hda.

---

### Post by PortraitOfKarma on 2008-04-19
I may have my drives configured so that the DVD drives take up the first few letters?

---

### Post by Pumalite on 2008-04-19
If that were the case; your Ubuntu should be booting according to your menu.lst.
This is error 2:

	

                






Quoted from the GNU/GRUB manual

    2 : Bad file or directory type
        This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO.

---

### Post by PortraitOfKarma on 2008-04-19
I was googling my error, and many people suggested modifying the way my hard drives boot, but most of this is aimed for people with just one hdd.  Also, there's nothing in my BIOS that'll let me do so.

---

### Post by Pumalite on 2008-04-19
You might have to get into your computer and change the cables and jumpers. If you are not sure, get an IT.

---

### Post by PortraitOfKarma on 2008-04-19
Luckily, I may be able to get someone to do this for me, however, what do you think the problem is with this install based on the information provided?

---

### Post by Pumalite on 2008-04-19
You have to fix the order of your drives and start from scratch. I'll be back tomorrow 8 AM Eastern Time. Cheers

---

### Post by PortraitOfKarma on 2008-04-19
Thanks a lot!  I'll give it a go later.

---

