---
title: "disable grub automagic"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by michalski7777 on 2007-11-16
hey i have grub and ubuntu 7.10 and need to know how to disable the automagic option in grub, so i can actually give different titles to the boot menu items thingy....  :P

basicly i want to rename the ubuntu 7.10 on the boot menu

heres my config:

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
password <im smart enough to remove this prior to posting>

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
# kopt=root=UUID=39a81e48-7d84-45e9-820d-dd5ce40f243c ro

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

splashimage=(hd0,2)/boot/grub/splash.xpm.gz

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=39a81e48-7d84-45e9-820d-dd5ce40f243c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=39a81e48-7d84-45e9-820d-dd5ce40f243c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		---
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		BASELINE/XSANF
root		(hd0,3)
makeactive
chainloader	+1
```

---

### Post by logos34 on 2007-11-16
I believe you can change the 'title' line and it will persist through the next kernel update.....but I could be wrong because to tell the truth I've never bothered to rename any of the kernels.  AFAIK it's the boot options you have to 'lock' if you don't want the automagic feature to change them at kernel update time.

gksudo gedit /boot/grub/menu.lst

edit, save and close.

---

### Post by michalski7777 on 2007-11-16
didnt work :S

---

### Post by logos34 on 2007-11-16
> **michalski7777 said:**
> didnt work :S

so, you changed this line

title		Ubuntu 7.10, kernel 2.6.22-14-generic

rebooted and the new name doesn't show up on the screen?

---

### Post by michalski7777 on 2007-11-16
i did that and then went to console and typed 

sudo update-grub

is that whats changing it?
do i need to type it after changing the file?

---

### Post by meierfra on 2007-11-16
Check out this link:  [Hermanzone]("http://users.bigpond.net.au/hermanzone/p15.htm#Edit_usrsbinupdate-grub")

---

### Post by meierfra on 2007-11-16
> did that and then went to console and typed

sudo update-grub

is that whats changing it?
do i need to type it after changing the file?
__________________


You don't need to run "sudo update-grub". Editing menu.lst is all it takes. 

But  "update-grub"  will be run  during the next kernel upgrade. The link in my previous post shows you how to change the titles "update-grub" uses.

---

### Post by logos34 on 2007-11-16
> **meierfra said:**
> Check out this link:  [Hermanzone]("http://users.bigpond.net.au/hermanzone/p15.htm#Edit_usrsbinupdate-grub")

hmm...so that's how you do it.  

But when you upgrade the kernel, the previous version remains in the automagic section, the new one merely becomes first in the list (default).  So will the Grub menu screen show both kernels with the same name, e.g. 'Ubuntu Gutsy'? (unless of course you comment the previous kernel(s) out).

---

### Post by Herman on 2007-11-16
:) Hello everyone,
```
hmm...so that's how you do it.  
```Actually, I have a slightly better way now, it's faster and easier to use the text editor nano instead of good old gedit. I just updated that link, so take another look now. :)

I can't understand why anyone would need to edit that now if they have Gutsy Gibbon though, for earlier versions it was nice to make the correct title appear in our GRUB menus, but I thought that was fixed now in Gutsy.
...Unless someone wants to put their system's hostname in there instead, I guess that might be a good idea for some people, especially if they have more than one Ubuntu in the same computer like I do.

Can anyone who has Kubuntu or Xubuntu or some other *buntu tell me if thier boot entries have the title 'Kubuntu', Xubuntu'  or whatever is applicable now?
I do know it at least mine tells me it's Ubuntu 7.10 now, I am hoping it also describes what *buntu we installed, but maybe I'm wrong. Thanks.

>  But when you upgrade the kernel, the previous version remains in the automagic section, the new one merely becomes first in the list (default). So will the Grub menu screen show both kernels with the same name, e.g. 'Ubuntu Gutsy'? (unless of course you comment the previous kernel(s) out). No, you would still need to edit that one yourself if you want to or comment it out like you said. It's only the new changes that get written the way specified in the update-grub file. At least when I tested it that's what happened.

Regards, Herman :)

---

### Post by jetsam on 2007-11-16
> Can anyone who has Kubuntu or Xubuntu or some other *buntu tell me if thier boot entries have the title 'Kubuntu', Xubuntu' or whatever is applicable now?

...I have a fairly new Xubuntu 7.10 install.  The defauls grub setup seems to be to bypass the menu entirely unless you hit esc.  If you hit escape, the menu reads:
```
Ubuntu 7.10, kernal 2.6.22-14-generic
Ubuntu 7.10, kernal 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+
```

I suppose it should read Xubuntu, but it seems a minor issue because you seldom see it anyway.

---

### Post by Herman on 2007-11-16
Oh, okay, thank you there, jetsam, that's exactly what I wanted to know. So there will still be a few people who will want to edit their /usr/sbin update-grub scripts then, so maybe I better test that myself a little and make sure I know how to edit the new gutsy version and make it say what *buntu it is then, if that's still possible. :)
Thanks.

Regards, Herman :)

---

