---
title: "Ubuntu 7.10 A problem after upgrade kernel 2.6.22-15 Please Help!!!!"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by ksh29 on 2008-06-21
Hi, all

I am quite new to Ubuntu. I have used Ubuntu 7.10 for a while and have dual os in my pc, ubuntu 7.10 and windows XP. Today, I have upgraded the new kernel from 2.6.22-14 to 2.6.22-15 as ubuntu os remind to me to do so. Once the installation completed, I restart my pc and I found my boot menu only have following choice. 

Ubuntu 7.10, Kernel 2.6.22-15-generic
Ubuntu 7.10, Kernel 2.6.22-15-generic (recovery mode)
Ubuntu 7.10, Kernel 2.6.22-14-generic
Ubuntu 7.10, Kernel 2.6.22-14-generic (recover mode)
Ubuntu 7.10, memtest86+

The option for XP has gone and added with these new kernels. However, when I choice the new Kernle, the screen stucks at the ubuntu start up progress bar for a while and then comes to this screen with following message on it, 

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of build-in commands.
(initramfs)


I have also tried to root from kernel 2.6.22-14, but it got the same problem. I think the kernel upgrade has edited my boot menu, so i can't see the my XP option. Can anyone please help me with this issue? Or even tell me where i can edit the boot menu is very helpful. 

Thanks for your help.

---

### Post by Pumalite on 2008-06-21
Can you boot a Live CD?

---

### Post by ksh29 on 2008-06-21
> **Pumalite said:**
> Can you boot a Live CD?

Yes. I just tried it with ubuntu 7.10 live CD and it boots fine.

I found this reported bug very close to my case. 

Bug #151013 in linux-source-2.6.22 (Ubuntu)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151013?redirection_url=https%3A%2F%2Fbugs.launchpad.net%2Fubuntu%2F%2Bsource%2Flinux-source-2.6.22%2F%2Bbug%2F151013](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151013?redirection_url=https%3A%2F%2Fbugs.launchpad.net%2Fubuntu%2F%2Bsource%2Flinux-source-2.6.22%2F%2Bbug%2F151013)

---

### Post by Pumalite on 2008-06-21
Post:
sudo fdisk -lu

---

### Post by ksh29 on 2008-06-21
> **Pumalite said:**
> Post:
sudo fdisk -lu

Disk Identifier: 0xf0biebb0
/dev/sda1 *   63   30732344   15355141  c  W95 FAT32 (LBA)
/dev/sda2 30732345 73738349   21503002+ f  W95 Ext'd (LBA)
/dev/sda3 73738350 115121789  20691720  83 Linux
/dev/sda4 115121790 117210239 1044225   82 Linux swap /Solaris
/dev/sda5 30732408  73738349  21502971  b  W95 FAT32

Thanks for your help

---

### Post by Pumalite on 2008-06-21
sudo mkdir /media/sda3
sudo mount -t ext3 /dev/sda3 /media/sda3
Post:
cat /media/sda3/boot/grub/menu.lst

---

### Post by ksh29 on 2008-06-21
> **Pumalite said:**
> sudo mkdir /media/sda3
sudo mount -t ext3 /dev/sda3 /media/sda3
Post:
cat /media/sda3/boot/grub/menu.lst

menu.lst 

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
# kopt=root=UUID=2657ea99-0a26-4809-bf00-9038c45a4b1b ro

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

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=2657ea99-0a26-4809-bf00-9038c45a4b1b ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=2657ea99-0a26-4809-bf00-9038c45a4b1b ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2657ea99-0a26-4809-bf00-9038c45a4b1b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2657ea99-0a26-4809-bf00-9038c45a4b1b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


I also found the menu.lst.bk which is the one before this problem

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
# kopt=root=UUID=3afab94e-133c-4324-94e9-240a77391d95 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3afab94e-133c-4324-94e9-240a77391d95 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3afab94e-133c-4324-94e9-240a77391d95 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

thank again...

---

### Post by Pumalite on 2008-06-21
This is all you need:
menu.lst

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2657ea99-0a26-4809-bf00-9038c45a4b1b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-15-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-15-generic root=UUID=2657ea99-0a26-4809-bf00-9038c45a4b1b ro quiet splash
initrd /boot/initrd.img-2.6.22-15-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-15-generic root=UUID=2657ea99-0a26-4809-bf00-9038c45a4b1b ro single
initrd /boot/initrd.img-2.6.22-15-generic

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=2657ea99-0a26-4809-bf00-9038c45a4b1b ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=2657ea99-0a26-4809-bf00-9038c45a4b1b ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

