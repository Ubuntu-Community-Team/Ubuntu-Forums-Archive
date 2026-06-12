---
title: "Trying to install Kubuntu on one Hard Drive and keep windows on other"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by Robert98374 on 2008-02-26
Hello Everyone!
I have 2 hard drives on my computer at this point, a 20gig hard drive for my windows XP and i just recently bought a 320gig hard drive so i could install Kubuntu also. My dilemma is i would like to install Kubuntu on the larger HD but i when i need to boot into windows i would like to be able to access the information on the HD that has Kubuntu on it. 

My understanding is that i would need to format that HD in fat32 so both operating systems can access it but i am having some issues. i don't see the option to format the HD into fat32 so i choose the option to manually partition the hard drive. This is the point that i am kinda stuck....i am sitting at that screen using the liveCD as we speak. 
Thanks to anyone that responds quickly in advance!

---

### Post by Pumalite on 2008-02-26
You don't have to worry. Let kubuntu do it's job and then install:
[http://www.fs-driver.org/](http://www.fs-driver.org/) in your Windows and you will be able to see Kubuntu.

---

### Post by Robert98374 on 2008-02-26
Thanks!
wow thats a giant load off my shoulders!

---

### Post by Pumalite on 2008-02-26
You are welcome. Good luck.

---

### Post by Robert98374 on 2008-02-26
OK now for some reason its getting stuck at 5% when partitioning...it didnt to this the first time so i am kinda confused

---

### Post by Pumalite on 2008-02-26
Burn a new CD. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Burn at 4x or less. Use good quality CD-R media

---

### Post by Robert98374 on 2008-02-26
Is it possible to burn a CD in live? because i now cant even access windows because grub is messing up....

---

### Post by Robert98374 on 2008-02-26
I have tried Xubuntu, Ubuntu Alt Cd and still they all get caught up at 5% when formating...i dont have a windows XP CD either...

---

### Post by Pumalite on 2008-02-27
Fix Windows MBR with your installation CD>Recovery>FIXMBR>FIXBOOT
or use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Robert98374 on 2008-02-27
Well i disconnected the windows HD then tried installing it, it moved past the 5% mark and is installing right now. Going to go do a few things and come back to it. How hard is it to add windows to grub?

---

### Post by Robert98374 on 2008-02-27
Well i dont know exactly what i did that fixed the issue but i am now writing this in windows and i am installing driver so i can use the rest of the Hard drive it windows

---

### Post by Robert98374 on 2008-02-28
Ok so i just went into Kubuntu and updated the system but now when i booted back into windows it wont let me do anything with the drive besides format it.

---

### Post by Pumalite on 2008-02-28
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by Robert98374 on 2008-02-28
Sorry i forgot the code to make it a small box thats scrollable inside the reply :(
Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92928eee

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   617554664   308777301   83  Linux
/dev/hda2       617554665   625137344     3791340    5  Extended
/dev/hda5       617554728   625137344     3791308+  82  Linux swap / Solaris

Disk /dev/hdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders, total 40132503 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x76e276e2

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    40114304    20057121    7  HPFS/NTFS

---

### Post by Pumalite on 2008-02-28
Where is the menu.lst?

---

### Post by Robert98374 on 2008-02-28
Is this what you are talking about?
Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92928eee

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   617554664   308777301   83  Linux
/dev/hda2       617554665   625137344     3791340    5  Extended
/dev/hda5       617554728   625137344     3791308+  82  Linux swap / Solaris

Disk /dev/hdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders, total 40132503 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x76e276e2

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    40114304    20057121    7  HPFS/NTFS
robert@robert-desktop:~$ sudo fdisk -lu cat /boot/grub/menu.lst
robert@robert-desktop:~$ sudo fdisk -lucat /boot/grub/menu.lst
fdisk: invalid option -- c

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by Pumalite on 2008-02-28
At the Terminal, post the output of:
cat /boot/grub/menu.lst

---

### Post by Robert98374 on 2008-02-28
Sorry forgot that i had to copy from the terminal from edit not ctrl+c
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
# kopt=root=UUID=8b02e504-5349-46c2-af21-5433168fe10b ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8b02e504-5349-46c2-af21-5433168fe10b ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8b02e504-5349-46c2-af21-5433168fe10b ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


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

### Post by Pumalite on 2008-02-28
Windows in hdb1 ia a problem, but let's try:
Edit menu.lst after backing up the file.
Change this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

To this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Professional
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

Save, exit and reboot.

---

### Post by Robert98374 on 2008-02-28
Ok its working great now thank you!

---

### Post by Pumalite on 2008-02-28
You are welcome. Good luck.

---

