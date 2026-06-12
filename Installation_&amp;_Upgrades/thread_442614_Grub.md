---
title: "Grub"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by Psicolonia on 2007-05-13
Hi everyone i've i nstalled ubuntu and replaced grub with suse's gfx. it's prettier now only... It ain't silent anymore. Usually you just press enter and it shows up "Starting" and the usplash right after. Same when i boot windows. However, scince i've done the trade (and did mess my computer really bad, had to re-install grub and everything) it shows a dump with the boot lines. Like:
```

root hdxxx
chainloader +a
boot
```

is there a way to get it clean again. All my choices on grub menu.lst have quiet on them.

:(

---

### Post by dannyboy79 on 2007-05-14
> **Psicolonia said:**
> Hi everyone i've i nstalled ubuntu and replaced grub with suse's gfx. it's prettier now only... It ain't silent anymore. Usually you just press enter and it shows up "Starting" and the usplash right after. Same when i boot windows. However, scince i've done the trade (and did mess my computer really bad, had to re-install grub and everything) it shows a dump with the boot lines. Like:
```

root hdxxx
chainloader +a
boot
```

is there a way to get it clean again. All my choices on grub menu.lst have quiet on them.

:(

I consider myself pretty knowledgable and I am part of the unanswered team here but I am not sure what you want. If you're saying that you replaced the grub menu with a graphical background at one point, and then you messed up your grub and had to reinstall grub, then why don't you just do what you did before again? Also, if you have the words quite and splash on your boot line, than you shouldn't see any dumping of text and u should see the boot splash. if you'd like anymore help, please be a little more specific.

---

### Post by Psicolonia on 2007-05-15
well... normally grub just says something like "starting..." and then the usplash comes up. If you are booting windows it shows "starting..." and then the windows logo comes up.

however scince i've made the change i get something like:

Starting...
root hdx
chainloader +1
boot

for a second. and even worst booting ubuntu... before the usplash.

This happened after installing grub. so even if i do it again... i'll get the same problem... :(

---

### Post by dannyboy79 on 2007-05-15
please post your /boot/grub/menu.lst so that I can see what may be causing this cause you're right, my latest fiesty install only states, "Starting......." and then the usplash shows up.

---

### Post by Psicolonia on 2007-05-15
Yes exactly!

Here's my menu-lst:

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
gfxmenu /boot/grub/message.new
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		60

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=74ace9fa-0a1f-422b-b145-1a240e6f24c0 ro

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

title		Ubuntu
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=74ace9fa-0a1f-422b-b145-1a240e6f24c0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
#savedefault

title		Ubuntu (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=74ace9fa-0a1f-422b-b145-1a240e6f24c0 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu (memtest86+)
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		----------------------
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional
root		(hd0,0)
#savedefault
makeactive
chainloader	+1


```

Thanks for helping out!

---

### Post by dannyboy79 on 2007-05-15
well it looks a little different but I can't seem to locate anything that sticks out except for these few things:

gfxmenu /boot/grub/message.new

I have attached mine for ya, maybe jusrt copy and paste it, except make my entries into yours and then add the windows entry at the bottom. then make sure that works, then do your change as far as a pretty grub menu. good luck.

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
timeout		3

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
# kopt=root=UUID=8c21ad7f-0448-4163-a347-f5a30902d1b0 ro

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
# defoptions=quiet splash noapic nolapic

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
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=8c21ad7f-0448-4163-a347-f5a30902d1b0 ro quiet splash noapic nolapic
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=8c21ad7f-0448-4163-a347-f5a30902d1b0 ro single noapic nolapic
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Psicolonia on 2007-05-15
nope :( nothing... maybe grub bfx boot is just different... i don't know... thanks for the help. can u tell me, however how to stop the timeout? I've tried timeout = 0 wich ofcourse skiped grub. And tried do comment default line. It get's a default of it's own... wierd...

Thank you one more time!

---

### Post by dannyboy79 on 2007-05-15
it sounds like you want your cimputer to turn on and have the grub menu just sitting there? if this is true than I would change the hiddenmenu option and also check out the gnu grub manual regarding the timeout as I have mine set at 1 second.
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

