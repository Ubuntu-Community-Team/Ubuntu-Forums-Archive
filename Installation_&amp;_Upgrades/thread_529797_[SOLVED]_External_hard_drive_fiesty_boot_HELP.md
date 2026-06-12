---
title: "[SOLVED] External hard drive fiesty boot *HELP*"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by rigv on 2007-08-19
Hi guys, 

I'm so close on destroying my external hdd and feisty live-cd... been** 2** nights that I've been trying to figure this problem out..

I bought a new *80gb 2.5" hard drive (WD Element)* and when I tried to install ubuntu fiesty fawn on it with grub (/dev/sdd <thats the location, I have 2 internal hard drives 160 & 400gb Seagate which has XP Pro in it) I took off my sata cables from my internals and plugged in my new usb drive, and installation was sweet and when I reboot my system this happened...;

First problem was** Error 29** and somehow fixed it by deleting* "savetodefault*"* from /media/disk/boot/grub/menu.lst and it worked, updated it and installed a driver for my 8800 and when I rebooted it again, it just showed me a black screen.. for almost **30mins** so I rebooted it and went back on Live-CD

Re-installed everything and this time with internals hard drive plugged in and did the boot location /dev/sdd and installation was sweet, then I encountered 2 annoying problems... **IT WONT BOOT** at all and went straight to XP Pro, I changed my bios to load up the external first then my OS hard drive.. reboot then loaded grub, cool.. then it gave me another error, ERROR 17.. heck.. I give up..

I seriously don't know what to do, if you guys can help me out. I would appreciate it! so please don't hesitate!! pleaseee.

Thanks

---

### Post by bulldog on 2007-08-19
If you installed GRUB on the external hdd,you must be able to boot from an USB device.
If you choose this option at boot time,you can start ubuntu from the grub menu.
If you do nothing your computer will boot from the first internal hdd,which aparantly is your windows hdd and you won't see anything of grub or the menu.lst

EDIT:
As far as I know,you can't set your USB hdd as first boot device in your BIOS.
So you should have an option like F12 or something to get a choice from which device you want to boot.

---

### Post by rigv on 2007-08-19
I tried doing that as well, in my case it's "ESC" I'm using Phoenix Bios on nVidia motherboard. Didn't work :(

---

### Post by bulldog on 2007-08-19
I think you didn't understand me :)
To boot from an USB hdd your BIOS must be able to do so,not all computers have this option.
When you boot your computer,you can see on the first page [mostly at the bottom of the screen] something like:Push DEL to get to the BIOS,Push F12 to get to the bootmenu.
If you hit F12 you see a list with all the boot able devices like cd-rom dvd-player hdd's and USB devices.
Now you select the USB device to boot from and you should see the GRUB menu,if you had installed it there of course.

EDIT:
Keep in mind that if your BIOS isn't capable to boot from an USB device,it will be hard to boot from it.
Any OS like the live cd will detect the USB device and let you install on it,but that won't make the device bootable.

---

### Post by logos34 on 2007-08-19
Boot frm the live cd and click on your linux partition to mount it.

**gksudo gedit /media/disk/boot/grub/menu.lst**

Change all instances of (hd1,0) to **(hd0,0)**  
(when you set the bios to boot first from the usb external it is seen as hd0)

Also change **device.map** so that the linux drive is '(hd0)'

---

### Post by logos34 on 2007-08-19
> **bulldog said:**
> I think you didn't understand me :)
To boot from an USB hdd your BIOS must be able to do so,not all computers have this option.
When you boot your computer,you can see on the first page [mostly at the bottom of the screen] something like:Push DEL to get to the BIOS,Push F12 to get to the bootmenu.
If you hit F12 you see a list with all the boot able devices like cd-rom dvd-player hdd's and USB devices.
Now you select the USB device to boot from and you should see the GRUB menu,if you had installed it there of course.

EDIT:
Keep in mind that if your BIOS isn't capable to boot from an USB device,it will be hard to boot from it.
Any OS like the live cd will detect the USB device and let you install on it,but that won't make the device bootable.

Unless I've misunderstood I think he is able to boot the usb drive--he said changed it to first in the Bios order and Grub menu comes up, but can't boot the ubuntu kernel--apparently the path is wrong.

---

### Post by rigv on 2007-08-19
> **bulldog said:**
> I think you didn't understand me :)
To boot from an USB hdd your BIOS must be able to do so,not all computers have this option.
When you boot your computer,you can see on the first page [mostly at the bottom of the screen] something like:Push DEL to get to the BIOS,Push F12 to get to the bootmenu.
If you hit F12 you see a list with all the boot able devices like cd-rom dvd-player hdd's and USB devices.
Now you select the USB device to boot from and you should see the GRUB menu,if you had installed it there of course.

