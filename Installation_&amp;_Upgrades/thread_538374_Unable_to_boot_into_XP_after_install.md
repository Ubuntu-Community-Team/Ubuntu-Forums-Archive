---
title: "Unable to boot into XP after install"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by Chayoss on 2007-08-29
I just installed Ubuntu onto a slave hard drive of mine, and I now I can't boot into XP. I had XP on my master hard drive working fine before the install. After installing from the CD, I was prompted to reboot. I did so, but received a 'Operating System Initialization Error' right after the DMI Verification. This is the bit where it normally does the OS initialization, I figure. I went into BIOS and set it to boot from my slave drive first. I got a GRUB error 21 - hard drive not found, I found out. 

I pulled out the slave drive and used my XP alone, received the same error no matter how I set the cables/BIOS. I tried every conceivable combination. The HDD with XP simply won't boot. I've been in the advanced BIOS (the hidden one with Gigabyte mobos) to see if anything could help me, but there was nothing. Every combination would lead to either a GRUB error 21 or an OS initialization failure. 

So, I'm running Ubuntu right now off of my slave drive (now master by cable, though the jumper is still set to slave and not cable select) with my XP drive connected as slave by cable (though master by jumper - it wouldn't work the other way around). I can see and mount the XP drive and all files are intact. It's not a HDD problem, I think, seeing as both work.

One noteworthy comment is that I have had problems in the past with the Ubuntu HDD. It crashed once after attempting to system restore XP, but worked fine as a slave after I got a new HDD, with all files still intact. It had a partition on it that I removed via Windows disk manager and then I formatted it NTFS before installing Ubuntu.
Also, I checksummed my download and verified my CD before install.

Can you please help me get my dual boot working? Let me know if you need more information.
Thanks!

---

### Post by Pumalite on 2007-08-29
Post:
sudo fdisk -l (small L)
cat /boot/grub/menu.lst

---

### Post by Chayoss on 2007-08-29
I can't log in as root.
At the terminal, I wrote what you said.
It asks me for a password (I assume root).
I try and type in the password, but the characters don't come up. For example, I type '123456', and the screen is exactly identical as if I had not typed in anything at all. Each character resets the cursor's blinking so that it the blinking rectangle is invisible, but no letters, stars, or movement is visible.
Typing it in anyway and pressing enter results in a 'Password incorrect, try again' message - as if I had entered a blank password.
Attempting to paste it in after copying the password from a text editor doesn't insert anything and doesn't work if I try and use that.

---

### Post by merlinus on 2007-08-29
Typing your password in a terminal is different from the login screen.  Nothing shows, but what you type is recorded.

So when prompted, try typing in your user password, and then press Enter.

-merlin

---

### Post by Chayoss on 2007-08-30
> **merlinus said:**
> Typing your password in a terminal is different from the login screen.  Nothing shows, but what you type is recorded.

So when prompted, try typing in your user password, and then press Enter.

-merlin

Ah, thanks.
Here's fdisk:
```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16709   134215011    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

```

And here's menu.lst
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
# kopt=root=UUID=e427c703-1f35-43c1-be9f-ec67e6f4db14 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e427c703-1f35-43c1-be9f-ec67e6f4db14 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e427c703-1f35-43c1-be9f-ec67e6f4db14 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Pumalite on 2007-08-30
We'll edit your menu.lst. First backup:
cp /boot/grub/menu.lst /boot/grub/menu.lst.back
gksudo gedit /boot/grub/menu.lst
Add at the end: 

title         Windows 95/98/NT/2000
rootnoverify          (hd0,0)
makeactive
chainloader   +1

Save and beboot

---

### Post by Chayoss on 2007-08-30
> **Pumalite said:**
> We'll edit your menu.lst. First backup:
cp /boot/grub/menu.lst /boot/grub/menu.lst.back
gksudo gedit /boot/grub/menu.lst
Add at the end: 

title         Windows 95/98/NT/2000
rootnoverify          (hd0,0)
makeactive
chainloader   +1

Save and beboot

Thank you very much, that worked.

---

### Post by Pumalite on 2007-08-30
You are welcome. Glad it worked for you.

---

