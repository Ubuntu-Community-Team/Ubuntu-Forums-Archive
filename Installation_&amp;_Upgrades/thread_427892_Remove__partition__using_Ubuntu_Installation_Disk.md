---
title: "Remove  partition  using Ubuntu Installation Disk"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by myousef on 2007-04-29
Hello,
I have tried to install Ubuntu twice and each time i got a different partition as below. How i can remove those two partitions using the Ubuntu installation disk to let me re-install Ubuntu again as dual-boot with WIndows XP. I did that because i'm getting Error 17 with grub.. so i want to start again and see if i get the same error.

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2756    22137538+   7  HPFS/NTFS
/dev/sda2            2757        3243     3911827+  83  Linux
/dev/sda3            3581        3648      546210    5  Extended
/dev/sda4   *        3244        3580     2706952+  83  Linux
/dev/sda5            3604        3648      361431   82  Linux swap / Solaris
/dev/sda6            3581        3603      184684+  82  Linux swap / Solaris

Partition table entries are not in disk order


Yours,
myousef

---

### Post by 67GTA on 2007-04-29
With the live cd open a terminal and type "sudo apt-get install gparted" Then go to SYSTEM>ADMINISTRATION>GNOME Partition Editor. You can create or delete partitions plus more.

---

### Post by myousef on 2007-04-29
Thank you very much. It works fine and i re-nistalled Ubuntu. Unfortunatly whne i boot my laptop i got an error .. grub .. erro17 .. any help in how over come that?

Best
myousef

---

### Post by undecidable on 2007-04-29
Grub error 17 is when the partition exists but the filesystem can't be recognized by Grub (I believe).

So likely in the mucking around something has gotten out of sync,
resulting in the grub entry that is trying to boot your linux root partition pointing to the wrong partition.

suggest you (with the live CD) compare the output of:
a.  fdisk -l
     (ie as in your original post)
b.  cat /boot/grub/menu.lst

Likely you will find menu.lst is not pointing to the correct partition.
Remember sda1 is (hd0,0) and sda2 is (hd0,1)

---

### Post by 67GTA on 2007-04-29
Error 17 usually has to do with grub not recognizing the partition or file system type. Did you let the installer do all the work? If you did then the file system type is not the problem. Try to fix grub. In a terminal type "sudo grub". You should have a grub> prompt. Then type in "find /boot/grub/stage1" and post the output. If you can't get to a prompt then you can use the live cd.

---

### Post by myousef on 2007-04-29
OK. This is the output of find /boot/grub/stage1
(hd0,1)


While this is the output of fdisk -l :

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2756    22137538+   7  HPFS/NTFS
/dev/sda2   *        2757        3603     6803527+  83  Linux
/dev/sda3            3604        3648      361462+   5  Extended
/dev/sda5            3604        3648      361431   82  Linux swap / Solaris

Your help...

Bests
myousef

---

### Post by undecidable on 2007-04-29
They are both saying your Lx system is on hda2 (hd0,1),
which is helpful.

But we need to see what grub is actually trying to boot to.
As I suggested above, pls compare this to
cat  /boot/grub/menu.lst
which is what grub is actually trying to boot to.

---

### Post by 67GTA on 2007-04-29
Now get back to the grub prompt"sudo grub" and run "root (hd0,1)" and then "setup (hd0)". That might put grub back in your ubuntu partition and your MBR.

---

### Post by myousef on 2007-04-29
This is the menu.lst file contents:
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
# kopt=root=UUID=4b20eed7-b2b4-4835-9ab1-9a5c39e63571 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4b20eed7-b2b4-4835-9ab1-9a5c39e63571 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4b20eed7-b2b4-4835-9ab1-9a5c39e63571 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by myousef on 2007-04-29
To : 67GTA
I did follow your last instruction "
Now get back to the grub prompt"sudo grub" and run "root (hd0,1)" and then "setup (hd0)". That might put grub back in your ubuntu partition and your MBR."

I still have the same booting problem. I mean "
GRUB Loading Stage1.5.
GRUB loading, please wait...
Error 17"

Please what i shall do now?

Best
myouse

---

### Post by undecidable on 2007-04-29
Your menu.lst uses uuids to point to the partitions,
and so it is hard to be sure it is pointing to the right partition.

You ned to be sure that /dev/sda2 
(which I think is your linux root partition) is
UUID=4b20eed7-b2b4-4835-9ab1-9a5c39e63571
which is what grub is trying to boot to.

One way to do it is in the live Cd go to a command prompt and type 
tune2fs -l /dev/sda2
This will print the superblock, and one of the entries is the uuid.
Check it is the same as above.

Alternatively as a temporary measure, you could replace 
root=UUID=4b20eed7-b2b4-4835-9ab1-9a5c39e63571
in menu.lst with
root=/dev/sda2

-----------------

A 2nd thing you should try is using 67GTA's suggestion above for hte find command, enter:
find /vmlinuz 
to try to get grub to help you by fidning the kernel for you.

---

### Post by 67GTA on 2007-04-29
If you boot with the live cd again go back to gparted, right click on your linux partition, select manage flags, and then check the "boot" box.

---

### Post by myousef on 2007-04-30
To undecidable:
I have updated menu.list to include /dev/sda2 

Still having the same problem of Error 17

To 67GTA:
The flag was "boot" and i still have the same problem of Error 17...

Any other suggestions...?

Best,
myousef

---

### Post by 67GTA on 2007-04-30
The only other thing I can think of trying is Super Grub Disk. You download and burn it to cd and boot from it. It will install Grub to your MBR, partition, and a number of other grub tasks. If that doesn't work then you might want to reinstall and manually set the partition mount points boot,root,etc.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by myousef on 2007-05-02
I just removed Ubuntu.. i will try to install it on my new laptop soon

---

