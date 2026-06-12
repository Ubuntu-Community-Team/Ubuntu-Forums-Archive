---
title: "numerous installation problems"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by rosspoko on 2007-09-15
I have an hp tx1000 laptop with vista, and have been trying to install linux on it.  I shrunk my windows partition by 20 gigs to make space.  I started with redhat, but that didn't even support my hard drive, so next I tried ubuntu.  My dad had an old ubuntu 5.10 cd so I tried to install from that.  It created a partition in the empty space on my hard drive, and I made no changes to my windows partition.  The first part of the install went well, but when I restarted the computer to finish the install, it told me that it was having problems synching with apic or something.  Worse, when I went into the menu in grub, windows wasn't an option.  I have been trying all kinds of  things to try to get windows back and to hopefully finish installing ubuntu.  I bought Partition commander and tried t get windows back, but apparently my c drive is no longer designated as c, and when I try to mount it, it just tells me that it can't.  Also, I downloaded the newest version of ubuntu and tried to install that, but it freezes at various places whenever I try.  I have also tried installing ubuntu 5.10 a few more times, and sometimes it gets past the apic problem, sometimes it doesn't. When it does, it continues installing for a while and then freezes when it does something involving bluetooth drivers.  so right now I have a computer with no working operating systems.

---

### Post by Pumalite on 2007-09-15
When starting the Live CD, press F6 and add the following to boot options:
doscsi noapic

---

### Post by rosspoko on 2007-09-15
Thanks.  That got ubuntu working.  Now I just need to get windows back, but I guess this is the wrong forum for that

---

### Post by Pumalite on 2007-09-15
No, you are in the right place. Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by rosspoko on 2007-09-15
Those two commands gave a rather long list of information, and the linux computer isn't on the internet, so I can't just copy/paste it all.  But to summarize the relevant-looking parts of what it says, I have 4 partitions: 
the first is my windows partition, /dev/sda1, and is also the boot partition.  the filesystem is HPFS/NTFS and the id number is 7.

/dev/sda2 is a recovery partition that HP uses instead of recovery disks.  its filesystem is "Hidden HPFS/NTFS" and its id is 17

/dev/sda3 is the swap partition: filesystem: "Linux swap / Solaris", id: 82

/dev/sda4 s where linux is: filesystem: "Linux", id: 83

quite far down in the list info that came out of cat /boot/grub/menu.lst, it lists different boot options: 

title: Ubuntu, kernel 2.2.20-15-generic
root: (hd0,3)
kernel: /boot/vmlinuz-2.6.20-15-generic root=UUID=a5ee4838-c148-4edd-872a-260a37ed2ed ro single quiet splash doscsi noapic
initrid: /boot/initrid.img-2.6.20-15-generic
quiet
savedefault

It then has a similar looking entry for recovery mode and a memtest86+ entry that has /boot/memtest86+.bin as the kernel

then it lists windows:

title: Windows Vista/Longhorn (loader)
root: (hd0, 0)
savedefault
makeactive
chainloader: +1

It then lists windows again, but I think its referring to the recovery partition.  When I restart the computer, windows is now an option in grub, but selecting it goes to a screen that says that the Windows Boot failed because it can't find a program

---

### Post by Pumalite on 2007-09-15
I think Grub is being fooled by that recovery partition. Backup your menu.lst and then edit removing the entry for the recovery partition.

---

### Post by rosspoko on 2007-09-15
It says that I don't have permission to edit it

---

### Post by Pumalite on 2007-09-15
gksudo gedit /boot/grub/menu.lst

---

### Post by rosspoko on 2007-09-15
That didn't work, but it did make it so that windows is only listed on the grub menu once.  It was on there twice before.

---

### Post by Pumalite on 2007-09-15
This is weird. What's your status now?. Can you boot to either OS?

---

### Post by rosspoko on 2007-09-15
linux still works fine.  I hope I didn't accidently delete part of windows somewhere along the way.  Also, whenever I would use partition commander, it lists the volume of my windows partition as *:  I'm pretty sure its supposed to be c: since it was the c drive in windows.  The d drive, which is the hp recovery partition, is labeled as volume d:.  Every time I try to mount the windows partition at c, or anything else for that matter, it tells me that it can't mount t and that it is an unknown partition type.

---

### Post by Pumalite on 2007-09-15
Get a Knoppix: [http://www.knoppix.org/](http://www.knoppix.org/) and explore your system. See if Windows still exists.

---

### Post by rosspoko on 2007-09-15
I can see my windows partition from ubuntu.  It seems intact, it has the WINDOWS folder and I even found the file that I'm told is missing when I try to boot it up.  So it definitely still exists

---

### Post by Pumalite on 2007-09-15
Try:
sudo chmod 777 /boot/grub/menu.lst
gksudo gedit /boot/grub/menu.lst
Copy and paste the contents here.

---

### Post by rosspoko on 2007-09-15
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
# kopt=root=UUID=a5ee4838-c148-4edd-872a-2640a37ed2ed ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# defoptions=quiet splash doscsi noapic

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a5ee4838-c148-4edd-872a-2640a37ed2ed ro quiet splash doscsi noapic
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a5ee4838-c148-4edd-872a-2640a37ed2ed ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Pumalite on 2007-09-15
I guess you cannot boot Windows yet. Try this: change 'root (hd0,0)' to 'rootnoverify (hd0,0)' in the Windows entry. I'm assuming you have only one hard drive.

---

### Post by rosspoko on 2007-09-15
That didn't help.

I gtg.  Thank you so much for all of your help.  I'll be trying again tomorrow.

---

### Post by Pumalite on 2007-09-15
OK. You are welcome. You can still re-install Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by dreadlocks1221 on 2007-09-16
Ive got a similar problem with blue tooth I managed to install Ubuntu with the alternate installation cd and now when I boot it says starting bluetooth services and hangs there, I added the doscsi noapic to my boot commands and the only new thing that comes up is failed startx (a problem with the regular instalation cd) 


My HP specs are

Core 2 T7300 Nvidia 8400m GS
200 GB hard Drive
4GB Ram
Wireless N and Bluetooth
Vista Ultimate 64bit

---

