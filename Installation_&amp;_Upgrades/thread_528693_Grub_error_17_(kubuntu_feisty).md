---
title: "Grub error 17 (kubuntu feisty)"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by Oceanic on 2007-08-18
Dear fellow  (K)Ubuntians,

I would very much appreciate some help ! :)  
Several Kubuntu installs worked but this is my first attempt of a [COLOR="Red"]dual-boot[/COLOR] of Kubuntu 7.04 along SuSe and Windows XP - effectively a triple-boot.

The installation seemed okay and XP is still alive, but I cannot reach Kubuntu 7.04 or SuSe since: 
**[COLOR="Red"]GRUB error 17[/COLOR]**

[IMG]http://www.sailingissues.com/partitions.png[/IMG]

and

[IMG]http://www.sailingissues.com/partitions2.png[/IMG]

Please note that I am a total newby with respect to partitioning and GRUB!
I am guessing that my Kubuntu partition is /dev/sdb2

Scanning for tips on the internet I tried the following GRUB commands in Konsole/LiveCD:
grub> root (hd0,1)
grub> setup (hd0)
Error 17: Cannot mount selected partition
grub> setup (hd1)
Error 17: Cannot mount selected partition
grub> root (hd1,1)
grub> setup (hd1)
Error 17: Cannot mount selected partition
grub> quit

Thanks very much in advance for your time !!!  :KS

---

### Post by Pumalite on 2007-08-18
Post:
sudo fdisk -l (small L)
cat /boot/grub/menu.list

---

### Post by Oceanic on 2007-08-18
**Thanks very much** [SIZE="3"]Pumalite[/SIZE],

Below my conversation with kubuntu:

[FONT="Courier New"]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1                  1       18572   149179558+   5  Extended
/dev/sda2           24437       30515    48829567+   7  HPFS/NTFS
/dev/sda3   *       18573       24436    47102580   83  Linux
/dev/sda5                  1        9118    73240272   83  Linux
/dev/sda6            9119       18236    73240303+  83  Linux
/dev/sda7           18237       18479     1951866   82  Linux swap / Solaris
/dev/sda8           18480       18572      746991   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sdb2            4865        9729    39078112+   f  W95 Ext'd (LBA)
/dev/sdb5            4865        8943    32764536    7  HPFS/NTFS
/dev/sdb6            8944        9729     6313513+   b  W95 FAT32
ubuntu@ubuntu:~$ cat /boot/grub/menu.list
cat: /boot/grub/menu.list: No such file or directory
ubuntu@ubuntu:~$
[/FONT]

No idea what this all means,
and the menu.list is probably somewhere else...

CHEERS !

---

### Post by Pumalite on 2007-08-18
cat /boot/grub/menu.list
Who owns the Grub?: Suse or Kubuntu?

---

### Post by ajgreeny on 2007-08-18
Your sdb disk is entirely formatted to windows file systems, ntfs and fat32, so ubuntu is not likely to be there.  On sda partitions 3, 5 and 6 are ext3 (linux) so it could be there, and partitions 7 and 8 are both swap.  Very confusing, perhaps but did you try to have a separate /home partition in either suse or ubuntu?  This might explain why there are so many partitions and we are in trouble sorting out what is what.

You will need to mount your linux partitions in the live CD and find the /boot/grub/menu.lst file to show us.  There may well be more than one of those, and it will help to see both at the moment, and then try to sort out which is the one to use when we show you how to reinstall grub.

---

### Post by Oceanic on 2007-08-18
**Thank you both, [COLOR="Red"]Pumalite[/COLOR] & [COLOR="Red"]ajgreeny[/COLOR] !**

I searched in file:/ and subfolders for **menu.list** and **menu.lst**
no menu.list was found
two menu.lst were found

rofs/usr/share/doc/grub/examples/
urs/share/doc/grub/examples/

Appreciated ! :KS

---

### Post by Oceanic on 2007-08-18
ajgreeny wrote : "*You will need to mount your linux partitions*" 

Unfortunately I have no clue how to get that done...

Cheers

---

### Post by Pumalite on 2007-08-18
You need to get the ones in /boot/grub
Mounting partitions from Live CD to access those files.
Get a Knoppix Lice CD; it mounts your partitions automatically: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Look for /boot/grub/menu.lst in sda3, sda5 and sda6

---

### Post by Oceanic on 2007-08-18
Like you said Knoppix brought me lots of harddisks on de desktop, very handy.

sda3, sda5 and sda6
were named hda3, hda5 and hda6, but were the linux partitions.

in hda6 there was no grub folder

in hda5 there was a grub/menu.lst YET I had no permission to read the file

in hda3 there was a grub/menu.lst that I was allowed to read.

Again, thank you in advance.

Below the menu.lst from hda3



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
# kopt=root=UUID=5fa27350-e743-4cac-befb-6948ac38db3b ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5fa27350-e743-4cac-befb-6948ac38db3b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5fa27350-e743-4cac-befb-6948ac38db3b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		SUSE LINUX 10.0 (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz root=/dev/hda5 vga=0x31a selinux=0 resume=/dev/hda7 splash=silent showopts 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Veilige modus -- SUSE LINUX 10.0 (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz root=/dev/hda5 vga=normal showopts ide=nodma apm=off acpi=off noresume selinux=0 nosmp noapic maxcpus=0 edd=off 3 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Veilige vga-extended modus -- SUSE LINUX 10.0 (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz root=/dev/hda5 vga=0x31a showopts ide=nodma apm=off acpi=off noresume selinux=0 nosmp noapic maxcpus=0 edd=off 3 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Pumalite on 2007-08-18
Your menu.lst seems in order. Re-install Grub following these guidelines:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Or with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Install Grub to MBR (hd0,0)

Before you do all this, one last try: edit menu.lst and in the XP entry replace 'root' for 'rootnoverify'

---

### Post by Oceanic on 2007-08-19
I was not allowed to write to the file

tried 
sudo chmod 744 /media/hda3/boot/grub/menu.lst 
and variants of this
but 
"read-only file system" ...

indeed with knoppix - in contrast to kubuntu LiveCD where I can "write" - everything is read-only...
I cannot write even to the USB-Stick

Will try the GRUB install now

Cheers

---

