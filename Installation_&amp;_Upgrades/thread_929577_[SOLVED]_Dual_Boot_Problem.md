---
title: "[SOLVED] Dual Boot Problem"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by gavmoulds on 2008-09-25
Hi everyone. I am completely new to this and have followed some instructions on installing and dual booting with my current xp installation.

Everything seems to have gone well except that I can no longer boot my xp.

It is listed as an option in the 'post' screen.

I can select it..press return..and nothing happens..it hangs with the message

Starting and a flashing cursor.

I am at the end of my patience having just lost everyrting to vista which is why i chose to return to xp and dual boot.

Please give all answers in total novice terms.

---

### Post by WWSmith36 on 2008-09-25
Do you have Windows installed on a separate hard drive than Ubuntu?
Please provide more information including
```

sudo fdisk -l
```

---

### Post by Elfy on 2008-09-25
Can you also post the menu list, run this in a terminal

```
cat /boot/grub/menu.lst
```

Paste command into the terminal and press enter, terminal in accessories menu.

---

### Post by WWSmith36 on 2008-09-25
Sorry, in novice terms

Open up a Terminal with Applications -> Accessories -> Terminal and type

```
sudo fdisk -l

cat /boot/grub/menu.lst
```

Paste the results of this output and we will be able to help you.

---

### Post by gavmoulds on 2008-09-25
> **WWSmith36 said:**
> Sorry, in novice terms

Open up a Terminal with Applications -> Accessories -> Terminal and type

```
sudo fdisk -l

cat /boot/grub/menu.lst
```

Paste the results of this output and we will be able to help you.


 menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=22be2789-7fcb-4538-af0c-565c31282a78 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=22be2789-7fcb-4538-af0c-565c31282a78 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=22be2789-7fcb-4538-af0c-565c31282a78 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
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

gavmoulds@gavmoulds2:~$

---

### Post by Elfy on 2008-09-25
we're going to need the other one as well - open the terminal again and run

```
sudo fdisk -l
```

---

### Post by gavmoulds on 2008-09-25
Too late..its completely gone now.

Nothing will boot it says error 22

---

### Post by Elfy on 2008-09-25
Well you can deal with it but you are going to need the cd you installed ubuntu with.

You need to let the pc boot with that and then once it has started got to the terminal and run the ```
sudo fdisk -l
```

---

### Post by gavmoulds on 2008-09-25
This is getting rediculous now.

Can I fix this or should I simply restart allover again.

---

### Post by Elfy on 2008-09-25
Yes you can fix it if you actually want to. Starting other threads in the hope that the information and actions needed won't work.

You have 3 threads about the same thing going on at the moment.

---

### Post by gavmoulds on 2008-09-25
Well at the moment nothing is working

---

### Post by Elfy on 2008-09-25
post 8 please

---

### Post by gavmoulds on 2008-09-25
> **forestpixie said:**
> Well you can deal with it but you are going to need the cd you installed ubuntu with.

You need to let the pc boot with that and then once it has started got to the terminal and run the ```
sudo fdisk -l
```

Its says:

here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give start and end in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by Elfy on 2008-09-25
Ok - can you paste the whole of the output in a post- use the mouse to select it and then you can use the middle button of your mouse to paste it.

I understand that it won't make much sense to you, but it will to me, we are going to have to paste some commands into your terminal later that are going to mean even less to you.

If you have questions about what we are going to do - ask them and I will try to help you understand. 

So for the moment run the command again and paste the output for me to read, also don't go of to the other thread or no-one will know what's going on.

One step at a time and we will get there - ok :)

---

### Post by gavmoulds on 2008-09-25
> **forestpixie said:**
> Ok - can you paste the whole of the output in a post- use the mouse to select it and then you can use the middle button of your mouse to paste it.

I understand that it won't make much sense to you, but it will to me, we are going to have to paste some commands into your terminal later that are going to mean even less to you.

If you have questions about what we are going to do - ask them and I will try to help you understand. 

So for the moment run the command again and paste the output for me to read, also don't go of to the other thread or no-one will know what's going on.

One step at a time and we will get there - ok :)

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$

---