Edit menu.lst
Backup the file first

---

### Post by ksh29 on 2008-06-21
Thanks for your help. umalite. Please excuse me if I have been careless. I can't see any different from the menu.lst file you have posted. Do I need to edit the menu.lst file? 

Cheers.

---

### Post by ksh29 on 2008-06-21
I got it. I have replace the UUID in the new menu.lst file by the UUID in the old one, which is also the same one in the /media/sda3/etc/fstab. It works now!!! Thanks. Umalite.....

---

### Post by Pumalite on 2008-06-21
Glad you got it. You are welcome. Good luck.

---

### Post by Mulhawkian on 2008-06-28
To all and Pumalite

New to Linux and Ubuntu.  I installed Ubuntu on a Windows XP system.  I have enjoyed Linux and the ability to boot into Windows XP when needed for the past 6 months. 


I have a very similar problem as ksh29.  After upgrade of Ubuntu 7.10 to Linux Kernel 2.6.22.15 I lost my Grub entry for booting into Windows XP.  


I am unable to use sudo gedit to edit menu.lst but I am able to use sudo nano.  When I append Pumalite's suggestion to the default menu.lst using nano and reboot my computer grub begins to load but then my system goes to a grub> prompt.  Note cut and paste of edit:

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader +1

title           Microsoft Windows XP Professional Recovery Console
root            (hd0,0)
savedefault
makeactive
chainloader +1


If I use the Repair Broken System I am able to cp the default menu.lst back, without Pumalites changes, to menu.lst and I am able to boot back into Linux.

It appears that any change I make to the default menu.lst causes the system to enter into grub> prompt instead of booting.  I have even tried just adding a title line after the ### END DEBIAN AUTOMAGIC KERNELS LIST entry and same thing.


sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4f6e4f6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     9782639     4891288+   b  W95 FAT32
/dev/sda2   *     9782640    72984239    31600800    7  HPFS/NTFS
/dev/sda3        72984240   153392399    40204080   83  Linux
/dev/sda4       153392400   156295439     1451520    5  Extended
/dev/sda5       154843983   156295439      725728+  82  Linux swap / Solaris
/dev/sda6       153392526   154843919      725697   82  Linux swap / Solaris

Partition table entries are not in disk order


Here is a cut and paste of nano read of default menu.lst that will boot me into linux.  The file appears to have a batch of control characters at the head but I have never used nano before and do not know if this is some kind of file header information or an indication the file maybe corrupted:

