---
title: "2 sata drives 2 OS's both sda1"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by 289Shelby on 2007-07-20
Hi,

I have 2 sata drives each with a different OS, one Feisty and the other Debian. I installed these as standalone drives, ie, I disconnected the Feisty drive in order to install Debian to the other drive. (I had an 'oops moment' on a previous attempt so that's why I did it like that.)

Being that both drives are seen by their respective OS's as sda1, is there any way that I can now have both drives connected at the same time and dual boot?

I'm not sure what other info might be needed, I'm still a newbie, so I'll wait until I'm asked.

Many thanks,

Patrick

---

### Post by Pumalite on 2007-07-20
Regardless of the OS's seen both the drives as sda1, when you install both in the computer, the hardware makes them sda and sdb. Now you have to figure out which is which. They both have Grub (Ubuntu) and Bootloader (Debian) in the first partition of their hard drive. You'll have to decide who is going to boot whom. I, myself, would make sure Ubuntu is in sda (sda1) and Debian in sdb (sdb1). I would then edit /boot/grub/menu.lst in Ubuntu and add the parameters that would boot Debian.(that would make Debian (hd1,0)).

---

### Post by dabl on 2007-07-20
If you don't have your heart set on avoiding one re-installation, it would be easy to simply choose which Linux to re-install, and then reinstall that one, and let it write the boot menu for you.  It will detect the other OS, and put it in second position on the boot list, all automatically.  Plus, doing it this way, the fstab file for the one you re-install will be correct -- you may have to fix the other one if it doesn't configure itself when you boot that OS.  :popcorn:

---

### Post by Pumalite on 2007-07-20
> **dabl said:**
> If you don't have your heart set on avoiding one re-installation, it would be easy to simply choose which Linux to re-install, and then reinstall that one, and let it write the boot menu for you.  It will detect the other OS, and put it in second position on the boot list, all automatically.  Plus, doing it this way, the fstab file for the one you re-install will be correct -- you may have to fix the other one if it doesn't configure itself when you boot that OS.  :popcorn:

In that case I would reinstall Ubuntu. It has a great Grub.

---

### Post by 289Shelby on 2007-07-20
Firstly, sorry for the late reply to you all but we've only just got the power back on due to a storm.

> 
Regardless of the OS's seen both the drives as sda1, when you install both in the computer, the hardware makes them sda and sdb.


Thanks, I didn't realise that that is how it worked.

> 
 Now you have to figure out which is which. They both have Grub (Ubuntu) and Bootloader (Debian) in the first partition of their hard drive. You'll have to decide who is going to boot whom. I, myself, would make sure Ubuntu is in sda (sda1) and Debian in sdb (sdb1).


Would I be correct in thinking that to do this I would have to connect Ubuntu on it's own in order for the system to see it as sda, then alter Grub to suit and then connect Debian? Switching off in between times of course:)


> 
 I would then edit /boot/grub/menu.lst in Ubuntu and add the parameters that would boot Debian.(that would make Debian (hd1,0)).


Could or would you be kind enough to explain how I would need to edit Grub for this to work please. I'm not at all well versed on editing Grub and would not like to really mess it up.

Thanks.

dabl : If I can avoid reinstalling Ubuntu I would prefer it. I've already messed up once because these two drives are partitioned very similarly and not really knowing what I'm doing the last time I tried it I ended up formatting part of the wrong drive.

---

### Post by Pumalite on 2007-07-20
Lamentably I'm not familiar with Debian at all. I dont know if it has Lilo or Grub. If it's Grub is no problen. I'm going to show you an example of /boot/grub/menu.lst in my computer:

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
# kopt=root=UUID=4ab7776c-ece9-4ee3-855d-daba66ad9818 ro

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

## ## End Default Options ##

title           Linux Mint, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4ab7776c-ece9-4ee3-855d-daba66ad9818 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Linux Mint, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4ab7776c-ece9-4ee3-855d-daba66ad9818 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Linux Mint, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=4ab7776c-ece9-4ee3-855d-daba66ad9818 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Linux Mint, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=4ab7776c-ece9-4ee3-855d-daba66ad9818 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Linux Mint, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

This a copy of LinuxMint Grub. You would have to add Debian at the end, before END DEBIAN, etc, etc. If Debian has a Grub you could copy and paste, but you would have to edit 'root'. In your case, if you leave Debian as sdb, then it would be (hd1,0)

---

### Post by confused57 on 2007-07-20
I believe you can add an entry to Feisty's grub to boot Debian:
```
title        Debian
configfile   (hd1,0)/boot/grub/menu.lst
```

This should boot to Debian's menu.lst grub boot menu, highlight your Debian entry, press "e", then change root from (hd0,0) to (hd1,0), then in the kernel line change the root entry from /dev/sda1 to /dev/sdb1, then press "b" to boot...(you'll need to press "e" a couple of times when you're editing).  This should boot you into Debian, where you can make the changes permanent, if it works.

---

### Post by 289Shelby on 2007-07-20
Many thanks to both of you for the info. It's getting a bit late to start playing around with this tonight but will have a go tomorrow and get back with the results.

Re "hardware makes them sda and sdb". Is this dictated by the connectors on the motherboard? In other words I have connectors "ser1" and "ser2" on the board so if two drives are connected will "ser1" always be sda and "ser2" sdb and if only one drive is connected it will be sda regardless of which connector it's attached to.

Thanks

---

### Post by Pumalite on 2007-07-20
Check your mobo manual. I'm sure you'll find it.

---

### Post by dabl on 2007-07-20
> **289Shelby said:**
> Is this dictated by the connectors on the motherboard?

No, not directly.  In your BIOS, there should be a section on "Boot Device Sequence", and it should include options on setting the sequence between multiple drives.  In mine (an Intel mobo), there is one section for IDE/PATA drives (of which I could only have 2, since there's only one header), and SATA drives.  So, in BIOS I can change the boot sequence if I want to, although it looks like the rule is "IDE precedes SATA", but among the SATA drives I can change the sequence.

So, the "sda, sdb, sdc" thing is really set by your BIOS setting.

When you have both drives running and you're setting up your boot menu, using Pumalite's excellent advice above, make sure you keep an eye on the /etc/fstab file of the filesystem that is going to control booting.  In other words, the partitions that you cite in /boot/grub/menu.lst need to be a match to the layout that is described in /etc/fstab, allowing for the fact that fstab uses "sda1" where menu.lst uses "hd0,0" for the same drive and partition.  :)

---

### Post by confused57 on 2007-07-20
> **289Shelby said:**
> Many thanks to both of you for the info. It's getting a bit late to start playing around with this tonight but will have a go tomorrow and get back with the results.

Re "hardware makes them sda and sdb". Is this dictated by the connectors on the motherboard? In other words I have connectors "ser1" and "ser2" on the board so if two drives are connected will "ser1" always be sda and "ser2" sdb and if only one drive is connected it will be sda regardless of which connector it's attached to.

Thanks
Actually, it would probably be easier to set your bios to boot first to the Debian drive, then add an entry to Debian's grub to boot your Ubuntu drive, using a configfile entry.  Then all you would need to do is change the root from (hd0,0) to (hd1,0).  Feisty uses UUID's, therefore it doesn't matter whether it's sda or sdb, meaning you wouldn't need to change anything in your kernel root entry, nor in your fstab.

---

### Post by 289Shelby on 2007-07-21
I've sort of got this working in that I can boot to either drive but I to have problem in that Debian is trying to use the Ubuntu file system and Ubuntu is trying to use the Debian file system. My uneducated guess is that I need to reverse the sd* in fstab and grub. This is what I have at the moment on Ubuntu

Fstab:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
 /dev/sda1
UUID=b63eac38-9f61-4276-b899-8947a833ceaf /               ext3    defaults,errors=remount-ro 0    $
 /dev/sda6
UUID=dee460c6-ffee-4a5a-b29c-d369ba86e9b2 /home           ext3    defaults        0       2
 /dev/sda5
UUID=215aeda5-5693-48d9-927c-6bd22e75ef1a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#
# Debian
#
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb6       /home           ext3    defaults        0       2
/dev/sdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#/dev/sdb1      /media/usbdevice auto   rw,user,auto,noatime 0      0


Grub:

> 
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
# kopt=root=UUID=b63eac38-9f61-4276-b899-8947a833ceaf ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=b63eac38-9f61-4276-b899-8947a833ceaf ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=b63eac38-9f61-4276-b899-8947a833ceaf ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b63eac38-9f61-4276-b899-8947a833ceaf ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b63eac38-9f61-4276-b899-8947a833ceaf ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b63eac38-9f61-4276-b899-8947a833ceaf ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b63eac38-9f61-4276-b899-8947a833ceaf ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet



title		Debian GNU/Linux, kernel 2.6.21-2-k7
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.21-2-k7 root=/dev/sdb1 ro 
initrd		/boot/initrd.img-2.6.21-2-k7
savedefault

title		Debian GNU/Linux, kernel 2.6.21-2-k7 #(single-user mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.21-2-k7 root=/dev/sdb1 ro #single
initrd		/boot/initrd.img-2.6.21-2-k7
savedefault

title		Debian GNU/Linux, kernel 2.6.21-2-486
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.21-2-486 root=/dev/sdb1 ro 
initrd		/boot/initrd.img-2.6.21-2-486
savedefault

title		Debian GNU/Linux, kernel 2.6.21-2-486 #(single-user mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.21-2-486 root=/dev/sdb1 ro #single
initrd		/boot/initrd.img-2.6.21-2-486
savedefault

title		Debian GNU/Linux, kernel 2.6.18-4-486
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.18-4-486 root=/dev/sdb1 ro 
initrd		/boot/initrd.img-2.6.18-4-486
savedefault

title		Debian GNU/Linux, kernel 2.6.18-4-486 #(single-user mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.18-4-486 root=/dev/sdb1 ro #single
initrd		/boot/initrd.img-2.6.18-4-486
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST


Should these settings be perhaps on Debian and not Ubuntu? In the Bios the only setting I've got that relates to sata is to boot from scsi and that's it.

---

### Post by Pumalite on 2007-07-21
Please post the errors you get when trying to boot in either one of your distros.

---

### Post by confused57 on 2007-07-21
OK, it looks like you've chosen to boot first to Ubuntu, which will work fine.  If this is your Ubuntu fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1
UUID=b63eac38-9f61-4276-b899-8947a833ceaf / ext3 defaults,errors=remount-ro 0 $
/dev/sda6
UUID=dee460c6-ffee-4a5a-b29c-d369ba86e9b2 /home ext3 defaults 0 2
/dev/sda5
UUID=215aeda5-5693-48d9-927c-6bd22e75ef1a none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
#
# Debian
#
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/sdb6 /home ext3 defaults 0 2
/dev/sdb5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
#/dev/sdb1 /media/usbdevice auto rw,user,auto,noatime 0 0

I would suggest removing the Debian entries from your Ubuntu fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1
UUID=b63eac38-9f61-4276-b899-8947a833ceaf / ext3 defaults,errors=remount-ro 0 $
/dev/sda6
UUID=dee460c6-ffee-4a5a-b29c-d369ba86e9b2 /home ext3 defaults 0 2
/dev/sda5
UUID=215aeda5-5693-48d9-927c-6bd22e75ef1a none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

Also, I would suggest removing the Debian entries you have in your /boot/grub/menu.lst and add the configfile entry I suggested:
```
title Ubuntu, kernel 2.6.20-16-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-386 root=UUID=b63eac38-9f61-4276-b899-8947a833ceaf ro quiet splash
initrd /boot/initrd.img-2.6.20-16-386
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-386 root=UUID=b63eac38-9f61-4276-b899-8947a833ceaf ro single
initrd /boot/initrd.img-2.6.20-16-386

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=b63eac38-9f61-4276-b899-8947a833ceaf ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=b63eac38-9f61-4276-b899-8947a833ceaf ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=b63eac38-9f61-4276-b899-8947a833ceaf ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=b63eac38-9f61-4276-b899-8947a833ceaf ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title   Debian
configfile (hd1,0)/boot/grub/menu.lst
```

Added:  Just make sure your Debian  fstab and menu.lst are set up the way you've listed them here, i.e. root (hd1,0) and /dev/sdb1...this "should" work.  If it doesn't work setting everything up this way, then you might leave the settings you've changed, but try switching the cable connections of the hard drives.

---

### Post by 289Shelby on 2007-07-21
Well that worked and I can now boot into either OS. Whether it was worth it is another matter:-) Both OS's now have problems which are no doubt due to my first efforts. I may after all this have to reinstall them after all.