### Post by Elfy on 2008-09-25
you typed the command and put 1 instead of l I suspect. But you've got the information in your other thread so perhaps you should follow that one instead.

---

### Post by gavmoulds on 2008-09-25
> **forestpixie said:**
> you typed the command and put 1 instead of l I suspect. But you've got the information in your other thread so perhaps you should follow that one instead.

Ive got no reply in the other thread

---

### Post by gavmoulds on 2008-09-25
Can someone please tell me how to get my windows xp back again.

It is on the hard disk but it will not boot and even so I cannot access grub.

I am currently booting from the live cd. I have learned that much

There must be an easier way than going through all this crap

---

### Post by Elfy on 2008-09-25
Ok the fdisk output in the otherthread shows that you don't have a linux partition.

The question now is how did you install ubuntu - did you do it when windows was running?

If you didn't do that, then you have managed to lose ubuntu. If that is the case you will have to start the pc with your xp cd and use the recovery console and fixmbr with that.

> Ive got no reply in the other threadwe're volunteers perhaps the people looking at it are doing something else

> There must be an easier way than going through all this crapCut the attitude please.

---

### Post by gavmoulds on 2008-09-25
> **forestpixie said:**
> Ok the fdisk output in the otherthread shows that you don't have a linux partition.

The question now is how did you install ubuntu - did you do it when windows was running?

If you didn't do that, then you have managed to lose ubuntu. If that is the case you will have to start the pc with your xp cd and use the recovery console and fixmbr with that.

we're volunteers perhaps the people looking at it are doing something else

Cut the attitude please.

Sorry but I have really had enough here.

I have tried fixmbr and fixboot with windows but it still keeps coming back to a ubuntu/grub problem.

Why cant I simply access the original partition with my xp on it.

I dont care an longer about ubuntu...to be frank it is causing me undue stress to say the least.

I cannot believe that a system so destructive exists

---

### Post by meierfra. on 2008-09-25
> I have tried fixmbr and fixboot with windows but it still keeps coming back to a ubuntu/grub problem.

What error messages are you currently getting during boot up?
Does the grub menu appear?

How old is your computer?

Do you have any valuable data which needs to be rescued?

Do you have more than one hard drive?

As far as you know, did you do anything which could have damaged the Ubuntu partition between time you started this  thread and the time you got   "grub error 22"?

---

### Post by gavmoulds on 2008-09-25
> **meierfra. said:**
> What error messages are you currently getting during boot up?
Does the grub menu appear?

How old is your computer?

Do you have any valuable data which needs to be rescued?

Do you have more than one hard drive?

As far as you know, did you do anything which could have damaged the Ubuntu partition between time you started this  thread and the time you got   "grub error 22"?

What else can I say. xp is listed and I can select it..it hangs...says 

Starting...cursor flashes.

I mean how many times can I explain it.

---

### Post by meierfra. on 2008-09-25
Try this:

Boot from the Ubuntu LiveCD.
(Edit: according to your third thread it looks like you are able to boot into Ubuntu again. So just boot into Ubuntu)

Enable the   "universe" repositories :

Systems-> Administration->Software Sources"
Click on the Box next to "Community-maintained Open Source Software (universe) 


Install testdisk and use it to rebuild the Windows boot sector:

Open a terminal and type


```
sudo apt-get update

sudo apt-get install testdisk

sudo testdisk /dev/sda

```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"

then quit testdisk and reboot.

---

### Post by gavmoulds on 2008-09-26
> **meierfra. said:**
> Try this:

Boot from the Ubuntu LiveCD.
(Edit: according to your third thread it looks like you are able to boot into Ubuntu again. So just boot into Ubuntu)

Enable the   "universe" repositories :

Systems-> Administration->Software Sources"
Click on the Box next to "Community-maintained Open Source Software (universe) 


Install testdisk and use it to rebuild the Windows boot sector:

Open a terminal and type


```
sudo apt-get update

sudo apt-get install testdisk

sudo testdisk /dev/sda

```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"

then quit testdisk and reboot.

Absolutely brilliant...I knew there would be a straight forward way to get this back running.

Worked great..did a repair install on the xp..fabulous..I am happy again

---

