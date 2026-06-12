---
title: "Configuring Mutiboot"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by abulfares on 2007-11-17
I have a clean HDD (93GB). I booted from Ubuntu LiveCD and using GParted, I created NTFS 30GB Partition in the beginning of the drive. I left the rest (63GB) as unallocated. Then, I installed Ubuntu on the Unallocated so it created 60GB Ext2/3 plus 3GB Swap.

Everything up to that point was working fine.

Then, I installed XP on the 30GB NTFS partition in the beginning of the drive. XP worked fine but cannot see Ubuntu/GRUB.

I booted from the LiveCD and using GParted, I flagged the Ubuntu partition as "boot".

Now, when I boot, all I see is "Error Loading the Operating System" and neither XP nor Ubuntu work.

Please help me configure GRUB so I can see a menu and choose from it which OS to boot.

I know there are many posts and tutorials regarding GRUB configuration, but I found that it really depends on the system setup as most these guides deal with 2 separate HDD (1 with XP and 1 with Ubuntu).

Thnx

---

### Post by Pumalite on 2007-11-17
Do it again, installing XP first After using Garrted Live CD and formatting the whole drive to ntfs. Install XP. Boot Gparted again and resize XP partition (right click). Then install Ubuntu and let Grub install to MBR. You'll have dual boot and no problems.

---

### Post by abulfares on 2007-11-17
one thing though, I spent hours yesterday configuring Ubuntu with themes and effects and so on. Is there a way to edit GRUB manually? if not, is there a way I can fully backup Ubuntu?

---

### Post by Pumalite on 2007-11-17
To backup:
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)

You can edit menu.lst but you would continue to have problems later.

---

### Post by abulfares on 2007-11-17
I followed this guide: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

and now I have a working Ubuntu and I can see GRUB fine.

Is there a way to add XP to the OS list without starting from scratch?

Thnx for the Backup links btw

---

### Post by Pumalite on 2007-11-17
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by abulfares on 2007-11-17
I entered the lines and that what i got:
```

mohusam@mohusam-laptop:~$ sudo fdisk -lu
[sudo] password for mohusam:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x864f864f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              34    63296099    31648033    7  HPFS/NTFS
/dev/sda2   *    63296100   189891803    63297852   83  Linux
/dev/sda3       189891804   195371534     2739865+  82  Linux swap / Solaris
mohusam@mohusam-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=d6365896-403c-416d-b0c6-6befcd3297f3 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d6365896-403c-416d-b0c6-6befcd3297f3 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d6365896-403c-416d-b0c6-6befcd3297f3 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
mohusam@mohusam-laptop:~$ 

```
what line do I need to enter here? sorry this is my first time doing this

---

### Post by Pumalite on 2007-11-17
Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
gksudo gedit /boot/grub/menu.lst
Add this after memtest:
title         Windows 
rootnoverify          (hd0,0)
makeactive
chainloader   +1

Save, exit, reboot.

---

### Post by abulfares on 2007-11-17
Thnx a million Pumalite.

Worked with no problems

btw, I also had to add "#" to "hiddenmenu" so the menu is displayed by default

Thanks again for all the help; really appreciate it.

---

### Post by Pumalite on 2007-11-17
You are welcome. Good luck.

---

