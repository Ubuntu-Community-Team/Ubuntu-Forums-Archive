---
title: "Can't get XP to boot"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by swati on 2007-09-18
Okay, So I Installed ubuntu.. Everything went perfectly. I already had a partition and used Partition Magic to indicate that I'll be installing another operating system.

I rebooted my computer and couldn't get into XP. From fdisk discovered that my XP partition was showing up as "Hidden." I used grub unhide to make it unhidden. Now it's marked as active and shows up fine in the fdisk:

-----------------------------------------------------------------------------------------------------------
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+   2  XENIX root
/dev/sda2   *         785       18584   142978500    7  HPFS/NTFS
/dev/sda3           18846       24321    43985970   83  Linux
/dev/sda4           18585       18845     2096482+  82  Linux swap / Solaris

Partition table entries are not in disk order
-----------------------------------------------------------------------------------------------------------

It's the second one that has majority of my files on it. It shows up fine on the grub screen when I am rebooting, but when I pick it and press enter, the computer just restarts. I get no Windows logo. No nothing. It just reboots.

Any advice? I am completely lost and frustrated :(

---

### Post by Pumalite on 2007-09-18
Post from Terminal:
cat /boot/grub/menu.lst

---

### Post by swati on 2007-09-18
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
# kopt=root=/dev/sda3 ro

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

title           Ubuntu, kernel 2.6.15-29-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-29-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-29-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-29-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-29-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Recovery Stuff
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by CowzRule on 2007-09-18
Sorry this isn't help for your problem, but you can clean up your menu.lst by changing the follow option
```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all
```Change the last line to read ```
# howmany=1
```
The in the terminal type ```
sudo update-grub
```That will stop those old kernal entries from showing.

---

### Post by Pumalite on 2007-09-18
Backup first: sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back, then:
gksudo gedit /boot/grub/menu.lst
Erase this from your menu.lst:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Recovery Stuff
root (hd0,0)
savedefault
makeactive
chainloader +1

Save, exit and reboot. I think Grub is being fooled by this entry. Let's hope Grub didn't install itself there. Let's see what happens.

---

### Post by swati on 2007-09-18
Just tried that. Didn't work :'( It removed the first 'Recovery' option from the selection screen. I clicked on the XP one, and it just restarted the machine.

---

### Post by CowzRule on 2007-09-18
Is the windows file "ntldr" located on /dev/sda2 or /dev/sda1
If it's located on /dev/sda1 change
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
makeactive
chainloader +1
```
to
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1
```

---

### Post by swati on 2007-09-18
I don't know what ntldr is persay, but everything to do with the OS is on sda2. sda1 is the recovery stuff.

I tried booting the recovery stuff. Gives me a blue screen saying fatal error. Don't know what happened there, or how that's supposed to work. Haven't had to use recovery in the past 2 years.

---

### Post by Pumalite on 2007-09-18
That's probably right. That sda1 'recovery' partition is the way Micro%&$ wants to prevent their users from installing any other OS.

---

### Post by swati on 2007-09-18
> **Pumalite said:**
> That's probably right. That sda1 'recovery' partition is the way Micro%&$ wants to prevent their users from installing any other OS.

Anyyy other suggestions/things I should try? Could this have to do something with mounting. I Don't know if I mounted stuff correctly during installation.

---

### Post by Pumalite on 2007-09-18
Did you try CowzRule suggestion of editing your menu.lst and changing the Windows entry in the 'root' line from (hd0,1) to (hd0,0)?

---

### Post by swati on 2007-09-18
Yes, that doesn't work. That gives me the same blue screen I got when I was trying to boot 'Recovery'

---

### Post by Pumalite on 2007-09-18
One last try: change 'root' for 'rootnoverify' and lets see.

---

### Post by swati on 2007-09-18
I tried that as well, didn't work. 

Last try...does that mean there is nothing else I can do?

---

### Post by Pumalite on 2007-09-18
I ran out of ideas, but there is people in this forum that knows a lot more than I. Someone will chime in. Good luck. BTW, you can restore XP by plugging in your install CD, hitting 'r' for Recovery>FIXMBR>FIXBOOT.

---

### Post by swati on 2007-09-18
The computer didn't come with a CD :( It came with the recovery partition, which is now corrupted for some reason. :'( :'(

---

### Post by Pumalite on 2007-09-18
You can get an OEM XP CD for 10 bucks and use the serial # stamped in your machine. They should give you one in the first place.

---

### Post by Pumalite on 2007-09-18
I forgot to tell you that you can get Super Grub and boot either OS:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

(it's free)

---

### Post by swati on 2007-09-18
Okay, I tried that too. 

I tried many options, including uninstalling grub (fixmbr for windows)-- that didn't work. It just sent my computer into an infinite loop where it kept rebooting. Nothing ever came up. I also tried activating partitions, booting just windows, booting a partition...nothing.

I am completely at loss here and frustrated. Can anyone help?

---

### Post by Pumalite on 2007-09-18
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

---

