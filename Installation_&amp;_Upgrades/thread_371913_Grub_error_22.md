---
title: "Grub error 22"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by Patrick83 on 2007-02-27
After I installed Ubuntu 6.06 on my pc (dualboot with Windows XP) and i restarted the computer. I'd received an Grub error 22.

To fix the problem i put the Windows XP-cd and used the recovery-cd. Tried both fixmbr and fixboot and the i restarted the pc. The error still was there waiting on my.:( 

Then i tried supergrub. First the usb-version and installed it following this artikel. [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk") But on the moment i put i in my pc he freezes. Then i tried the cd-version, but for some reason he cannot load it. Yes, i put my cd-rom on top of the boot-sequence. Does anyway has een idea to make the grub work, or to restore the MBR so i can boot Windows again. And the install Ubuntu back. 


Partitions
/dev/sba 298.09GB Empty
/dev/sdb1 48.83GB Windows xp
/dev/sdb5 249.25GB data
/dev/sdc5 123.47GB data
/dev/sdc6 5.76GB Swap
/dev/sdc1 168.85 Ubuntu

---

### Post by tgalati4 on 2007-02-27
I just love how the Windows partitions are shrinking!

Boot the Ubuntu live CD.

sudo mount /dev/sdc1

cd /mnt/sdc1/boot/grub/

more menu.lst
more device.map

We need to see what is going on before you can help yourself.

Oh, and welcome to the forums.

---

### Post by Patrick83 on 2007-02-28
When I type sudo mount /dev/sdc1, I get the message 

Mount: can't find /dev/sdc1 in /etc/fstab or /etc/mtab

:confused:

---

### Post by rsambuca on 2007-02-28
You'll have to mount the drive to a specific directory.

First make the directory:```
mkdir /mnt/sdc1
```
Then mount the partition to the directory you just created:```
sudo mount /dev/sdc1 /mnt/sdc1
```

---

### Post by Patrick83 on 2007-02-28
Thank you, for your quick reply. Here is the print-out.


ubuntu@ubuntu:/mnt/sdc1/boot/grub$ more menu.lst
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
# kopt=root=/dev/sdc1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title           Ubuntu, kernel 2.6.15-26-amd64-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdc1 ro single
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
boot

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

ubuntu@ubuntu:/mnt/sdc1/boot/grub$ more device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
ubuntu@ubuntu:/mnt/sdc1/boot/grub$

---

### Post by rsambuca on 2007-02-28
From the live cd, use a terminal to enter the grub engine```
sudo grub
```
At the grub> prompt, enter ```
find /boot/grub/stage1
```, and what do you get?

---

### Post by Patrick83 on 2007-02-28
(hd2,0)

---

### Post by rsambuca on 2007-02-28
I think the fact that you did a fixmbr from the XP disk and still get error 21 means that grub has guessed the drive order incorrectly.  Check the boot order of your hard drives in the Bios and make sure they match the order listed in your device.map.

To enter your bios you usually have to press Esc, or F12, or F11, just after the beeps when you restart your rig.

---

### Post by Patrick83 on 2007-02-28
When i put them in the right order, i don't get the error 22, but instead of this i get the error 17. Which should be logical because for some reason my latest added hdd is now hda, (sata1) When i try to put de disk were Ubuntu is installed on to the top, I receive an "no operation systeem has installed/detected".

---

### Post by rsambuca on 2007-02-28
What was the order when you first checked?

---

### Post by Patrick83 on 2007-02-28
Normal is sata 2 (hdb)
sata 4 (hdc)
sata 1 (hda)

Could it be that my sata1 hdd has taken over the hda from sata2. And that the grub is looking for hda but it has been changed to hdb??

---

### Post by rsambuca on 2007-02-28
I think I would leave your bios order the way it was, but change the device map entries to correspond.  ie.
hd0 - Sata2
hd1 - Sata4
hd2 - Sata1

Then from the live CD, enter a terminal and try sudo grub-install

---

### Post by tgalati4 on 2007-03-01
I am so confused!

Well at least you have more information to work from.  It looks like when you did a "fixmbr" it simply overwrote the Grub bootloader on the default boot partition.  

This is a common noob error--thinking that Windows can fix your problems when it really makes it worse.  Then you have to use Linux to fix it!

As rsambuca suggests, reinstalling grub should take care of it.  You could also phyically switch cables to get the correct boot drive.

An alternative, that I have used when the MBR gets hopelessly screwed up:

Make yourself a grub floppy.  That way it will always boot to floppy when the floppy is installed and you will have a working grub system that you can experiment with.  The menu.lst file is also kept on the floppy so you can edit it.

This way Windows always has an intact MBR (and it thinks it is still king) and you can boot to grub via floppy to get to your other 7 Linux distros.

Search grub floppy in the forums or ubuntu wiki to find the grub floppy tutorial.

Good luck.

---