$^D&#65533;&#1412;&#65533;t&#1803;G^D&#65533;&#65533;^At^N&#65533;&#65533;^Hu&#971;E^H&#395;@E^A&#65533;&#395;E^H&#65533;p0&#459;@(^@^@^@^@&#65533;&#65533;t^P&#65533;4$&#65533;&#587;&#65533;^T^@&#65533;4$&#65533; &#65533;&#1675;&#65533;&#65533;E^H&#459;@0^@^@^@^@&#46672;&#65533;t&^@U&#65533;&#22096;&#65533;&#50768;^X&#65533;}&#65533;&#65533;}^P&#65533;]&#65533;&#34384;cÙ&#1753;&#65533;&#65533;Ù&#793;^Lp^@&#65533;u&#65533;&#65533;^G&#65533;p^D&#34384;I&#65533;(^@&#65533;<$&#65533;D$^D&#65533;&#1412;&#65533;&#65533;]&#65533;&#65533;u&#65533;&#65533;}&#65533;&#65533;&#65533;]Ë^G&#65533;p^D&#65533;&#65533;&#65533;&#1739;&#65533;&#65533;<$&#65533;D$^D&#65533;&#1412;&#65533;t&#1795;^?^D^Au E^H&#459;@,^@^@^@^@&#65533;&#653;&#65533;^@^@^@^@U&#65533;&#65533;&#65533;&#65533;^X&#65533;E^H&#65533;]&#65533;&#65533;}&#65533;&#65533;}^L&#65533;u&#65533;&#65533;@\&#65533;&#65533;^Í&#1741;&#65533;&#65533;ÍS^Lp^@&#65533;&#65533;t!&#65533;&#65533;t^]&#65533;^G&#65533;p^D&#65533;g&#65533;&#1741;&#65533;&#65533;<$&#65533;D$^D&#65533;&#1412;&#65533;t^F&#65533;G^D  u^O&#65533;$
p^@&#65533;Gl&#65533;&#65533;t^]&#65533;&#65533;&#65533;&#65533;t^R&#65533;Gp&#65533;]&#65533;&#65533;u&#65533;&#65533;}&#65533;&#65533;&#65533;]&#65533;f&#65533;&#65533;Gl&#65533;&#65533;&#65533;<$&#65533;&#65533;q&#65533;&#65533;&#65533;&#65533;&#65533;E&#65533;t&#1291;@^L&#459;^D$^X^@^@^@&#65533;E&#65533;&#65533;V&#65533;&#1675;&#65533;&#65533;E&#65533;&#65533;E&#65533;&#65533;D$^D&#65533;E&#65533;&#65533;^D$&#65533;&#65533;&#65533;&#1675;&#65533;&#65533;E&#65533;&#65533;Gl&#65533;E&#65533;&#65533;@^L&#459;^D$^X^@^@^@&#65533;E&#65533;&#65533;&&#65533;&#1675;&#65533;&#65533;E&#65533;&#65533;E&#65533;&#65533;D$^D&#65533;E&#65533;&#65533;^D$&#33905;&#1681;$
t&#65533;&#65533;&#48331;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;E&#265;L$^D&#65533;E&#65533;&#65533;^D$&#33355;&#65533;1&#1737;&#65533;&#48267;&#65533;X &#65533;&#65533;&#65533;^G&#65533;&#65533;u^Z&#65533;&#65533;&#946;^@&#52363;&#65533;&#65533;D$^H&#498;D$^D^Q^@^@^@&#65533;<$&#35979;&#754;Y&#1778;&#65533;&#65533;^G&#65533;4$&#65533;D$^D&#35979;=&#3211;&#1714;&#65533;&#46288;&#65533;&#65533;&^@^@^@^@&#65533;&#65533;'^@^@^@^@U&#65533;&#21712;&#65533;&#50384;^X&#65533;]&#65533;&#34000;Y&#65533;&#1747;&#65533;&#65533;Ó^Ó^@p^@&#65533;u&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^@^@^@&#65533;&#65533;&#65533;&#1708;&#65533;&#65533;^@&#65533;4$&#65533;D$^D&#65533;¬&#2028;&#1708;&#65533;&#48589;t&^@U&#65533;&#24013;WVS&#36301;&#52685;&#65533;&#1783;&#65533;&#65533;÷U^@p^@&#65533;&#52685;\&#65533;}^L&#65533;&#65533;&#65533;&#28109;&#65533;&#65533;&#65533;^F&#65533;&#65533;^O&#65533;&#1335;^A^@^@&#65533;^F&#65533;U^P&#65533;D$^D&#65533;^B&#65533;^D$&#36301;R?&#1783;&#65533;&#65533;&#65533;tW&#65533;&#65533;&#65533;}&#65533;t^H&#65533;^G&#65533;<$&#65533;P^D&#65533;^F&#65533;&#65533;^O&#65533;i^B^@^@&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;D$^
&#65533;&#65533;&#65533;&#65533;&#65533;0&#65533;&#65533;&#65533;&#65533;^F&#65533;&#65533;^O&#65533;&#65533;^B^@^@&#65533;^F&#65533;U^P&#65533;D$^D&#65533;^B&#65533;^D$&#65533;O=&#65533;&#65533;&#65533;&#65533;^O&#65533;&#65533;^@^@^@&#65533;&#65533;^\&#65533;&#65533;&#65533;&#65533;^F&#65533;&#65533;^O&#65533; ^C^@^@&#65533;^F&#65533;U^P&#65533;D$^D&#65533;^B&#65533;^D$&#65533;$=&#65533;&#65533;&#65533;&#65533;^O&#65533;^[^A^@^@&#65533;W^P&#65533;&#1161;U&#521;t   &#65533;G^P&#65533;^T$&#65533;P^D&#65533;^F&#65533;&#65533;^O&#65533;&#65533;^C^@^## lines between the AUTOMAGIC KERNELS LIST markers will be modified
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
# kopt=root=UUID=12cd0281-4ab7-42c9-bf81-29a2cc0bf5a4 ro

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

title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=12cd0281-4ab7-42c9-bf81-29a2cc0bf5a4 ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=12cd0281-4ab7-42c9-bf81-29a2cc0bf5a4 ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=12cd0281-4ab7-42c9-bf81-29a2cc0bf5a4 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=12cd0281-4ab7-42c9-bf81-29a2cc0bf5a4 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


