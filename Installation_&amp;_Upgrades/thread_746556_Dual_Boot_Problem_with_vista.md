---
title: "Dual Boot Problem with vista"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by ayush3090 on 2008-04-05
i had Vista already installed on my x86 PC
then i installed Ubuntu in another partition
but i dont see Windows Vista In the Grub boot loader
all i see is the 3 ubuntu kernel and etc stuff

is there a way to start vista again ?

thanx

---

### Post by Pumalite on 2008-04-05
Yes. First, post, from the Terminal, the output of:
sudo fdisk -lu

---

### Post by ayush3090 on 2008-04-05
sure sir

```
ayush@Ayush:~$ sudo fdisk -lu
[sudo] password for ayush:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf8fff8ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    63617399    31808668+  83  Linux
/dev/sda2        66441060   390721319   162140130    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3        63617400    66428774     1405687+   5  Extended
/dev/sda5        63617463    66428774     1405656   82  Linux swap / Solaris

Partition table entries are not in disk order
ayush@Ayush:~$ 
ayush@Ayush:~$ 


```

---

### Post by Pumalite on 2008-04-05
Post:
cat /boot/grub/menu.lst

---

### Post by ayush3090 on 2008-04-05
```
ayush@Ayush:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=7dc0af05-427a-403d-bba6-f98f9848d687 ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=7dc0af05-427a-403d-bba6-f98f9848d687 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=7dc0af05-427a-403d-bba6-f98f9848d687 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ayush@Ayush:~$ 

```

---

### Post by Pumalite on 2008-04-05
Backup your file first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Let's edit:
gksudo gedit /boot/grub/menu.lst
Below this line:
### END DEBIAN AUTOMAGIC KERNELS LIST
Add the following:
title         Windows 
rootnoverify          (hd0,1)
savedefault
makeactive
chainloader   +1

Save, exit, reboot.
(This might be a problem: 'Partition 2 does not end on cylinder boundary')

---

### Post by ayush3090 on 2008-04-05
sir this is what i get in the boot menu - 

[IMG]http://xs126.xs.to/xs126/08140/image_352_223.jpg[/IMG]

---

### Post by ayush3090 on 2008-04-05
im sorry but how and what should i back up ?

---

### Post by Pumalite on 2008-04-05
Post again your menu.lst to check it:
cat /boot/grub/menu.lst

---

### Post by ayush3090 on 2008-04-05
```
ayush@Ayush:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=7dc0af05-427a-403d-bba6-f98f9848d687 ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=7dc0af05-427a-403d-bba6-f98f9848d687 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=7dc0af05-427a-403d-bba6-f98f9848d687 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ayush@Ayush:~$ 
ayush@Ayush:~$ 

```

how do i edit this ?

---

### Post by Pumalite on 2008-04-05
Follow the commands I gave above at the Terminal. That will make a copy of your menu.lst in case something goes wrong. 
Once you are in 'gedit' (an editor), just add what I told you.. Then you save it by going to 'File'>Save.

---

### Post by ayush3090 on 2008-04-05
its empty sir - 

[IMG]http://xs126.xs.to/xs126/08140/screenshot699.png[/IMG]

---

### Post by Pumalite on 2008-04-05
Sorry. The command is:
gksudo gedit /boot/grub/menu.lst

---

### Post by ayush3090 on 2008-04-05
thanx sir i got the windows option but after i clicked it i got the following error - 

[IMG]http://xs226.xs.to/xs226/08140/image_353_181.jpg[/IMG]

---

### Post by Pumalite on 2008-04-05
You seem to have installed Ubuntu before Windows?

---

### Post by ayush3090 on 2008-04-05
no sir

i installed vista before ubuntu

---

### Post by Pumalite on 2008-04-05
How did you end up with Ubuntu in sda1 and Vista in sda2?:

'   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    63617399    31808668+  83  Linux
/dev/sda2        66441060   390721319   162140130    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.'

Vista, when installed first, normally goes on sda1.

---

### Post by ayush3090 on 2008-04-05
i earlier had windows XP media center edition installed along with Windows Vista

i then deleted the XP partition using Gparted and then installed ubuntu through the option "largest continuous space/volume available"

---

### Post by ayush3090 on 2008-04-05
but is there anything i could do now sir ?

---

### Post by ayush3090 on 2008-04-05
sir its 4:30 am here

its tooooo late

i better sleep now

i hope to see your reply on how to solve this problem after i wake up

thanx a lot for all the help till now

im really greatful to you

goodnite

---

### Post by Pumalite on 2008-04-05
You might also have a Partition Table problem. So I'd start from scratch. Use Gparted Live CD:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Make 2 partitions of your hard drive. The first (sda1) at the beginning ofr the drive formatted ntfs, for Vista. With the rest of the space, make 3 partitions:
10 GB for '/'
1 GB for /swap
The rest for /home.
Install Vista in the first partition. Then install Ubuntu, go 'Manual' and use the partitions already prepared.

---

### Post by ayush3090 on 2008-04-06
will i lose all my data that i had on vista ? :(

---

### Post by Pumalite on 2008-04-06
You can backup and restore>
[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)
you could try sbackup - in the repos
DAR
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)
[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

---

### Post by ayush3090 on 2008-04-08
hi sir, i just formated my whole PC, thankfully i had abackup of my data in my laptop

ive now installed vista again, and now im sing ubuntu 8.-4 hardy via wubi :D

thanx fr all your help

---

### Post by Pumalite on 2008-04-08
Congrats. Good luck.

---