That said, many thanks for the time and help you've all given me. It's duly noted for future reference.

---

### Post by confused57 on 2007-07-21
> **289Shelby said:**
> Well that worked and I can now boot into either OS. Whether it was worth it is another matter:-) Both OS's now have problems which are no doubt due to my first efforts. I may after all this have to reinstall them after all.

That said, many thanks for the time and help you've all given me. It's duly noted for future reference.

Thought it "should" work, but you never know...what kind of problems are you having?  If you reinstall and install Debian to sdb, you might want to have Feisty on sda connected when you do.  You can always reinstall Feisty's grub using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

then add a configfile entry to boot Debian to Feisty's grub, or just use Debian's grub to boot Feisty...least you have a better understanding now of how grub works to boot distros on 2 separate hard drives.

See the grub section on this site for more info on how grub works:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by 289Shelby on 2007-07-21
> 
Thought it "should" work, but you never know...what kind of problems are you having?


I'm not sure what else might not work but at the moment and common to both OS's is that the minimise button on any program closes it. I can't get any program to actually minimise. On Debian I cannot get the nvidia driver to install. It was installed, using Envy. I've cleaned the system of any drivers and reinstalled it but X will only work with the 'nv' driver. Change it to 'nvidia' and X won't load.

> 
If you reinstall and install Debian to sdb, you might want to have Feisty on sda connected when you do.