I am in over my head and have tried for days to find a way to get my Windows XP grub entries to reappear.  I am learning from the experience and I know that most of computing is hammering until the rock breaks.  Tried reinstalling grub, tried using both nano and gedit and cut and paste your entire menu.lst ... any change from default gives me grub> prompt.

What ever help you can offer would be greatly appreciated.

Pete

---

### Post by fastharry on 2011-08-21
> **Mulhawkian said:**
> To all and Pumalite

New to Linux and Ubuntu.  I installed Ubuntu on a Windows XP system.  I have enjoyed Linux and the ability to boot into Windows XP when needed for the past 6 months. 


I have a very similar problem as ksh29.  After upgrade of Ubuntu 7.10 to Linux Kernel 2.6.22.15 I lost my Grub entry for booting into Windows XP.  


I am unable to use sudo gedit to edit menu.lst but I am able to use sudo nano.  When I append Pumalite's suggestion to the default menu.lst using nano and reboot my computer grub begins to load but then my system goes to a grub> prompt.  Note cut and paste of edit:

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader +1

title           Microsoft Windows XP Professional Recovery Console
root            (hd0,0)
savedefault
makeactive
chainloader +1


If I use the Repair Broken System I am able to cp the default menu.lst back, without Pumalites changes, to menu.lst and I am able to boot back into Linux.

It appears that any change I make to the default menu.lst causes the system to enter into grub> prompt instead of booting.  I have even tried just adding a title line after the ### END DEBIAN AUTOMAGIC KERNELS LIST entry and same thing.


sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4f6e4f6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     9782639     4891288+   b  W95 FAT32
/dev/sda2   *     9782640    72984239    31600800    7  HPFS/NTFS
/dev/sda3        72984240   153392399    40204080   83  Linux
/dev/sda4       153392400   156295439     1451520    5  Extended
/dev/sda5       154843983   156295439      725728+  82  Linux swap / Solaris
/dev/sda6       153392526   154843919      725697   82  Linux swap / Solaris

Partition table entries are not in disk order


Here is a cut and paste of nano read of default menu.lst that will boot me into linux.  The file appears to have a batch of control characters at the head but I have never used nano before and do not know if this is some kind of file header information or an indication the file maybe corrupted:

