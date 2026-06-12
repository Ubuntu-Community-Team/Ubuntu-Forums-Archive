---
title: "Another noob GRUB/Sata issue"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by squirrel_f13 on 2007-02-06
Hey all - first time linux user here. Very impressed at how easy Ubuntu was to install (except for this one issue) and how customizable and responsive it is.

Anyway - the issue:

I get this error if my 3rd SATA drive is attached on boot:

BusyBox
/bin/sh: can't access tty; job control turned off
(initramfs)

3 400Gb SATA drives are installed:

sda
sdb
sdc

I installed over a Windows Vista RC2 install - formatting the Vista partition and reformatting it as ext3 during the Live CD install. Once the install was complete and I rebooted I got a "Operating System Not Found. Insert Disk and Hit Any Key" error.

So I unplugged the SATA drives until I found a combo that allowed me to boot up - which is currently:

sda1 - ext3 boot partition
sda2 - extended
sda3 - Swap

sdb1 - NTFS (mounted through fstab addition)
sdb2 - ext3 partition of extra space (mounted)

So my 3rd SATA drive is the problem - it is a 400 gig drive with only about 18 gig free on it (movies and music) formatted in Vista as NTFS. If I reconnect it the system throws a GRUB error after post/Ubuntu splash. 

Current fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=70c8e737-6ce3-4771-beda-0db5e14c1a91 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8778fec1-259a-4755-8f86-5fe1e9b2757e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1    /media/sdb1 ntfs  nls=utf8,umask=0222 0    0
/dev/sdb2 /media/music ext3 defaults 0 0

```

What should I be looking to do to be able to hook up and mount the 3rd SATA drive?

EDIT: Also I have searched around to try and understand - just not sure if it's media.lst or another file I should be investigating?

---

### Post by confused57 on 2007-02-06
I don't know, but it might be just a matter of changing your hard drive boot order in bios...if it isn't already, change it to boot sda, sdb, then sdc, in that order.  I assume your sda is set to boot first, when you only have sda & sdb connected.  You might try setting sdc as the 3rd hard drive in your boot order, regardless of whether sda or sdb is first.

---

### Post by squirrel_f13 on 2007-02-06
Thanks for the quick response - I have tried that but in by BIOS the configuration menu of my Abit BIOS only allows me to specify that the SATA Bus is on the list, not specific drives hooked up. (Which I thought was odd?) 

EDIT: The error is actually a Busy Box v1.1.3 error, which I am having trouble finding info on...

---

### Post by squirrel_f13 on 2007-02-07
Hate to bump my own thread but I'm having a heck of a time finding info on this specific error and I can't figure out why it only happens when the 3rd drive is attached as most info I read about Busy Box seems unrelated?

---

### Post by confused57 on 2007-02-07
> **squirrel_f13 said:**
> Thanks for the quick response - I have tried that but in by BIOS the configuration menu of my Abit BIOS only allows me to specify that the SATA Bus is on the list, not specific drives hooked up. (Which I thought was odd?) 

EDIT: The error is actually a Busy Box v1.1.3 error, which I am having trouble finding info on...

Since you're not able to change your hard drive boot order, which is indeed unusual, post your entries to boot Ubuntu and Windows in your /boot/grub/menu.lst...what I'm thinking is that you might be able to try connecting your  data drive from sdc to sdb(& Windows drive to sdc), but it would involve making some changes to your fstab & grub menu...if it'll work at all.

```
gedit /boot/grub/menu.lst
```
menu.lst is short for menu.list

Just post the entries to boot Ubuntu & Windows, this will give an idea of where grub is actually installed.  As I mentioned, when your sdc is connected, I think it changes the way grub recognizes the order of your hard drives, i.e. sda may change from hd0 to hd1, etc.

---

### Post by squirrel_f13 on 2007-02-07
Thanks Confused! menu.lst below. Just to clarify - there is no Windows Install on this machine anymore. The problem drive is NTFS but should only have data - it was never a Windows boot drive (unless Vista adds something?) The drive called sda was the Vista install which I reformatted as ext3 using the Live CD prior to installing.

menu.lst

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=70c8e737-6ce3-4771-beda-0db5e14c1a91 ro
# kopt_2_6=root=/dev/sda1 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

```

Also, have modified my fstab slightly - backed up the sdb1 ntfs partition and reformatted it as well:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=70c8e737-6ce3-4771-beda-0db5e14c1a91 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8778fec1-259a-4755-8f86-5fe1e9b2757e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1 /media/moviebox ext3 defaults 0 0

```

Thanks!

---

### Post by confused57 on 2007-02-07
I suppose your sda drive with Ubuntu will boot, if it's the only drive connected...this would mean that grub was installed to the sda mbr.

If you get a grub menu when all 3 drives are connected, you could highlight the entry to boot Ubuntu, press "e" to edit and change root (hd0,0) to root (hd1,0) & if that doesn't work, then root (hd2,0).  This would be the easiest to try first since your kernel points to /dev/sda1.

I'm really fumbling for an answer to help you, but if the above doesn't work, i.e. you're not getting a grub menu at all with all 3 drives connected, you could try switching your Ubuntu drive to sdc & your current sdc drive to sda & if you get a grub menu, press "e" to edit, & change the line in the kernel to root=/dev/sdc, & press "b"(I think that's correct) to boot.

On second thought the latter suggestion would be more difficult, because of the mountpoint s in /etc/fstab, which is currently sda for root & swap, would need to be changed also...I've never tried this myself, so you might want to wait for someone else to guide you.   I believe the first suggestion would be the best way to proceed...forget I even mentioned the other one.



Since you're not able to change the boot order in bios, the above is all that I can think of to try at the moment.  None of the above is permanent, but if you find a combination that works then you can make it permanent in your /boot/grub/menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Good luck with it, there's plenty of knowledgable people here...hopefully someone else can help you more than I can.

Found this thread with the same issue:
[http://ubuntuforums.org/showthread.php?t=292533&page=3](http://ubuntuforums.org/showthread.php?t=292533&page=3)

---

### Post by squirrel_f13 on 2007-02-07
Well I resolved it by switching the SATA cables clockwise, rebooting, error, switch, reboot, error, switch, reboot SUCCESS. Thank god. Thanks for your help - bed now :P

---

### Post by confused57 on 2007-02-07
> **squirrel_f13 said:**
> Well I resolved it by switching the SATA cables clockwise, rebooting, error, switch, reboot, error, switch, reboot SUCCESS. Thank god. Thanks for your help - bed now :P

Third time's usually a charm, believe you got it working in spite of my feeble attempts to help.
Looks like boot order & grub may have been the problem, when you connected the 3rd drive?

Added:  I forgot to mention, you might want to look at this section in your /boot/grub/menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)

If there is a kernel upgrade, this is where update-grub looks for your root device, i.e. if you ended up with Ubuntu on something other than sda, it'd need to be changed accordingly.

---

