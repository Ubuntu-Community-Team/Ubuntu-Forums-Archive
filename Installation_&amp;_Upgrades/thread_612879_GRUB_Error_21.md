---
title: "GRUB Error 21?"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by hep2103 on 2007-11-14
So first things first...I am a total Linux neophyte, so be gentle, but I am completely fed up with Windows and prepared (now that Wine supports my favorite games...) to make the final switch...only one problem.

Also, I've looked all over the web for this problem, but haven't been able to find a solution that makes any sense. Help please!

So I've tried two things, both returning the same error. First, I tried partitioning my Windows HD and installing Ubuntu. Everything went smoothly until reboot, when I got "GRUB error 21." No luck at all, had to delete everything on the Linux partition just to get Windows to work again.

Then I tried something else- I unplugged that HD, and got another with an old Windows install on it, and totally overwrote everything on it with an Ubuntu installation. But...same error.

What the hell is going on? Do both HD's have some deep record of their past Windows lives that is preventing me from running Ubuntu? Could there be an error on the install CD? Is it because I am trying to use 7.04?

I would really love to get Ubuntu running, as even my brief exposure to it on LiveCD convinced me that Windows is utterly useless. Please help!

My system:

Intel Core2Duo E6300
MSI p965 Neo-F
2x1024MB PC2-5300
NVidia GeForce 7600 GS
etc, etc

Again, I'm a tyro... thanks in advance for any help!

hep2103

---

### Post by az on 2007-11-14
Error 21 means that your motherboard bios has a bug.  When you boot your computer, it loads the bootloader from the MBR and executes that code to be able to find the operating system and run it.  In this case, it is not able to locate the hard disk.  There is a file that maps the devices for grub for situations like this.

Boot the live cd, and browse the disk onto which you installed Ubuntu.  Look in /boot/grub for the device map.  You will need to change the hd(0,1) to hd(1,1) in most cases so that it can find the hard drive.  You will need to edit the file as root, so run

sudo gedit 

from the command line and don't forget to save the file.

If that still doesn't work, post back.

---

### Post by meierfra on 2007-11-14
To figure out what is going on and to be able to help you, I need some information. Boot from the Ubuntu Live CD  and open a terminal. (To open a terminal go to Applications->Accessories->Terminal)

Type 

```
sudo fdisk -l
```
( the "l" is a lower case L)

Copy the output and post it here.

---

### Post by hep2103 on 2007-11-14
No luck...

First, I couldn't find "device.map" when I was browsing within gedit, even though I could navigate there with the browser. I checked the "grub" folder properties and found it was actually in "media/boot." Don't know if that makes a difference.

First try, I changed device.map from hd(0) to hd (1,1). This resulted in errors during shutdown, and no luck booting up. So I tried just hd(1) to match the previous format. This time, shutdown was fine, but the same error 21. Ideas?

Many thanks- I can tell just from the ease of fiddling in ubuntu versus windows that this will all be worth it...

hep2103

---

### Post by hep2103 on 2007-11-14
Here's the result of sudo fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris

---

### Post by melisandre on 2007-11-14
Have the same problem... (and am doing the same switch) I thought it was because I have an NTFS and an EXT2 (or whatever it's called, I think that's it) partition on the same hard drive... might that be a problem?

Thanks,
Melisandre

---

### Post by hep2103 on 2007-11-14
If so, I would have no clue as to how to diagnose or fix it...

hep2103

---

### Post by meierfra on 2007-11-14
fdisk looks normal, so we have to dig deeper. 


1) Do you have more than one hard drive plugged in, or just one?

2) Open the file "menu.lst"   and post it here (according to your second post  the file should be in 

/media/boot/grub

---

### Post by melisandre on 2007-11-14
sudo fdisk -l gives me:
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        4454    35736592+   7  HPFS/NTFS
/dev/sda3            4455        4862     3277260   db  CP/M / CTOS / ...

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0fa2ddae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11808    94847728+   7  HPFS/NTFS
/dev/sdb2           11809       19395    60942577+  83  Linux

I have two hard drives.

Upon putting "/media/boot/grub/menu.lst" in Terminal I get
bash: /media/boot/grub/menu.lst: No such file or directory

---

### Post by meierfra on 2007-11-14
melisandre: I will respond to your "fdisk" in the thread you started yourself. Your case is different and it's better to keep things separate.

---

### Post by melisandre on 2007-11-14
ok thanks

---

### Post by hep2103 on 2007-11-15
Sorry it has taken me so long to respond, I'm in midterms... I should be around all day though.

To answer your questions, meierfra:

1) Right now, I only have one HD plugged in, and manually swap the cables when I want to switch between OSes. Once I am confident in Ubuntu I will partition my Windows drive, but until then I am running this as a "separate," all-Linux system.

2)

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
# kopt=root=UUID=24bf5e42-1a55-4241-87f4-3d00f97ad0e9 ro

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=24bf5e42-1a55-4241-87f4-3d00f97ad0e9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=24bf5e42-1a55-4241-87f4-3d00f97ad0e9 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



Many thanks all!

hep2103

---

### Post by Gwendolyn on 2007-11-15
I've been having the exact same problem. I'm about ready to just thrown windows XP back on there. *cry*

---

### Post by meierfra on 2007-11-15
hep2103:

Try  this

 Edit the file "menu.lst"

change "timeout 3" to "timeout 10"

and 

"hiddenmenu"  to "#hiddenmenu"

(This won't fix your problems, but I want to see whether the grub menu appears at boot-up)

Next: In a terminal type

sudo grub

you will get a "grub>" prompt

type

root (hd0,0)

setup (hd0)

quit

This reinstall grubs (the boot loader) and might solve your problem, but I'm not sure.

Reboot and let my know whether anything changed.

---

### Post by hep2103 on 2007-11-18
No change- same old error. Sorry it took me so long- I didn't realize there had been a reply. I'm around all day, though.

Thanks-

hep2103

---

### Post by meierfra on 2007-11-18
Sorry I have no clue what is going on.

Did you get any error messages during "sudo grub - root (hd0,0) - setup (hd0) - quit"?

You might try that again, but before "quit" copy the content of the terminal and post it here.

Googling I  found a couple of people who solved a similar problem by  creating a small boot  partition. But I really don't know why that would make a difference. So I'm hesitant to recommend it. On the other hand since you have a fresh install, it wouldn't  really hurt to try.

But I would wait a little bit and see whether anybody else comes along with a better suggestion.

---

### Post by meierfra on 2007-11-18
Just noticed that I never recommended Super Grub: [Hermanzone Info on Super Grub]("http://http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by teryowen on 2007-11-18
edit: my apologies, sorry for the confusion.

---

### Post by hep2103 on 2007-11-18
In which file can i find the "root" and "kernel" lines?

---

### Post by meierfra on 2007-11-18
hep2103:  You can ignore the advice from teryowen.  He is mixing up your case with  melisandre's

---