$^D&#65533;&#1412;&#65533;t&#1803;G^D&#65533;&#65533;^At^N&#65533;&#65533;^Hu&#971;E^H&#395;@E^A&#65533;&#395;E^H&#65533;p0&#459;@(^@^@^@^@&#65533;&#65533;t^P&#65533;4$&#65533;&#587;&#65533;^T^@&#65533;4$&#65533; &#65533;&#1675;&#65533;&#65533;E^H&#459;@0^@^@^@^@&#46672;&#65533;t&^@U&#65533;&#22096;&#65533;&#50768;^X&#65533;}&#65533;&#65533;}^P&#65533;]&#65533;&#34384;cÙ&#1753;&#65533;&#65533;Ù&#793;^Lp^@&#65533;u&#65533;&#65533;^G&#65533;p^D&#34384;I&#65533;(^@&#65533;<$&#65533;D$^D&#65533;&#1412;&#65533;&#65533;]&#65533;&#65533;u&#65533;&#65533;}&#65533;&#65533;&#65533;]Ë^G&#65533;p^D&#65533;&#65533;&#65533;&#1739;&#65533;&#65533;<$&#65533;D$^D&#65533;&#1412;&#65533;t&#1795;^?^D^Au E^H&#459;@,^@^@^@^@&#65533;&#653;&#65533;^@^@^@^@U&#65533;&#65533;&#65533;&#65533;^X&#65533;E^H&#65533;]&#65533;&#65533;}&#65533;&#65533;}^L&#65533;u&#65533;&#65533;@\&#65533;&#65533;^Í&#1741;&#65533;&#65533;ÍS^Lp^@&#65533;&#65533;t!&#65533;&#65533;t^]&#65533;^G&#65533;p^D&#65533;g&#65533;&#1741;&#65533;&#65533;<$&#65533;D$^D&#65533;&#1412;&#65533;t^F&#65533;G^D  u^O&#65533;$
p^@&#65533;Gl&#65533;&#65533;t^]&#65533;&#65533;&#65533;&#65533;t^R&#65533;Gp&#65533;]&#65533;&#65533;u&#65533;&#65533;}&#65533;&#65533;&#65533;]&#65533;f&#65533;&#65533;Gl&#65533;&#65533;&#65533;<$&#65533;&#65533;q&#65533;&#65533;&#65533;&#65533;&#65533;E&#65533;t&#1291;@^L&#459;^D$^X^@^@^@&#65533;E&#65533;&#65533;V&#65533;&#1675;&#65533;&#65533;E&#65533;&#65533;E&#65533;&#65533;D$^D&#65533;E&#65533;&#65533;^D$&#65533;&#65533;&#65533;&#1675;&#65533;&#65533;E&#65533;&#65533;Gl&#65533;E&#65533;&#65533;@^L&#459;^D$^X^@^@^@&#65533;E&#65533;&#65533;&&#65533;&#1675;&#65533;&#65533;E&#65533;&#65533;E&#65533;&#65533;D$^D&#65533;E&#65533;&#65533;^D$&#33905;&#1681;$
t&#65533;&#65533;&#48331;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;E&#265;L$^D&#65533;E&#65533;&#65533;^D$&#33355;&#65533;1&#1737;&#65533;&#48267;&#65533;X &#65533;&#65533;&#65533;^G&#65533;&#65533;u^Z&#65533;&#65533;&#946;^@&#52363;&#65533;&#65533;D$^H&#498;D$^D^Q^@^@^@&#65533;<$&#35979;&#754;Y&#1778;&#65533;&#65533;^G&#65533;4$&#65533;D$^D&#35979;=&#3211;&#1714;&#65533;&#46288;&#65533;&#65533;&^@^@^@^@&#65533;&#65533;'^@^@^@^@U&#65533;&#21712;&#65533;&#50384;^X&#65533;]&#65533;&#34000;Y&#65533;&#1747;&#65533;&#65533;Ó^Ó^@p^@&#65533;u&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^@^@^@&#65533;&#65533;&#65533;&#1708;&#65533;&#65533;^@&#65533;4$&#65533;D$^D&#65533;¬&#2028;&#1708;&#65533;&#48589;t&^@U&#65533;&#24013;WVS&#36301;&#52685;&#65533;&#1783;&#65533;&#65533;÷U^@p^@&#65533;&#52685;\&#65533;}^L&#65533;&#65533;&#65533;&#28109;&#65533;&#65533;&#65533;^F&#65533;&#65533;^O&#65533;&#1335;^A^@^@&#65533;^F&#65533;U^P&#65533;D$^D&#65533;^B&#65533;^D$&#36301;R?&#1783;&#65533;&#65533;&#65533;tW&#65533;&#65533;&#65533;}&#65533;t^H&#65533;^G&#65533;<$&#65533;P^D&#65533;^F&#65533;&#65533;^O&#65533;i^B^@^@&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;D$^
&#65533;&#65533;&#65533;&#65533;&#65533;0&#65533;&#65533;&#65533;&#65533;^F&#65533;&#65533;^O&#65533;&#65533;^B^@^@&#65533;^F&#65533;U^P&#65533;D$^D&#65533;^B&#65533;^D$&#65533;O=&#65533;&#65533;&#65533;&#65533;^O&#65533;&#65533;^@^@^@&#65533;&#65533;^\&#65533;&#65533;&#65533;&#65533;^F&#65533;&#65533;^O&#65533; ^C^@^@&#65533;^F&#65533;U^P&#65533;D$^D&#65533;^B&#65533;^D$&#65533;$=&#65533;&#65533;&#65533;&#65533;^O&#65533;^[^A^@^@&#65533;W^P&#65533;&#1161;U&#521;t   &#65533;G^P&#65533;^T$&#65533;P^D&#65533;^F&#65533;&#65533;^O&#65533;&#65533;^C^@^## lines between the AUTOMAGIC KERNELS LIST markers will be modified
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
# kopt=root=UUID=12cd0281-4ab7-42c9-bf81-29a2cc0bf5a4 ro

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

title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=12cd0281-4ab7-42c9-bf81-29a2cc0bf5a4 ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=12cd0281-4ab7-42c9-bf81-29a2cc0bf5a4 ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=12cd0281-4ab7-42c9-bf81-29a2cc0bf5a4 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=12cd0281-4ab7-42c9-bf81-29a2cc0bf5a4 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


I am in over my head and have tried for days to find a way to get my Windows XP grub entries to reappear.  I am learning from the experience and I know that most of computing is hammering until the rock breaks.  Tried reinstalling grub, tried using both nano and gedit and cut and paste your entire menu.lst ... any change from default gives me grub> prompt.

What ever help you can offer would be greatly appreciated.

Pete



I don't like the sound of this....Maybe I can help being an Ubuntu fan..

---

