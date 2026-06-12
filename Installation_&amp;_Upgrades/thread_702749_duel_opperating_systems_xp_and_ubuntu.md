---
title: "duel opperating systems xp and ubuntu"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by carking on 2008-02-20
I had a former friend build my computer. he divided my 200 gig hard drive into two partitions then installed xp pro on one part and Ubuntu on the other.
to access an operating sys. we had to select it at start up. this worked great and we liked both.
last week all of a sudden the selection for windows was not there.
the folder was there in the hard drive of Ubuntu. 
I cannot figure why it doesn't show up any more at start up and my support guy (friend) dropped off the face of the earth.
Can any one tell me how to find windows in the start up screen.
I will check back soon I need to do my taxes and the tax software will not run on Ubuntu. 
If I cant fix this soon I will have to install xp home and format the hard drive and loose Ubuntu.

thanks for the help 

The carking (Paul)

---

### Post by Pumalite on 2008-02-20
You probably have to edit /boot/grub/menu.lst. Post:
sudo fdisk -lu

---

### Post by carking on 2008-02-20
:confused:
Sorry to deep for me.
be specific and detailed I'm not the sharpest at computers.
please Help.:(

---

### Post by jocheem67 on 2008-02-20
"Sudo fdisk -lu" is a command you put in the terminal, which is found in the top-left menu....
Then copy the output and paste it into your next post, people will be able to do some troubleshooting that way.
sudo stands for "superuser do" , some commands only work that way out of safety precaution...

Fdisk will show the attached drives and partitions...

---

### Post by carking on 2008-02-20
ok here it is
sudo: fdisk-lu: command not found

---

### Post by carking on 2008-02-20
Ok I typed it wrong here it is again.

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14601460

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   327677804   163838871    7  HPFS/NTFS
/dev/hda2       327677805   485066609    78694402+  83  Linux
/dev/hda3       485066610   488392064     1662727+  82  Linux swap / Solaris

Please explain. 

:confused:

---

### Post by Pumalite on 2008-02-20
OK., XP is in hda1 and Ubuntu in hda2. Post:
cat /boot/grub/menu.lst

---

### Post by carking on 2008-02-20
WOW
not sure what to do here how do I edit?

:confused:

~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=77c5e122-b96e-4b8b-b37c-05966e61393b ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=77c5e122-b96e-4b8b-b37c-05966e61393b ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=77c5e122-b96e-4b8b-b37c-05966e61393b ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

---

### Post by Pumalite on 2008-02-20
Backup your file first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Now edit:
gksudo gedit /boot/grub/menu.lst
Add Windows:
title Windows XP
root (hd0,0)
makeactive
chainloader +1

After this line:
### END DEBIAN AUTOMAGIC KERNELS LIST
Save, exit, reboot.

---

### Post by carking on 2008-02-20
wow your great 
now here is what I got 
where do I add windows.
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
timeout		15

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
# kopt=root=UUID=77c5e122-b96e-4b8b-b37c-05966e61393b ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=77c5e122-b96e-4b8b-b37c-05966e61393b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=77c5e122-b96e-4b8b-b37c-05966e61393b ro single
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
:confused:

---

### Post by Pumalite on 2008-02-20
Below this line:
### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by carking on 2008-02-20
do i put the

Add Windows:
title Windows XP
root (hd0,0)
makeactive
chainloader +1

or just

title Windows XP
root (hd0,0)
makeactive
chainloader +1

---

### Post by Pumalite on 2008-02-20
# This is for Windows XP
title Windows XP
root (hd0,0)
makeactive
chainloader +1

---

### Post by kathryn on 2008-02-20
In future, the <code> tag might make it easier for Paul (and other inexperienced users) to understand exactly what to paste in.

---

### Post by carking on 2008-02-20
Pumalit fantastic.
You are great swing by the house Ill give you a puppy we have 12 to get ride of 

that worked great. I have windows back in my start up menu it booted right into windows.
I have several problems to solve soon like
no sound on Ubuntu.sound works on windows.


Thank you very much::p

---

### Post by Pumalite on 2008-02-20
Thanks for the suggestion.

---

