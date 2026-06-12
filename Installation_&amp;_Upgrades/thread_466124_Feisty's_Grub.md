---
title: "Feisty's Grub"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by amdfanboy on 2007-06-06
i already installed feisty on my PC...

since im still a beginner...

i would like to ask on how can i disable GRUB and revert to DOS as my boot loader?

---

### Post by merlinus on 2007-06-06
More info would be helpful.  For example, are you dual-booting with windows?  Do you want to be able to choose between windows and ubuntu?

-merlin

---

### Post by Elrohir on 2007-06-06
"it's all about the flags, baby!"

not sure of this one, never tried it myself, but you can do this:

pop the Ubuntu live cd, on terminal```
sudo gparted
```and deactivate boot flag on the root partition and activate it on Windows partition... good luck!

---

### Post by Jose Catre-Vandis on 2007-06-06
Why?

Grub is so much easier, once you figure out how it works. on my dual boot machines I always opt for grub over any other solution. Are you having trouble configuring?

---

### Post by logos34 on 2007-06-06
> i would like to ask on how can i disable GRUB and revert to DOS as my boot loader?

There's a way, but why?  Grub is so versatile, heck of a lot better than windows ntldr...If you don't want to see it at startup and want to go by default into windows, you can can set that and even lower the timout so that you won't even see grub menu unless you hit a key (i.e. in order to boot ubuntu).

---

### Post by Mark Phelps on 2007-06-06
The specific details depend on whether or not you have a dual-boot situation, and if so, whether the Windows OS is XP or Vista.

I'm triple-booting with Xp, Vista, and Feisty -- and have spent weeks trying to get the Vista boot loader to incorporate Feisty -- with absolutely no success.  So, I boot into Grub, and in the event that I still want to get into Windows, have that as an entry in the Grub menu, select that, and then select the specific Windows version I want.  Clumsy, but it works.

If you're dual-booting with Vista, there are two different third-party windows-based products, both of which should work: EasyBCD and VistaBootPro.  They're both available for free for download (google for them). If what you want to do is boot Feisty from Windows, you're welcome to try either of these.  Both products have support forums where you'll see lots of postings about them working and, in my case, not working.

---

### Post by amdfanboy on 2007-06-06
sorry for not providing complete information regarding my system...

i'm dual booting windows xp and ubuntu linux 7.04


its just that i want windows to boot by default...because in my grub, ubuntu is on top of the list of OS's...

there's a timer there prompting for OS selection..when the timer runs out, it boots ubuntu because it's on top of the list...

i just want to put windows on top of the list so that i don't even have to press a key when it comes to that OS selection screen...

so as to provide ease of use for my family when using the computer since they don't know what to select...

i'm thinking that if that's not possible (putting windows on top of the list) i'll be shifting back to win xp bootloader....

bear with me here ^_^

---

### Post by logos34 on 2007-06-06
> i just want to put windows on top of the list so that i don't even have to press a key when it comes to that OS selection screen...

All you have to do is edit the 'default line' at the top of menu.lst to boot from windows first.  When you get to the grub menu, Windows will be highlighted and boot after the timeout.

So, for example, if windows is the fourth 'title' line without a hash mark starting from 'End defualt section', then you would change it to read 'default  3' (Grub starts counting from 0).
> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**default		3**

If unsure, post your menu.lst.

---

### Post by merlinus on 2007-06-06
gksudo gedit /boot/grub/menu.lst

Look for a line that says default

It is probably set to 0 (zero)

Then count down how many stanzas until the one for windows.

Subract one (1) from that number, and change default to it.

The options start at 0, not 1.

Then windows will boot by default.

Good luck!

-merlin

---

### Post by amdfanboy on 2007-06-07
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
# kopt=root=UUID=19907b2c-f02c-42f9-96f5-2dcf443c4a1a ro

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=19907b2c-f02c-42f9-96f5-2dcf443c4a1a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=19907b2c-f02c-42f9-96f5-2dcf443c4a1a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by amdfanboy on 2007-06-07
what should i do in order to put my win xp on top of the list?

i'm still a newbie ubuntu user ^_^

---

### Post by Elrohir on 2007-06-07
the line which says default 0 replace it with default 4... Not placing Windows on top, but making Windows the default option to boot...

---

### Post by amdfanboy on 2007-06-07
nice...managed to do it...thanks for all the help ^_^

---

### Post by Elrohir on 2007-06-07
glad to help...

---

### Post by amdfanboy on 2007-06-07
now i'm having this problem...

since i upgraded ubuntu...the GRUB now shows the old version of ubuntu and the latest version...

how can i delete the old version from the GRUB so that it does not appear when i boot up my pc...

---

### Post by logos34 on 2007-06-07
> **amdfanboy said:**
> now i'm having this problem...

since i upgraded ubuntu...the GRUB now shows the old version of ubuntu and the latest version...

how can i delete the old version from the GRUB so that it does not appear when i boot up my pc...

gksudo gedit /boot/grub/menu.lst

Comment them out by putting hash marks ('#') in front of the kernels you don't want to appear like this:

> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

**#**title		Ubuntu, kernel 2.6.17-10-generic
**#**root		(hd0,3)
**#**kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro quiet splash
**#**initrd		/boot/initrd.img-2.6.17-10-generic
**#**quiet
**#**savedefault
**#**boot

**#**title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
**#**root		(hd0,3)
**#**kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro single
**#**initrd		/boot/initrd.img-2.6.17-10-generic
**#**boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by amdfanboy on 2007-06-08
done...problem fixed ^_^

---

