---
title: "[SOLVED] Please help me fix my Grub"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by krokodil on 2008-11-24
I have installed Etch on one hard drive and Ubuntu 8.10 on another. With just Ubuntu grub was working fine, but the Etch install configured it incorrectly.

I'm afraid I don't know how to fix it. Can someone please advise me?

Here is my fdisk -l. On /dev/sdb2 I have the new netinstall of Etch, and on /dev/sdd2 I have the Ubuntu 8.10:

+++

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1cba761

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2434 19551073+ 83 Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002acd1

Device Boot Start End Blocks Id System
/dev/sdb1 1 243 1951866 82 Linux swap / Solaris
/dev/sdb2 244 972 5855692+ 83 Linux
/dev/sdb3 2676 24321 173871495 83 Linux
/dev/sdb4 973 2675 13679347+ 83 Linux

Partition table entries are not in disk order

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00018e80

Device Boot Start End Blocks Id System
/dev/sdc1 1 30401 244196001 83 Linux

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002f246

Device Boot Start End Blocks Id System
/dev/sdd1 1 249 2000061 5 Extended
/dev/sdd2 250 2213 15775830 83 Linux
/dev/sdd4 2214 30401 226420110 83 Linux
/dev/sdd5 1 249 2000029+ 82 Linux swap / Solaris

Disk /dev/sde: 4127 MB, 4127194624 bytes
255 heads, 63 sectors/track, 501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

Device Boot Start End Blocks Id System
/dev/sde1 1 501 4024251 b W95 FAT32

++++

---

### Post by EnGorDiaz on 2008-11-24
> **krokodil said:**
> I have installed Etch on one hard drive and Ubuntu 8.10 on another. With just Ubuntu grub was working fine, but the Etch install configured it incorrectly.

I'm afraid I don't know how to fix it. Can someone please advise me?

Here is my fdisk -l. On /dev/sdb2 I have the new netinstall of Etch, and on /dev/sdd2 I have the Ubuntu 8.10:

+++

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1cba761

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2434 19551073+ 83 Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002acd1

Device Boot Start End Blocks Id System
/dev/sdb1 1 243 1951866 82 Linux swap / Solaris
/dev/sdb2 244 972 5855692+ 83 Linux
/dev/sdb3 2676 24321 173871495 83 Linux
/dev/sdb4 973 2675 13679347+ 83 Linux

Partition table entries are not in disk order

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00018e80

Device Boot Start End Blocks Id System
/dev/sdc1 1 30401 244196001 83 Linux

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002f246

Device Boot Start End Blocks Id System
/dev/sdd1 1 249 2000061 5 Extended
/dev/sdd2 250 2213 15775830 83 Linux
/dev/sdd4 2214 30401 226420110 83 Linux
/dev/sdd5 1 249 2000029+ 82 Linux swap / Solaris

Disk /dev/sde: 4127 MB, 4127194624 bytes
255 heads, 63 sectors/track, 501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

Device Boot Start End Blocks Id System
/dev/sde1 1 501 4024251 b W95 FAT32

++++

