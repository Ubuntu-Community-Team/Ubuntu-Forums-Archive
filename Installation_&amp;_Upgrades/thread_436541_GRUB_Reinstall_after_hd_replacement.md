---
title: "GRUB Reinstall after hd replacement"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by oddcarout on 2007-05-07
OK. I had a perfectly working system. Didn't really have problems installing.

My old windows drive died. I installed a new drive and need to reinstall grub. I read somewher e that i only needed to use the live cd. But how?

I am running off the live CD and don't know where to go from here. Please help.

How do I reinstall the grub loader?

Thanks

---

### Post by psusi on 2007-05-07
What is your system configuration?  Do you have two hard drives?  Is ubuntu installed on the second, with windows on the first?  What is the output of sudo fdisk -l?

---

### Post by oddcarout on 2007-05-07
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4188    33640078+  83  Linux
/dev/hda2            4189        8159    31897057+  83  Linux
/dev/hda3            8160        8323     1317330   82  Linux swap / Solaris
/dev/hda4            8324        9729    11293695    7  HPFS/NTFS

---

### Post by psusi on 2007-05-08
You seem to have two linux partitions on the one disk.  How do you have the linux partitions set up?  Which one did you use as the root?  Did you use the other as /boot or as /home?

---

### Post by confused57 on 2007-05-08
Here's how to reinstall grub using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by oddcarout on 2007-05-08
hda1 /root
hda2 /home

---

### Post by psusi on 2007-05-08
So right now the computer is booting from the windows drive and loads windows just fine?  Then this is what you need to do:

sudo grub
device (hd0) /dev/sda
device (hd1) /dev/hda
root (hd1,0)
setup (hd0)

---

### Post by oddcarout on 2007-05-09
ok having a problem booting...

mounting root file system
waiting for root file system...... it hangs here.

Now what can I do?????????

thanks.

---

### Post by confused57 on 2007-05-09
Does Windows  boot when selecting the Window's entry in grub?

Added:  Did you try to reinstall grub, using the live cd, from the instructions in the link I provided earlier?
If you can't boot either Windows or Ubuntu, boot the live cd & mount your Ubuntu root partition:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu
```
then post your menu.lst:
```
gedit /media/ubuntu/boot/grub/menu.lst
```
and
```
gedit /media/ubuntu/boot/grub/device.map
```

Also, what does "find /boot/grub/stage1" return:
```
sudo grub
find /boot/grub/stage1
```

just enter "quit", without quotes, to exit the grub prompt.

---

### Post by oddcarout on 2007-05-09
I can boot into windows just fine from grub.

should I still follow your last post?


Z

---

### Post by confused57 on 2007-05-09
> **oddcarout said:**
> I can boot into windows just fine from grub.

should I still follow your last post?


Z

Yes, it "might" tell us what the problem is.

---

### Post by psusi on 2007-05-09
What does your /boot/grub/menu.lst look like?

---

### Post by oddcarout on 2007-05-09
this is my menu.lst

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
default		6

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
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-28-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by oddcarout on 2007-05-09
device.map

```
(hd0)	/dev/hda
(hd1)	/dev/hdb

```

---

### Post by spankymasterc on 2007-05-09
if im correct when the grub starts press E on the ubutu kernel you want to run then click E once more then change the (h1,0) to (0,1) the press B now if that works you will have to change it in the grub menu when it boots.....

---

### Post by oddcarout on 2007-05-10
no dice....

still hangs in waiting for root..


```
 sudo grub
find /boot/grub/stage1 
```

(hd0,0)

Z

---

### Post by confused57 on 2007-05-10
> **oddcarout said:**
> no dice....

still hangs in waiting for root..


```
 sudo grub
find /boot/grub/stage1 
```

(hd0,0)

Z

Are you sure "find /boot/grub/stage1" returned "root (hd0,0)"?...this is contradictory to what your /boot/grub/menu.lst shows.

You can try installing grub to your Ubuntu drive mbr, then set your bios to boot your Ubuntu drive before your Windows drive, then temporarily modify the line with root to (hd0,0):
```
sudo grub
find /boot/grub/stage1
```
whatever this returns, e.g. "root (hdx,y)", then you'll enter the following to install grub to Ubuntu's drive:
```
root (hdx,y)
setup (hdx)
quit
```

Then set your bios to boot your Ubuntu drive before your Window's drive, you "should" get a grub menu at boot, if you do, highlight your Ubuntu entry, press "e", change root to (hd0,0), then press "b" to boot.
This change is temporary, but maybe it will boot your Ubuntu installation...if it does, the changes can be made permanent and an entry added to boot Windows.

This may not work, but worth a shot.

Another thing I noticed and it may not be the problem is that your Ubuntu root partition does not have the bootflag set to on(*).  One way to turn it on is with the gparted live cd:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
it's only a 45 Mb download & is an excellent partitioning utility for Linux...
It's possible this may be your problem...maybe someone else can give you an idea.

---

### Post by psusi on 2007-05-10
The problem is not with grub, but with the kernel.  It is being told to use /dev/hdb1 as the root, which you don't have, so it can never find it.  Change the root= to /dev/hda1 on the line:


kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb1 ro quiet splash

---

### Post by confused57 on 2007-05-10
> **psusi said:**
> The problem is not with grub, but with the kernel.  It is being told to use /dev/hdb1 as the root, which you don't have, so it can never find it.  Change the root= to /dev/hda1 on the line:


kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb1 ro quiet splash

Good catch...after looking a little more closely at his "sudo fdisk -l", that should be a simple fix...

---

### Post by oddcarout on 2007-05-10
I figured that out last night. got all the hdb taken care of.

Now I am having the problem while booting of it looking for fsck.ext3 on hdb2. 

any ideas.
I had everything set to how I wanted it don't really want to reinstall.

Thanks

---

### Post by confused57 on 2007-05-10
> **oddcarout said:**
> I figured that out last night. got all the hdb taken care of.

Now I am having the problem while booting of it looking for fsck.ext3 on hdb2. 

any ideas.
I had everything set to how I wanted it don't really want to reinstall.

Thanks
You probably need to change mountpoints in your /etc/fstab, you'll need use the live cd to mount your root partition:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu
gedit /media/ubuntu/etc/fstab
```
Post the output of your /etc/fstab, or if you feel confident editing:
```
cd /media/ubuntu/etc
sudo cp fstab fstab_backup
gksudo gedit /media/ubuntu/etc/fstab
```

You probably need to change all hdb entries to hda.

---

### Post by psusi on 2007-05-10
Yea, your /etc/fstab probably also lists /dev/hdb instead of hda for your root partition.

---

### Post by Books on 2007-06-11
Oooops! Sorry... I was posting to another thread and accidentally posted to this one.

These aren't the droids you're looking for... carry on.

---

