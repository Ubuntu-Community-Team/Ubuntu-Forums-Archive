---
title: "HD seen as SD"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Juha Aaltonen on 2007-10-19
What's going on?
I have tried to replace debian with ububtu, but the installation
does not work. The installation seems to do a lot of things, but the
booting fails. It seems like the setup thinks that my hard drive is a SCSI disk.

My machine is (probably typical) x86 machine with CD-RW in the 1st IDE connection (master) and 250 GB IDE disc in the 2nd IDE connection (master). I guess that the disc should be hdc. The linux root partition is the 3rd partition on the disc. First 2 are windows partitions (primary + extended) so the linux root partition should be hdc3?. For some weird reason the /dev does not list a single hd device, but instead sd devices just as I would expect my partitions to look like idf the drive was a SCSI disc: sda1-sda6. I guess they should be hdc1-hdc6.

What can I do to install the ubuntu linux so that it boots?

Oh, and  my machine is not too new:

MoBo MSI 745 Ultra (MS-6561)
with SiS 745 chipset

SAMSUNG CD-R/RW SW-252F as IDE 0 master

MAXTOR STM3250820A as IDE 1 master
 partition 1: 97Gb NTFS (win)
 partition 2: Extended partition
   Logical drive1: 57Gb NTFS (win data)
   Logical drive2: 1Gb FAT(win data)
 partition 3: 73Gb ext3 (Linux root)
 partition 3: 4Gb swap  (linux swap)

Debian used to refer to the linux-partition as hdc3.

---

### Post by Juha Aaltonen on 2007-10-20
The installing was made with downloaded 7.10 ISO image burnt on CD, but I also tried free 7.4 CD from the community that I got from a friend with the same results.

---

### Post by Jimlas53 on 2007-10-20
I believe it is the way the disk management is now set up.  All of my systems are IDE (notebooks might be SATA) and they all are SDA, SDB, etc.  Ubuntu still recognizes the partitions correctly, and you should be OK.
Hope this helps!

-Doug:)

---

### Post by Jimlas53 on 2007-10-20
Are you able to boot up the Live CD?
Or are you seeing sda in the partitioner?

-Doug

---

### Post by Juha Aaltonen on 2007-10-20
The live CD runs fine.
I have to check what it says in the partition editor.
Anyway it shows the partition sizes and types right, and the boot manager installs in the right place. It boots windows OK, but linux does not start. Instead I have some strange looking shell (busybox) that has no disk management tools. It seems to run a miniature linux on the ram disk. Even if the HDs have changed to SDs, should it show SDC instead of SDA?

---

### Post by Juha Aaltonen on 2007-10-20
Yes, the partition editor shows the partitions as sda1 - sda6. and I recall that the boot loader is installed on hd(0).

---

### Post by Jimlas53 on 2007-10-20
Usually the first hard drive (IDE0) will be assigned SDA, 2nd drive SDB, 3rd drive SDC, etc.
For some reason the partitioner or LVM decided your drive needs to be SDC.  The bigger issue is why the OS is not starting.
Can you look at /boot/menu.lst and see what partition is assigned to boot Ubuntu from?

---

### Post by rleidt on 2007-10-20
While 7.10 won't install for me either, I had no problem with this "ATA failing cause I don't have sata" issue while installing 7.40 but I had a slow boot and at the end of this post and I'm sure this is the issue with the 7.10 installation. (See the fix I used below).

The fix is great for the installed system but how do we modify a CD?  I have no idea how to make it ignore "ata_piix" and use "ide_generic". Boot options? Some busybox commands?

It would be real nice if someone posted the steps to make this work for the the newbie and if it couild be made "sticky" in the forum, even better. This is messing up a lot of people.

************
edit /etc/initramfs-tools/modules, and adding this lines:

piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

# prevent unnecessary modules from being loaded (you don't need to do this)
blacklist ata_generic
blacklist libata
blacklist scsi_mod

after editing:

sudo update-initramfs -u

**************

Credit for this 7.40 slow boot fix goes to "Fabio Povoledo". He had it posted in a forum somewhere and I was days finding the solution. I saw a lot of people trying to fix the slow boot issue. I assume none of these people could do a fresh 7.10 install.

---

### Post by Juha Aaltonen on 2007-10-20
My boot is not slow - it doesn't take place at all.

The strange shell had , in parenthesis, something about ramfs - maybe initramfs.

Anyway, I started live CD, mounted the sda3 and a windows partition and copied some files there. Then I booted windows and converted the files into the windows text format to be able to show them here, so here:

device.map:
(hd0)	/dev/sda

fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5fe6b559-ce31-4f1c-a8c4-cb62d8a5745e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=527CF6437CF62181 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=C0D8D353D8D34676 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=5416-00D0  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=633f0533-e1e0-44b4-84ad-1007c63ff2b5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

mtab:
/dev/sda3 / ext3 rw,data=ordered 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,noatime 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0

menu.lst:
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
# kopt=root=UUID=5fe6b559-ce31-4f1c-a8c4-cb62d8a5745e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5fe6b559-ce31-4f1c-a8c4-cb62d8a5745e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5fe6b559-ce31-4f1c-a8c4-cb62d8a5745e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Juha Aaltonen on 2007-10-21
So should i give up with ubuntu and try fedora instead?

---