EDIT:
Keep in mind that if your BIOS isn't capable to boot from an USB device,it will be hard to boot from it.
Any OS like the live cd will detect the USB device and let you install on it,but that won't make the device bootable.

I get what you mean, but I don't have F2 hehe I have "ESC" for boot menu.

> **logos34 said:**
> Boot frm the live cd and click on your linux partition to mount it.




**gksudo gedit /media/disk/boot/grub/menu.lst**

Change all instances of (hd1,0) to **(hd0,0)**  
(when you set the bios to boot first from the usb external it is seen as hd0)

Also change **device.map** so that the linux drive is '(hd0)'

How do I go linux partition? and everything has (hd2.0) in it :S I'll try changing that now and see what happens

BTW heres my list fdisk -l

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
16 heads, 63 sectors/track, 775221 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      365714   184319824+   7  HPFS/NTFS
/dev/sdb2          365715      775218   206390016    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris


---

### Post by logos34 on 2007-08-19
> **rigv said:**
> I get what you mean, but I don't have F2 hehe I have "ESC" for boot menu.

How do I go linux partition? and everything has (hd2.0) in it :S I'll try changing that now and see what happens

mistake on my part...right, (hd2,0) because it's sdc and was obviously seen last (the **two** internals always get listed first by the ubuntu installer)

---

### Post by rigv on 2007-08-19
I will try to reformat and re-install everything

This time I will set boot loader to (HD2,0).

Correct me if I'm wrong but is the sequence goes like this?

HD0,0 - Drive 1
HD1,0 - Drive 2
HD2.0 - Drive 3
and so on?

---

### Post by confused57 on 2007-08-19
> **rigv said:**
> I will try to reformat and re-install everything

This time I will set boot loader to (HD2,0).

Correct me if I'm wrong but is the sequence goes like this?

HD0,0 - Drive 1
HD1,0 - Drive 2
HD2.0 - Drive 3
and so on?
Try pressing "Esc" when prompted to enter grub's boot menu, then highlight your Ubuntu entry, press "e" to edit, highlight the line with root, press "e" again, change root from (hd2,0) to (hd0,0), press "enter", then "b" to boot.

This site explains grub quite nicely:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Drive 1 is (hd0)
Drive 2 is (hd1)
Drive 3 is (hd2)

(hd2,0) is the 3rd drive, first partition.

---

### Post by rigv on 2007-08-19
Cool my hunch was right hheeh,

Here is my boot devices in order;
-Removable
-Hard Drive
-CD/DVD

And here's my Hard Drive devices in order;
-160gb (XP Pro)
-400gb (Storage)
-80gb (External)

---

### Post by logos34 on 2007-08-19
> **rigv said:**
> Cool my hunch was right hheeh,

Here is my boot devices in order;
-Removable
-Hard Drive
-CD/DVD

And here's my Hard Drive devices in order;
-160gb (XP Pro)
-400gb (Storage)
-80gb (External)

I thought you said you changed the bios order to boot the usb first (and were able to get grub menu just not boot the ubuntu kernel)? --

> ...IT WONT BOOT at all and went straight to XP Pro, I **changed my bios to load up the external first then my OS hard drive.. reboot then loaded grub, cool.. then it gave me another error, ERROR 17**.. heck.. I give up..

Set the 80 GB external usb first in the hard disk boot priority:

[B]
-80gb (External)[/B]
-160gb (XP Pro)
-400gb (Storage)

Now try it with the edited menu.lst -- i.e. all instances of (hd2,0) changed to (hd0,0)

Or just do what Confused57 said and hit 'e' on the grub menu and change it that way

---

### Post by rigv on 2007-08-19
I kinda fix the booting problem.

I'm suppose to boot in Hard Drive>80WDexternal not Removable Devices>USB so I can boot now on Grub w/o problems.

My only problem now is Error 17...? mounting partition something..

---

### Post by rigv on 2007-08-19
> **logos34 said:**
> I thought you said you changed the bios order to boot the usb first (and were able to get grub menu just not boot the ubuntu kernel)? --



Set the 80 GB external usb first in the hard disk boot priority:

[B]
-80gb (External)[/B]
-160gb (XP Pro)
-400gb (Storage)

Now try it with the edited menu.lst -- i.e. all instances of (hd2,0) changed to (hd0,0)

Or just do what Confused57 said and hit 'e' on the grub menu and change it that way

I'm sorry Logo, I keep on changing the booting sequence. sorry.