goto the link in my sig :) [http://ubuntuforums.org/showthread.php?t=990830](http://ubuntuforums.org/showthread.php?t=990830)

---

### Post by caljohnsmith on 2008-11-24
Do you know whether it is Ubuntu or Etch that controls Grub on start up? Which drive are you booting from on start up? How about posting the output of the following commands, but change "sda" to whichever is the drive you boot from on start up:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
If you don't know which drive you boot from on start up, please run the two commands above on all your drives.

---

### Post by krokodil on 2008-11-24
> Do you know whether it is Ubuntu or Etch that controls Grub on start up?

Since Etch is the last one I installed I think it is Etch. Also the Ubuntu Grub used to work fine, and the Etch grub menu.lst contains references to both Ubuntu and itself.

---

### Post by caljohnsmith on 2008-11-24
> **krokodil said:**
> Since Etch is the last one I installed I think it is Etch. Also the Ubuntu Grub used to work fine, and the Etch grub menu.lst contains references to both Ubuntu and itself.
So what exactly is wrong with your Debian Etch menu.lst then? What errors do you get when you boot Etch/Ubuntu? How about posting the contents of your Etch menu.lst, and also please post the output of the previous commands I gave using "sda" as the drive; we can work from there.

---

### Post by krokodil on 2008-11-24
The error I am recieving is "Error 22". Which as far as I can find out means "Can't find partition".

I can give you the device map and menu.lst, the output of the commands will have to wait until I get home.

Etch device.map:

(hd0)	/dev/hdd
(hd1)	/dev/sda
(hd2)	/dev/sdb
(hd3)	/dev/sdc

++++

Etch menu.lst

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
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title		Debian GNU/Linux, kernel 2.6.18-6-486
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.18-6-486 root=/dev/sda2 ro 
initrd		/boot/initrd.img-2.6.18-6-486
savedefault

title		Debian GNU/Linux, kernel 2.6.18-6-486 (single-user mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.18-6-486 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.18-6-486
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdc2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=87891495-45ac-4b5c-923c-3a1a07f52dd1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdc2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=87891495-45ac-4b5c-923c-3a1a07f52dd1 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 8.10, kernel 2.6.27-3-rt (on /dev/sdc2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.27-3-rt root=UUID=87891495-45ac-4b5c-923c-3a1a07f52dd1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-3-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 8.10, kernel 2.6.27-3-rt (recovery mode) (on /dev/sdc2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.27-3-rt root=UUID=87891495-45ac-4b5c-923c-3a1a07f52dd1 ro single 
initrd		/boot/initrd.img-2.6.27-3-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 8.10, memtest86+ (on /dev/sdc2)
root		(hd3,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by caljohnsmith on 2008-11-24
So which OS entry in your Grub menu gives you the error 22? Do all the entries result in a Grub error 22? Since you have multiple drives, most likely your problem is a result of how your drives are ordered in the BIOS boot order; on start up, Grub sees the order of drives as the BIOS boot order, not as how the drives are ordered in Ubuntu's/Etch's /dev directory. So when your Etch entries in the menu.lst use (hd1,1), that means Etch needs to be on the 2nd boot drive for Grub to find Etch and boot it correctly. In other words, (hd1) is not necessarily the sdb drive, which is what the Grub installer has to assume since it has no way of knowing your BIOS boot order; (hd1) is simply the 2nd drive in your BIOS boot order.

The bottom line is that you can probably fix your problem as follows: when you get the Grub menu on start up, select an entry that gives you the Grub error, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change the X to be either 1, 2, 3, or 4 (but not zero in your case), press return to save the change, then press "b" to boot. You'll have to try all those values of X until you find which works. That assumes that the other parts of the menu.lst are correct, which is usually a safe assumption. Note that the above change is not permanent, so once you find the (hdX,Y) that works, you'll need to modify your menu.lst to make it permanent. Give that a shot and let me know how it goes. :)

---

### Post by krokodil on 2008-11-24
I used to have an Ubuntu install on the now Etch drive, and that's how I used to fix it, but now I don't even get to the Grub menu.

It just says Grub 1.5 loading or whatever and then Error 22 and freezes there, can't get any further.

---

### Post by caljohnsmith on 2008-11-24
OK, getting that Grub error 22 before seeing the Grub menu is most likely also a result of how your multiple drives are ordered in your BIOS boot order, because you have Grub installed to the MBR of a drive other than the drive that contains Grub's boot files. I think the easiest solution for your problem is if you install Grub to the MBR (Master Boot Record) of your Etch drive (sdb), and then change your BIOS to boot the Etch drive on start up. Then you should get the Grub menu on start up, and booting the OSes should not be difficult to get working either; just follow my previous instructions for modifying the Grub entries on start up, but use (hd0,1) to boot any of the Etch entries. 

To install Grub to the MBR of the Debian drive, you can do the following (assuming fdisk shows Etch is on sdb):
```
sudo grub
grub> root (hd1,1)
grub> makeactive
grub> setup (hd1)
grub> quit
```
How about giving that a shot and letting me know how it goes.

---

### Post by krokodil on 2008-11-24
Thanks, that did the trick.

Can I ask how you knew to use hd1?

---

### Post by caljohnsmith on 2008-11-24
> **krokodil said:**
> Thanks, that did the trick.

Can I ask how you knew to use hd1?
Glad to hear you can boot OK now. About using (hd1), when you are in Linux running Grub commands, then Grub will see the order of drives as the same as they are ordered in the /dev directory (unless you specifically tell Grub otherwise), so that;
```
(hd0) = sda
(hd1) = sdb
(hd2) = sdc
...etc
```
But the Grub on start up is totally different, because it sees the order of drives as:
```
(hd0) = 1st boot drive
(hd1) = 2nd boot drive
(hd2) = 3rd boot drive
...etc.
```
So when you did those Grub commands while in linux, (hd1) would be sdb or your Debian drive. But on start up, since you changed your BIOS to boot your sdb drive first, then Debian is located on (hd0), or the first boot drive. That's why your entry for Debian in the menu.lst should use (hd0) and not (hd1).

Anyway, cheers and have fun with your distros. :)

---

