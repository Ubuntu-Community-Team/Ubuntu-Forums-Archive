---
title: "Gutsy and Grub problems"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by rp2615 on 2007-10-27
Hi there!
I just upgraded to gutsy (fresh install) and something went wrong with the installation, GRUB gives me error 22 and I am only able to boot via livecd.

here is the output of fdisk -l:

```
ubuntu@ubuntu:/mnt/root$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00470046

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17326357

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x021d1399

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       39163   314576766    7  HPFS/NTFS
/dev/sdc2           39164       48641    76132035    5  Extended
/dev/sdc5           39164       48591    75730378+  83  Linux
/dev/sdc6           48592       48641      401593+  82  Linux swap / Solaris
ubuntu@ubuntu:/mnt/root$ 

```

here is my menu.lst from the linux partition:

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
# kopt=root=UUID=50c1969d-bfc4-4d71-92f2-6e9964491469 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,4)

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
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=50c1969d-bfc4-4d71-92f2-6e9964491469 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=50c1969d-bfc4-4d71-92f2-6e9964491469 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

and here is my device.map:
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```

I have 3 hds, 2 ide and 1 sata, windows is in the 1st ide (sda1) drive and ubuntu is installed in the second partition of the sata drive (sdc5, according to fdisk).

I would really appreciate some help since I can't boot to any os (I know the 'fixmbr' trick but that only solves the windows problem and I really want ubuntu:))

---

### Post by Pumalite on 2007-10-27
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
Start by reinstalling Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
If it doesn't do the trick, we'll try other things.

---

### Post by thelocust on 2007-10-27
I think your sdc5 need to have a boot flag added to it. I could be wrong and you might be able to only have 1 per hdd. But you could find out real quick with gparted. Can anybody else tell me if I'm wrong?
 
Edit: Nevermind since XP is on sda1 you can switch the boot flag from sdc1 to sdc5.

---

### Post by Pumalite on 2007-10-27
BEHIND ME is right. What's more interesting is that there are 2 boot flags pointing to two different ntfs partitions. So, you might be right and all that is needed is moving the boot flag from sdc1 to sdc5. But reinstalling Grub might correct that. Let's wait.

---

### Post by rp2615 on 2007-10-27
Thank you for the quick replys!

I've just set the boot flag on gparted and I've reinstalled grub with that guide but  got the same result, any other ideas?:confused:

btw, this is the curent output of fdisk -l:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00470046

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17326357

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x021d1399

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       39163   314576766    7  HPFS/NTFS
/dev/sdc2           39164       48641    76132035    5  Extended
/dev/sdc5   *       39164       48591    75730378+  83  Linux
/dev/sdc6           48592       48641      401593+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


```

---

### Post by thelocust on 2007-10-27
Can you repost you menu.lst also.

---

### Post by rp2615 on 2007-10-27
here it is:
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
# kopt=root=UUID=50c1969d-bfc4-4d71-92f2-6e9964491469 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,4)

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
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=50c1969d-bfc4-4d71-92f2-6e9964491469 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=50c1969d-bfc4-4d71-92f2-6e9964491469 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by thelocust on 2007-10-27
Error 22: no such partition.
 
when you boot up and Grub gives you the option to pick an OS highlight the ubuntu option and hit "e" twice. this will bring up (hd2,4). Change the numbers then hit enter and "b" to try and boot. repeat until it works i.e.
 
(hd0,0)
(hd0,1)
(hd0,2)
(hd1,0)
(hd2,0)
 
remember which one worked.

---

### Post by thelocust on 2007-10-27
Hope it works out for you I gotta get going. Good luck.

---

### Post by Pumalite on 2007-10-27
Change this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

To this:
title		Windows NT/2000/XP (loader)
rootnoverify		(hd0,0)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
savedefault
makeactive
chainloader	+1

And place it in your menu.lst below memtest and above KERNEL MAGIC

---

### Post by rp2615 on 2007-10-27
Wow, that was wierd, I tried with hd0,4 and ubuntu booted, something must switched somewhere.
Anyway, thank your for your help, now I just have to guess where grub thinks my windows partition is and I'l be set:guitar:

---

### Post by rp2615 on 2007-10-27
@Pumalite:
I made those changes on menu.lst an now windows boots as well! This is just a wierd bug I guess.

Thank you for your help!

---

### Post by logos34 on 2007-10-27
cancel

---

### Post by logos34 on 2007-10-27
> **rp2615 said:**
> @Pumalite:
I made those changes on menu.lst an now windows boots as well! This is just a wierd bug I guess.

Thank you for your help!

But isn't that booting windows on sdc1?  What about windows on sda1?

---

### Post by rp2615 on 2007-10-27
> **logos34 said:**
> But isn't that booting windows on sdc1?  What about windows on sda1?

I only have windows in sda, so I guess it's booting that; it thinks sdc is hd0 and sda is hd1; wierd stuff...

---

### Post by logos34 on 2007-10-27
yeah, weird stuff is right...i'm still scratching my head over how grub detected the drives (even considering the ide and sata mix).  Because I would think that windows entry with 'rootnoverify (hd0,0)' it would try to boot sdc1 since sdc is definitely hd0...And I'm not forgetting the map lines

---

### Post by thelocust on 2007-10-27
> **rp2615 said:**
> Wow, that was wierd, I tried with hd0,4 and ubuntu booted, something must switched somewhere.
Don't forget to change groot=(hd2,4) to groot=(hd0,4) in your menu.lst so when the kernel updates it doesn't revert back. Glad it worked out for you.

---

### Post by Pumalite on 2007-10-27
Don' t try to fix something that is not broken. You have your Ubuntu and your Windows. Be happy.

---

### Post by thelocust on 2007-10-27
> **Pumalite said:**
> Don' t try to fix something that is not broken. You have your Ubuntu and your Windows. Be happy.but it will break later:confused:

---

### Post by Pumalite on 2007-10-27
Not unless they fool around with it.

---

### Post by meierfra on 2007-10-27
> Not unless they fool around with it.

If groot does not get changed, Ubuntu won't boot after the next kernel upgrade, 

And since the windows title  got moved to the automatic kernel section, windows will disappear from the grub menu.

---

### Post by Tosa on 2007-10-28
> **thelocust said:**
> Don't forget to change groot=(hd2,4) to groot=(hd0,4) in your menu.lst so when the kernel updates it doesn't revert back. Glad it worked out for you.

In my menu.lst the groot line is commented. Should it be uncommented?

---

### Post by thelocust on 2007-10-28
> **Tosa said:**
> In my menu.lst the groot line is commented. Should it be uncommented?No it's good here's mine as an example

```
# groot=(hd1,0)
```

---