---

### Post by logos34 on 2007-08-19
> **rigv said:**
> I'm sorry Logo, I keep on changing the booting sequence. sorry.

no problem...and you'll have to edit device.map too if you want to have a chance of using grub to boot windows, but save that for later if you haven't done it.

---

### Post by rigv on 2007-08-19
Cool man, whats device.map? hehe and how can I fix Error 17?

---

### Post by logos34 on 2007-08-19
> **rigv said:**
> Cool man, whats device.map? hehe and how can I fix Error 17?

still error 17 after doing that?  what a bummer.


[edit]

here:

**/boot/grub/device.map** 

But there;s not much point in worrying about it if you can't get any linux kernels to boot.

---

### Post by logos34 on 2007-08-19
rigv,

Can you post your disk info and grub files?  From the live cd, mount root partition, then

**sudo fdisk -l**  (lowercase letter L)

**cat /media/disk/boot/grub/menu.lst /media/disk/boot/grub/device.map **

---

### Post by rigv on 2007-08-19
FDISK

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
16 heads, 63 sectors/track, 775221 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      365714   184319824+   7  HPFS/NTFS
/dev/sdb2          365715      775218   206390016    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris




GRUB menu

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
# kopt=root=UUID=711990f8-2ce0-4fc7-8317-c4e55bd5038e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=711990f8-2ce0-4fc7-8317-c4e55bd5038e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=711990f8-2ce0-4fc7-8317-c4e55bd5038e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
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
chainloader	+1


Grub device.map

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdd


I don't know how to do "mount root partition" is that a command or a file? :S

---

### Post by logos34 on 2007-08-19
> I don't know how to do "mount root partition" is that a command or a file? :S

it's mounted, otherwise you wouldn't have access to your files (in Fesity you simply have to click on it in nautilus browser.  Or you can mount it with s**udo mount -t <filesystem> /dev/<drive> /mointpoint**)

Ok, to the main matter--first off I see this discrepancy: 

-your menu.lst says (hd2,0) for linux, and the device.map has **(hd2) /dev/sdd**, but linux root is on /dev/sdc1 according to fdisk.  However sdc is  not listed on the device.map.  

Did you have a USB stick/flash drive attached?

Try editing your boot files and then reinstall Grub to the MBR of the USB 80 GB external drive (make sure you get the right drive!).

Open menu.lst and make these changes:
[B]
gksudo gedit /media/disk/boot/grub/menu.lst[/B]


change the 'groot' line:

> ## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd**[COLOR="Red"]0[/COLOR]**,0)

Then the kernels:

> 
title Ubuntu, kernel 2.6.20-15-generic
root (hd[COLOR="Red"]0[/COLOR],0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=711990f8-2ce0-4fc7-8317-c4e55bd5038e ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd[COLOR="Red"]0[/COLOR],0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=711990f8-2ce0-4fc7-8317-c4e55bd5038e ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd[COLOR="Red"]0[/COLOR],0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd[COLOR="Red"]1[/COLOR],0)
savedefault
chainloader +1


Then, 

**gksudo gedit /media/disk/boot/grub/device.map**

**(hd0) /dev/sdc**
(hd1) /dev/sda
(hd2) /dev/sdb


Now reinstall Grub to the MBR of the USB drive:

[B]sudo grub
find /boot/grub/stage1[/B]
(enter the output '(hdx,0)--whatever it is-- in the next command.  'x' will be 0,1,or 2, i'm just not sure which at this point)
[B]root (hdx,0)
setup (hdx)[/B]
quit

Now reboot and enter the bios.  Make sure the USB external 80 GB drive is set first in the hard disk boot order.

---

### Post by rigv on 2007-08-19
Mate, your a legend! ahh man thanks alot! you just made my day! Ahh KUDOS to you man.

---

### Post by logos34 on 2007-08-20
Ok, great,

If you want to edit the windows entry in menu.lst so you can boot it (or try to boot it!) from grub menu, post back.

---

### Post by rigv on 2007-08-20
How? :S that would be cool. 'Cause at the moment I cant..

---

### Post by logos34 on 2007-08-20
ok, if your windows drive is hd1 (i.e. second in the bios boot order after the linux drive), and it's listed in device.map as

**(hd1) /dev/sda**

then you can try adding the following lines to menu.lst entry for windows:
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd1,0)   
[B]map (hd0) (hd1)
map (hd1) (hd0)[/B]
savedefault
chainloader +1

*or try **rootnoverify (hd1,0)** in place of root line above

---

### Post by rigv on 2007-08-21
Thanks!

---

