---
title: "Unable to install ... kernel panic"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by slacker9876 on 2006-07-10
I have not been able to get Kubuntu to boot off the Live CD or Live DVD, I have tried the 1386 disc as well as the x86_64 disc. I have a Compaq Presario V2000 laptop. The "official" model number is V2104CL.

I am equipped with a Turion ML-32 processor, 2GB of RAM and the ATI Radeon Express 200M. I have read many threads here stating NOT to upgrade past the 8.24 driver series, but do not know how I would "change" this from an ISO.

I am posting from Suse 10.1 which seems to be OK, but I am running Kubuntu on my desktop, an EMT64 processor that kicks butt. 

I have tried the noapic, nolapic and vga=771 options in both normal and graphics safe boot modes. I am not knowledgeable of other boot parameters for installation and appear to be stuck. Would love some feedback or ideas.

Thank you

](*,)

---

### Post by raldz on 2006-07-11
try to add acpi=off along with noapic nolapic and vga=771.. I have this Kernel panic issue with a KM400 motherboard, and resolved it by turning acpi off..

---

### Post by slacker9876 on 2006-07-11
That did take me past kernel panic, thanks for the tip! However, I am still stuck, the GUI will not boot, therefore allowing installation. I am sure the Radeon 200M is still tied into the issue somewhere but not sure where to go from here. I will provide the xx.xxxx number where it locks up if that will help. are there other parameters for VGA=xxx?

Thanks!

---

### Post by raldz on 2006-07-12
You may try to download the "alternate" CD-ISO from Ubuntu's download page, this will help you install Ubuntu in text mode.. after installing, you have to edit GRUB to add "acpi=off" to the boot parameters.. after this, you may have to configure xserver-xorg or try to install the ATI Legacy drivers manually to enable GUI.. goodluck..

---

### Post by jrleighton on 2006-07-12
When you say "add acpi=off" .... is this in grub ? how exactly should grub be edited to add this ?  thanks

---

### Post by raldz on 2006-07-13
Here is how my GRUB looks like with acpi=off

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro noapic nolapic

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro noapic nolapic quiet splash acpi=off
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro noapic nolapic single acpi=off
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		 
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		_
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

if you will check the line where you could find "kernel" I appended "acpi=off" at the end..

here is a guide to edit grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by slacker9876 on 2006-07-15
I did also download the DVD which has the text install mode but there are still just sour grapes. I know the ATI driver is the corresponding issue and seemed to remember using a generic VESA driver in the past on another ATI hard-wired platform. I would *really* like to get this running so I hope you bag of tricks is not empty yet! ](*,) 

Also on another note I have seen that file sharing while enabled is not adjustable under the networking screens. I have not searched the fourms yet but I was wondering if you may already know how to utilize the advanced features. When I select administrator mode and enter my password, all the options are still greyed out.

I also would like to add that K/Ubuntu is the most kick *** distro I have seen, this is why I am anxious to get moved!!!

---

### Post by slacker9876 on 2006-07-15
OMG ... I guess it would have helped to install the NFS and Samba server packages ... sorry for being a dunce on that one!

---