That was the problem I originally had. Both the disks are 250GB and partitioned in a very similar way. When it comes to reinstalling all I see is sda and sdb as the disks and I'm not at all sure how to tell which is which. It would be handy if you could name the disks say, Debian and Ubuntu, at least the I would know which drive I was working on:-)

I will certainly take a look at the links you kindly provided. I never thought about doing any reading on Grub.

Many thanks.

---

### Post by confused57 on 2007-07-21
I'm not sure what's going on with your windows closing by clicking on the minimise button.  I have Debian Etch and installed the Nvidia driver using automatix2:
[http://www.getautomatix.com/](http://www.getautomatix.com/)
may depend on which Nvidia card you have, but it worked great with my GeForce FX5500

If you decide to try reinstalling Debian, maybe you could disconnect your Ubuntu drive from sda and just leave the drive you're installing Debian to connected to sdb...then all you would need to do is change the root from (hd0,0) to (hd1,0), if you decide to reinstall.  

Maybe starting a new thread with a descriptive title of the problem you're having with closing windows would get the attention of someone who has had this problem and was able to find a solution.

Grub is an impressive bootloader and much more powerful and easier to use than Window's bootloader...the link I provided is about the best I've seen.  Good luck.

---

### Post by upchucky on 2007-07-21
what u are trying to do will work, i have sda, sdb and they both can boot, it took supergrub editing to set it up
i can boot off of either one and access files on any with either one.

However ever since i switched to Fiesty, i cant automount my usb drive. i must connect my usb drive after booting so i can use the drive, edgy used to automount it, when i have some time i will figure that one out.

I can't remember if i posted how i got both installs to be bootable via grub, search my posts maybe i did post it.

---

### Post by 289Shelby on 2007-07-22
> 
I'm not sure what's going on with your windows closing by clicking on the minimise button. I have Debian Etch and installed the Nvidia driver using automatix2:
[http://www.getautomatix.com/](http://www.getautomatix.com/) may depend on which Nvidia card you have, but it worked great with my GeForce FX5500ton. I have Debian Etch and installed the Nvidia driver using automatix2:[http://www.getautomatix.com/](http://www.getautomatix.com/) may depend on which Nvidia card you have, but it worked great with my GeForce FX5500


On the initial install on Debian Testing is was great. I used Envy and my card is a GeForce 7600 GS so I know it can work..

> 
If you decide to try reinstalling Debian, maybe you could disconnect your Ubuntu drive from sda and just leave the drive you're installing Debian to connected to sdb...then all you would need to do is change the root from (hd0,0) to (hd1,0), if you decide to reinstall.


I think I will start again from scratch an reinstall both of them. Thanks to you I now know how to do what I wanted to.

I'm curious as to this minimise problem so I might start a new thread just to see if there is a solution. I did find out that while they don't minimise they are still running. The ps command shows that.

upchucky:

Thanks for the info, I will do a search for your posts to see what I can find.

---

