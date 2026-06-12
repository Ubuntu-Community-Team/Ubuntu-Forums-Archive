---
title: "Setting up dual boot w/ ubuntu and XP??"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by unbwogable on 2008-03-02
I've installed Ubuntu with two partitions on the same drive, but the only way I can get a boot menu is to insert the Ubuntu CD and tell it to boot from the first hard disk. Is there a better way? (Newb question)

---

### Post by tyler_roach on 2008-03-02
Can you give us more information about your problem, such as how many hard drives you have, and what happens when you boot without the CD -- is there an error message, nothing at all, or does it boot into the OS without showing the menu?

---

### Post by kdarkentity on 2008-03-02
so you have a dual boot set-up on your computer of windows xp and ubuntu but you can't boot into either without the live cd?

---

### Post by unbwogable on 2008-03-02
Exactly. Help!!

---

### Post by tyler_roach on 2008-03-02
What exactly happens when you try to boot without the CD?

---

### Post by unbwogable on 2008-03-02
It boots directly into Ubuntu without giving me an option. I DO, however, get a 10 second period where my monitor gives me an 'analog video: cannot display' error, before it boots into Ubuntu...

---

### Post by tyler_roach on 2008-03-02
could you post the contents of /boot/grub/menu.lst   here?

Go to a command line, and enter

gedit /boot/grub/menu.lst

then paste the contents of that text file here.

---

### Post by johnbouma on 2008-03-02
also, how many hdd's do you have on your system -> and what order are they set up to boot in the bios.

---

### Post by unbwogable on 2008-03-02
I will post that, but I'm in Windows at the moment.

Just one drive. I cloned it onto another as a backup, though, so the backup contains just my original Windows installation (NOT connected at the moment).

The BIOS is set to boot from CD then HDD, in that order

---

### Post by tyler_roach on 2008-03-02
This is a temporary solution, but try hitting ESC as the computer boots.

---

### Post by unbwogable on 2008-03-02
> **tyler_roach said:**
> could you post the contents of /boot/grub/menu.lst   here?

Go to a command line, and enter

gedit /boot/grub/menu.lst

then paste the contents of that text file here.

As promised:
Begin --->
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
# kopt=root=UUID=28c32017-88fd-4598-9b87-04ea888665bb ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=28c32017-88fd-4598-9b87-04ea888665bb ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=28c32017-88fd-4598-9b87-04ea888665bb ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by confused57 on 2008-03-02
You could try removing the quiet & splash kernel options:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
remove the kernel options quiet & splash...quit & save

---

### Post by tyler_roach on 2008-03-02
What is your video card/monitor setup like?

---

### Post by unbwogable on 2008-03-03
ATi All-in-wonder-pro 256MB and a Dell 15" LCD (not exactly sure the model, too dark to look :-))

---

### Post by unbwogable on 2008-03-03
> **tyler_roach said:**
> This is a temporary solution, but try hitting ESC as the computer boots.

I get nothing.... lol.. it just boots normally

---

### Post by unbwogable on 2008-03-03
> **confused57 said:**
> You could try removing the quiet & splash kernel options:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
remove the kernel options quiet & splash...quit & save

That just managed to reset my color scheme :-)

---

### Post by tyler_roach on 2008-03-03
Your grub configuration is fine, it just seems that the menu isn't displaying on your monitor for some reason, and you get this error message instead. The menu times out after ten seconds, and then you get the boot splash.

Can you try switching the monitor cables from DVI to VGA, or vice versa, and see what results?

---

### Post by unbwogable on 2008-03-03
Would it work with TV out? How can I change this setting, as my video card doesn't have DVI outputs

---

### Post by tyler_roach on 2008-03-05
There are two other things you can try:

- Some LCD's have an autoconfig button on the front; try pressing that as the computer is booting.
-When the error message displays, just press "down" three times, and then "enter" if you want to boot into windows.

Beyond that, I'm at a loss.

---

