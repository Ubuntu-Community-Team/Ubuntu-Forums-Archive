---
title: "IBM ThinkPad T41"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by kobix on 2005-07-13
Hi

I am new !

I was trying to install ubuntu on IBM T41 with WinXP Pro already installed. I saw some remarks on it before. I created a new partition for ubuntu. I also told ubuntu to put grub in the Master Boot Record (MBR). This is a problem according to [http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html](http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html).
Now when I reboot I get brub error 17. I cant use the IBM resuce key.

(1) Was this the cause of the error?
(2) How to fix things up?

Thanks, Koby

---

### Post by alastair on 2005-07-13
I have a T40p. I blew away my "utility" partition - no harm done. Is the "IBM resuce key" the "access IBM" button?


Error 17 is "the filesystem type cannot be recognized by GRUB". See :

[http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable](http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable)

It might be trying to mount your "utility" partition as the root device.

The best thing to do would be to boot Linux via a LiveCD (e.g. Ubuntu Live, or Knoppix), and copy your /boot/grub/menu.lst file.

Also, note the output of "fdisk -l".

Then post here and we can fix - and you can reinstall GRUB.

Well .... that's the theory anyway.

---

### Post by kobix on 2005-07-13
ubuntu@ubuntu:/$ sudo fdisk -l /dev/hda

Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       70695    35630248+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           73425       77520     2064352+  83  Linux
Partition 2 does not end on cylinder boundary.


I cant see the file that you said? How do I see the content of the hard disk?

Thanks, Koby

---

### Post by alastair on 2005-07-13
I guess where /dev/hda2 is mounted ("mount").

Look under /boot for :

/boot/grub/menu.lst

You might need to mount /dev/hda2.

---

### Post by kobix on 2005-07-13
I cant mount it
I tried mount /dev/hda{1,2}
I get can't find /dev/hda2 in /etc/fstab or /etc/mtab
koby

---

### Post by alastair on 2005-07-14
The /etc/fstab file holds filesystems to get mounted at boot. 

To manually mount your linux partition, try :

mkdir /mnt/tmp
mount /dev/hda2 /mnt/tmp

Then, if successful, the /boot/grub/menu.lst file is :

/mnt/tmp/boot/grub/menu.lst

---

### Post by kobix on 2005-07-14
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

---

