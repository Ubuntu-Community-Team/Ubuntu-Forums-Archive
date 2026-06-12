---
title: "Edgy Grub Stage 2 Hang"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by shcodip on 2007-04-05
After several months of use I am now unable to boot into Kubuntu. I have tried to fix the problem myself with little luck so I am posting here hoping to get some answers. I will outline the symptoms and steps I took to solve the problem below.

1) Initial Symptom: upon boot grub would hang with the following message...

'Grub loading Stage1.5Disk Error'

I thought that grub may need to be reinstalled so I did the following...

2) Booted kubuntu using the live cd
3) Started a console and executed 'sudo grub'

At the grub shell executed...
4) find /boot/grub/stage1
This returned '(hd0,0)'
5) root (hd0,0)
6) setup (hd0)
7) exit

Upon restart I got the following grub message...

'Grub loading Stage2..'

Then I was thrown into a grub shell. 

So, it looks as if I successfully installed grub to the mbr on the initial disk which seems to me to be the correct configuration as I can execute the following command and browse to /mnt/localdisk/boot/grub/stage1

> mount -t ext3 /dev/hda1 /mnt/localdisk

I thought that perhaps my disk had been corrupted however that doesn't seem to be the case as I can mount and browse the disk fine.

My grub.conf looks like this...

> cat /mnt/localdisk/boot/grub/grub.conf
-------------------snip--------------------------------------------------------------------------
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
# kopt=root=UUID=73612d65-49b2-42d7-8618-668e29d8c25d ro
# kopt_2_6=root=/dev/hda1 ro

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

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------end snip-------------------------------------

This is a pretty vanilla grub.conf as I haven't modified it from the original that was installed with the system some time ago. 

My partition info looks like this...

> cat /proc/partitions
major minor  #blocks  name

   3     0   78150744 hda
   3     1   74951226 hda1
   3     2          1 hda2
   3     5    3196903 hda5
   3    64   78150744 hdb
   3    65   78148192 hdb1
   7     0     623164 loop0


Something that is a little distrubing to me is the output of fdisk -l

> sudo fdisk -l
Unable to read /dev/hda

This makes me think that my partition table is messed up but would I still be able to mount directories on it if this were true?

Thanks in advance for all of your help.

---

### Post by phidia on 2007-04-05
> Something that is a little distrubing to me is the output of fdisk -l

> sudo fdisk -l
Unable to read /dev/hda

Yeah that is disturbing. What output do you get from > sudo cfdisk /dev/hda?

---

### Post by shcodip on 2007-04-06
> sudo cfdisk /dev/hda

This command produces a terminal screen that displays the partition table. And the table looks correct. 

hda1     Boot     Primary     Linux ext3                   76750.09
hda5                 Logical      Linux swap / Solaris     3273.67

Something else I have attempted was running fsck on /dev/hda and I get the dreaded bad superblock message... I then ran

> sudo mke2fs -n /dev/hda

...Got a whole bunch of superblock backup numbers and tried them all but to no avail. Getting output from cfdisk gives me some hope though...

Can you offer the next step? I am a bit lost.

Thanks!

---

