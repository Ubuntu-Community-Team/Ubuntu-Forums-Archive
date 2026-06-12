---
title: "Live CD troubles"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by stroudma on 2008-04-03
i need to use live cd to re-install GRUB, which was deleted while installing vista for dual boot, the graphical menu will come up when i try but whenever i choose one of the options, it will process for a sec then the monitor will say it has no signal and turn off, it wont turn back on no matter how long i wait, i've tried a few of the different options including safe graphics mode, and all end with the same result, my theory is that it is actually running ubuntu, just minus any video output to the monitor, other people i've seen online have said that before their monitors turn off it signals that the refresh rate is out of the monitors range, so maybe thats it, either way i cant find a work around, oh and while im not 100% the live cd is good, i am pretty sure seeing as it's the same one i used the first time around about a month ago

would really appreciate any suggestions, thanks

---

### Post by Pumalite on 2008-04-03
You can use Super Grub: [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by jonwop on 2008-04-03
i think i had a similar problem with my original install. i kept trying and trying to get ubuntu installed and it would go through the motions and it would load (took about 10 mins maybe) and then the screen would go black.

so i tried again and again like 5 times power button shut down and doing it all agian.
but maybe the 6th or 7th time i just hit the power button for half a second and the screen came back up at the start of the ubuntu install. 

now i did try pressing keys on the keyboard and moving the mouse to wake up the computer but everything was running but when i hit the power button on the monitor nothing happend. i guess since the drivers hadn't been installed yet.

so try hitting the button real quick if your computer doesn't do a shut down when you press it like that and wait a few seconds and then the screen might wake up. so i hope that might help you since i think i had the same problem as you did.

lemme know how it goes cheers

---

### Post by stroudma on 2008-04-03
oh, sweet, thanks man

---

### Post by Pumalite on 2008-04-03
Good luck!

---

### Post by stroudma on 2008-04-03
huh, so Super GRUB worked, it installed GRUB but changed the boot priority of the partitions so it boots linux first, im am now on linux and need to get vista up but i think that one might be a bit easier assuming this didnt corrupt anything or upset vista's delicate sensibilities, oh and strangely enough that hit the power button thing didnt work for the live cd but did later on when the monitor cut out when ubuntu asked me to enter my password

---

### Post by Pumalite on 2008-04-03
From Ubuntu's Terminal, post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by stroudma on 2008-04-03
yea, i got into that a bit ago and i changed the delay from 3 to 15 seconds to give me time to choose vista if i wanted but the only options are ubuntu kernel, ubuntu kernel recovery and memtest... im hesitant to switch the default value to 4 (what i hear represents a second operating system) since the live cd still isnt working so im not sure how i would get back to edit all this if it screwed it up, im getting this all from another guide though, what exactly did you think i should have done in with the fdisk and menu.lst, dont suppose it could have been as simple as just type them in could it?

---

### Post by stroudma on 2008-04-03
oh, wait im retarded, did you want the output?

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cb675

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   140681204    70340571   83  Linux
/dev/sda2   *   140681205   281057174    70187985    7  HPFS/NTFS
/dev/sda3       281057175   293041664     5992245    5  Extended
/dev/sda5       281057238   293041664     5992213+  82  Linux swap / Solaris
mark@Skynet:~$ sudo fdisk -lu

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cb675

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   140681204    70340571   83  Linux
/dev/sda2   *   140681205   281057174    70187985    7  HPFS/NTFS
/dev/sda3       281057175   293041664     5992245    5  Extended
/dev/sda5       281057238   293041664     5992213+  82  Linux swap / Solaris
mark@Skynet:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         15

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
# kopt=root=UUID=4d14ac39-2508-4ce1-ad77-6611803bf4e9 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=4d14ac39-2508-4ce1-ad77-6611803bf4e9 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=4d14ac39-2508-4ce1-ad77-6611803bf4e9 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

well, kinda long but there it is, basically i dont think grub recognizes vista at all, the screenshots i have of the GRUB bootloader screen clearly shows a windows option which mine does not have, i think i might just have to start all over, reinstall vista and then go from there

---

### Post by stroudma on 2008-04-03
im in gparted and it list /dev/sda2 as a NTFS filesystem and has the boot flag which is my vista partition so it seems like everything is in order there

---

### Post by stroudma on 2008-04-03
a workaround i found is to use Super GRUB and manually choose a partition to boot windows from, this works but is a hassle and worrisome too seeing as Super GRUB cant locate windows without me finding it manually, i think vista's bootloader got jacked up at some point, im just gonna format the vista partition and reinstall everything, then try to use EasyBCD as a bootloader for both, thanks for the help, if you have any brainstorms, let me know

---

### Post by Pumalite on 2008-04-03
Did you install Ubuntu first and then Vista?

---

### Post by stroudma on 2008-04-03
yea

---

### Post by Pumalite on 2008-04-03
I cannot assure you it'll work, but lets try this:
Backup your file first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Let-'s edit:
gksudo gedit /boot/grub/menu.lst
Add this below the Debian Automagic Kernel List:
title Windows Vista
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1
Save, exit and reboot.

---

### Post by stroudma on 2008-04-03
yea, alright, it's reinstalling vista right now, hopefully Super GRUB and Grub will actually recognize the partition this time, i'll try that in a bit and get back too you

---

### Post by stroudma on 2008-04-04
alright, well i reinstalled everything after much hassle, vista again deleted GRUB but this time instead of worrying about it i used easybcd, to set up the dual boot, it gives you the option to  boot linux using something called neogrub, i believe, so everything is right again in the world, haha, sorry i didnt get around to testing the last thing you posted, but thanks for the help man, i really appreciate it

oh and i dunno if you ever actually had to use Super GRUB before but that is a really handy program and not just for linux, im about to keep a copy for emergencies and such

---

