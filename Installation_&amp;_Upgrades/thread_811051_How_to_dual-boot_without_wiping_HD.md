---
title: "How to dual-boot without wiping HD??"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by TheDriller on 2008-05-28
hi,
i formatted my hard drive and installed Ubuntu Studio about 3 weeks ago and quite like it.
but i'm getting sick of trying to force my Firewire soundcard to work with it so i need to set up an XP partition to get on with recording.

Question: how would i go about setting up a new XP partition without having to format the hard drive?

i dont want to have to format the drive, install XP, spend a week setting it up, install Ubuntu, spend a month setting it up.. etc...

also, how can i find out how much space my Ubuntu Studio instalation is using up and also condense it down to free up space on the hard disk?

thanks

---

### Post by iaculallad on 2008-05-28
> **TheDriller said:**
> hi,
i formatted my hard drive and installed Ubuntu Studio about 3 weeks ago and quite like it.
but i'm getting sick of trying to force my Firewire soundcard to work with it so i need to set up an XP partition to get on with recording.

Question: how would i go about setting up a new XP partition without having to format the hard drive?

i dont want to have to format the drive, install XP, spend a week setting it up, install Ubuntu, spend a month setting it up.. etc...

also, how can i find out how much space my Ubuntu Studio instalation is using up and also condense it down to free up space on the hard disk?

thanks

Before trying to intall windoze xp, try reading this [page]("https://help.ubuntu.com/community/UbuntuStudioPreparation") if it could help you setup your firewire soundcard.

---

### Post by TheDriller on 2008-05-28
> **iaculallad said:**
> Before trying to intall windoze xp, try reading this [page]("https://help.ubuntu.com/community/UbuntuStudioPreparation") if it could help you setup your firewire soundcard.

yes, i've been through it, i got it mostly working, the audio goes in to ardour fine but the headphone output doesnt work., no solution so far.

anyway, im tired of hanging around and i just want to get back to proper recording. i want to still keep my Ubuntu Studio installation, hence why i dont want to format the HD,

cheers:guitar:

---

### Post by zvacet on 2008-05-29
Download [Gparted live CD.]("http://gparted.sourceforge.net/") Boot with it and shrink your Ubuntu partition and format free space as NTFS.On that partition install Windows,and [reinstall grub.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

### Post by TheDriller on 2008-05-29
actually, now that i think about it, would i be better off just using VirtualBox?

i want to use the XP for music production, would VirtualBox be ok for this or is there a performance cap?

thanks lads, ye are a great help as always :)

---

### Post by EndPerform on 2008-05-29
> **TheDriller said:**
> actually, now that i think about it, would i be better off just using VirtualBox?

i want to use the XP for music production, would VirtualBox be ok for this or is there a performance cap?

thanks lads, ye are a great help as always :)

There's always going to be some form of performance hit using virtualization.  That being said, though, what are the specs of your machine?  Depending on what you have, you might be able to get it running fine.

---

### Post by zvacet on 2008-05-29
Using any virtualization program you have to share ram between your OS and virtual machine.That can make virtual machine slow,but if you have enugh ram that will not be problem.

---

### Post by TheDriller on 2008-05-31
> **EndPerform said:**
> There's always going to be some form of performance hit using virtualization.  That being said, though, what are the specs of your machine?  Depending on what you have, you might be able to get it running fine.

I have an AMD Turion 64 (I think its the equivilant of a Pentium 4) and 2Gigs of RAM.

---

### Post by TheDriller on 2008-06-02
> **zvacet said:**
> Download [Gparted live CD.]("http://gparted.sourceforge.net/") Boot with it and shrink your Ubuntu partition and format free space as NTFS.On that partition install Windows,and [reinstall grub.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

hi,
now that i have re-installed grub, my machine wont allow me to boot into my windows XP partition, here is the whole story:

-I had Ubuntu Studio intalled but wanted to dualboot XP

-I used GParted Live CD to resize and create a partition for windows

-I insalled XP on this new partition, at this time, the machine would only boot into XP for me.

-I then did this "Re-Install GRUB" thing ( with the hd number coming up as hd0,0)

-Now my machine only boots into Ubuntu Studio

i want to have a choice at startup between the two operating systems

how can i fix this??

my grub menu looks like:::::

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
# kopt=root=UUID=77c188a4-a9ef-460e-ac55-8b00c0290d94 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=77c188a4-a9ef-460e-ac55-8b00c0290d94 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=77c188a4-a9ef-460e-ac55-8b00c0290d94 ro single
initrd		/boot/initrd.img-2.6.24-16-rt

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

