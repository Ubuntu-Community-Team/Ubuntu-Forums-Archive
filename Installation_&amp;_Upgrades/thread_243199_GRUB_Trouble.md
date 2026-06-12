---
title: "GRUB Trouble"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by cleentrax on 2006-08-24
I can't install ubuntu! I have done probably a dozen installs previously, including a couple on this server, but I had to reformat the drives and start over.

Specific problems: The Live CD install crashes (can't write GRUB). The alternate install CD installs successfully, but upon reboot, the computer freezes at "GRUB _".

I have tried to do a rescue with the Live CD, and reinstall GRUB from there, but no dice. I can see the drives, but I can't boot.

What next?

---

### Post by Iarwain ben-adar on 2006-08-24
Hi,
can you tell me what grub throws at you when you try to reinstall?


Iarwain

---

### Post by randell6564 on 2006-08-24
I'm trying to reinstall grub.

How do you use the live cd to reinstall grub?

---

### Post by Iarwain ben-adar on 2006-08-24
Hi,
normally you do this:
```
 #boot via live cd
#open a console
sudo fdisk -l
sudo mkdir /rec
sudo mount -t ext3 /dev/hdXX    #this is the linux partition, see the output of fdisk -l
sudo grub
grub> find /boot/grub/stage1
grub> root (hdx,y)     #here you put the output of the 'find' command
grub> setup (hd0)     #if you want to install grub to your mbr
grub> quit
exit
```

And if this doesn't work, we have to change your menu.lst i think :D


Iarwain

---

### Post by randell6564 on 2006-08-24
> **Iarwain ben-adar said:**
> Hi,
normally you do this:
[code] #boot via live cd
#open a console
sudo fdisk -l
sudo mkdir /rec
sudo mount -t ext3 /dev/hdXX    #this is the linux partition, see the output of fdisk -l
sudo grub
grub> find /boot/grub/stage1
grub> root (hdx,y)     #here you put the output of the 'find' command
grub> setup (hd0)     #if you want to install grub to your mbr
grub> quit
exit[code]

And if this doesn't work, we have to change your menu.lst i think :D


Iarwain

Hello My Friend!  I know that you know what you are describing, but it is all greek to me!

Please allow me to fill you in on how I came to hit this wall!

I have been using ubuntu dapper for a long time.

I have dapper on my 120GB Ide master, and a 20GB Ide slave (FS Ext3), as a storage drive for my music.

I decided that I wanted to install the Ubuntu C.E. (Christian Edition) onto my 20GB slave, so I transfered all my music over to Hda1 and installed C.E. onto Hdb1.

Now I have two WORKING OS's, but cannot boot to either one without the live cd!

I'm guessing that grub needs to be reinstalled to the MBR, but I dont know how to do this.  

Is that clear?  Anything that you might need me to post, just ask and you got it!

For now, here is my fdisk -l

[B]bigboss@bigboss-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14759   118551636   83  Linux
/dev/hda2           14760       14946     1502077+   5  Extended
/dev/hda5           14760       14946     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2377    19093221   83  Linux
/dev/hdb2            2378        2482      843412+   5  Extended
/dev/hdb5            2378        2482      843381   82  Linux swap / Solaris[/B]

Thanks!

---

### Post by Iarwain ben-adar on 2006-08-24
Hi, no problem :D

Could you please post the contents of your menu.lst ?
(do you know how to access it?)

PS. can you make a new thread please, because i don't think cleentrax would be happy if he'd look at the thread thinking his problem is to be solved, only to find yours :D


Iarwain

---

### Post by randell6564 on 2006-08-24
> **Iarwain ben-adar said:**
> Hi, no problem :D

Could you please post the contents of your menu.lst ?
(do you know how to access it?)

PS. can you make a new thread please, because i don't think cleentrax would be happy if he'd look at the thread thinking his problem is to be solved, only to find yours :D


Iarwain

Sure!  But I forgot where my menu.lst is! lol!  I thought it was 'sudo gedit /boot/menu.lst' but there was nothing there refering to menu!

I'll post a new thread as, 'Help with grub'

---

### Post by randell6564 on 2006-08-24
Hey, I posted a new thread.  Here is my menu.lst just in case!

[B]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST[/B]

Sorry for hijackin' this thread!

---

### Post by cleentrax on 2006-08-24
> **Iarwain ben-adar said:**
> Hi,
can you tell me what grub throws at you when you try to reinstall?


Iarwain

Well, when I reinstall with the Live CD, it crashes, saying it can't write to the disk. When I do the alternate CD, it installs fine, and when I do the first reboot, when it gets to Grub, it just says GRUB and freezes. That's it.

---

### Post by randell6564 on 2006-08-24
It didn't work my friend!

Dont know what the hell it could be!  Maybe I'll just wipe the drive and reinstall both OS's!

Although.,I kinda like the way it's set up!  You cant boot into either OS unless you have the live cd.

So., without it, I'm the king!  No one can get in!  AH shi#! they're gonna hate me! lol!

---

### Post by Iarwain ben-adar on 2006-08-24
The "can't write to disk" i think i know why :D

Did you mount your / ?


Iarwain

---

### Post by cleentrax on 2006-08-24
> **Iarwain ben-adar said:**
> The "can't write to disk" i think i know why :D

Did you mount your / ?


Iarwain

Well... No. But I shouldn't have to if I've wiped the drive and installing straight from the CD, should I?

EDIT: I think I see what you're saying -- perhaps / is mounted, and shouldn't be... I'll take a look, but I don't think so.

---

### Post by Iarwain ben-adar on 2006-08-24
No, then you shouldn't :D

Are the devices mounted? (just another stupid question... it's late :D )

And when you install with the alternate CD, it installs?

When it is installed, try booting with the live-cd, and reinstall grub
(you might better first look if you have a non-blank /boot/grub/menu.lst file)


Iarwain

---

### Post by cleentrax on 2006-08-24
Here's what fdisk says about the drive:

Disk /dev/hdi: 18.0 GB, 18042716160 bytes
255 heads, 63 sectors/track, 2193 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdi1   *           1        2100    16868218+  83  Linux
/dev/hdi2            2101        2193      747022+   5  Extended
/dev/hdi5            2101        2193      746991   82  Linux swap / Solaris


> you might better first look if you have a non-blank /boot/grub/menu.lst file

How do I do that without mounting the drive?

---

### Post by randell6564 on 2006-08-24
GO TO BED Iarwain! lol!

---

### Post by Iarwain ben-adar on 2006-08-25
> **randell6564 said:**
> GO TO BED Iarwain! lol!

Been to bed :D
Back again...

Now, cleentrax:

If you installed via alternate cd, the system is installed, right?

Is this then what you do? :
Boot up (not via live/install/alternate cd), and get a grub console?
```
grub>
```

Because if you do, then there is little problem to finally boot your system
(atleast with my pc it was like that :D )


Iarwain

---

### Post by cleentrax on 2006-08-25
> **Iarwain ben-adar said:**
> Been to bed :D
Back again...

Now, cleentrax:

If you installed via alternate cd, the system is installed, right?

Is this then what you do? :
Boot up (not via live/install/alternate cd), and get a grub console?
```
grub>
```

Because if you do, then there is little problem to finally boot your system
(atleast with my pc it was like that :D )


Iarwain

Not quite. It's not a grub console. It's a frozen GRUB.

---

