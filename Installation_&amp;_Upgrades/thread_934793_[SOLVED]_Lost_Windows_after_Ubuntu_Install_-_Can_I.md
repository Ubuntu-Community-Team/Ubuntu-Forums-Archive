---
title: "[SOLVED] Lost Windows after Ubuntu Install - Can I get it back dual?"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by athrpf on 2008-10-01
Hey everyone,

just until two days ago I had only Windows XP running on my machine. I had another free partition to spare, so I decided to install ubuntu. I had read in the dual boot section that it would automatically detect my windows and set up a dual boot. After booting, however, my windows booting ability is gone. The computer automatically starts ubuntu and the only possibilities that the boot manager gives me upon hitting Esc are ubuntu related (recovery etc.). 

(I suppose the problem for ubuntu to not see my windows installation could have been, that it was on a logical partition which was E:\ in windows)

Windows is still fine, sitting in its partition, that I can access from linux. Is there any way I can get this windows running again without having to reinstall windows or linux? 

I tried using testdisk, as was discribed in 
[http://ubuntuforums.org/showthread.php?t=934371&highlight=windows+dual+boot](http://ubuntuforums.org/showthread.php?t=934371&highlight=windows+dual+boot)
to revive the windows boot sector, but that didn't help at all. 

Is there anybody out there who can help me with this?

---

### Post by lisati on 2008-10-01
It is possible (but not absolutely certain) that you deleted Windows from your computer. In order for us to help you find it (assuming it's still there) could you please run the following in the terminal (it's on the Applications->Accessories menu) and post the output:
```
fdisk -l
```

---

### Post by athrpf on 2008-10-01
Thanks for the quick reply! This is fdisk -l :

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27062705

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        9729    78140160    f  W95 Ext'd (LBA)
/dev/sda5               2        4864    39062016    7  HPFS/NTFS
/dev/sda6            4865        7296    19535008+  83  Linux
/dev/sda7            7297        7539     1951866   82  Linux swap / Solaris
/dev/sda8            7540        9729    17591143+  83  Linux

Disk /dev/sdb: 4095 MB, 4095737344 bytes
255 heads, 63 sectors/track, 497 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           5       40131    0  Empty
/dev/sdb2               6         497     3951990    b  W95 FAT32

---

### Post by lisati on 2008-10-01
Sorry for the delay replying. I'm not sure exactly how to proceed, but it looks like there is a Windows partition on your system (SDA5) - was this a partition you set up for data? (Windows often likes to be set up first on a hard disk)

---

### Post by athrpf on 2008-10-01
Windows actually was installed before linux. While installing linux, i set a mount point to my windows partition to be able to access it from linux. But that cannot be the problem, because I installed linux twice, the first time without this mount point, and even then it did not recognize the Windows installation. 

What do you expect to happen, if I tried recovering the installation with a windows XP cd - would that kill my linux?

---

### Post by justsomedude on 2008-10-01
Your Windows seems to be still there, so let's get it to boot. :)

Please post the output of 
```

cat /boot/grub/menu.lst
```

---

### Post by athrpf on 2008-10-01
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
# kopt=root=UUID=0e10f559-350e-4a02-adc3-b8c8840a64b1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0e10f559-350e-4a02-adc3-b8c8840a64b1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0e10f559-350e-4a02-adc3-b8c8840a64b1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by justsomedude on 2008-10-01
Okay, we will have to add an entry for Windows to that list.

First, we create a backup of the menu.lst file:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Then, open menu.lst

```
sudo gedit /boot/grub/menu.lst
```


This may take several attempts to get it right. Add this:

```
title           Windows XP
root            (hd0,1)
savedefault
chainloader     +1
```

to the very bottom of the file, save it and reboot. If it works, fine. If not, we may have to modify that entry.

---

### Post by athrpf on 2008-10-01
Thanks for your help!
I'm sorry, it didn't work. When I tried to start Windows with the newly available boot option, it said:

Error 22: No such partition 

What should I change?

---

### Post by justsomedude on 2008-10-01
Like I said, we may need several attempts. Let's try it like this:

```
title           Windows XP
root            (hd0,4)
savedefault
chainloader     +1
```

---

### Post by lisati on 2008-10-01
justsomedude beat me to suggesting another change to try (I'm 'running' between browsing the forums and getting an XP installation back on track after running amuck)

---

### Post by athrpf on 2008-10-01
That seemed to be a hit, but I probably have a problem now. I got:

NTLDR is missing

and had to reboot. Any ideas?

---

### Post by Bucky Ball on 2008-10-01
Not a fix, but in your menu.lst, change these settings:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```to:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout        30**

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**# hiddenmenu**
```Your boot menu is hidden so you don't rightly know if grub is giving you the option to choose Windoze anyhow. :)

Rule of thumb: install windoze first. It wants the first available primary partition (as far as I know won't boot from logical without serious tweaking).
Do the changes I have outlined and have a look at the grub and possibly you can try a few edits from there.

---

### Post by Sef on 2008-10-01
> 'm sorry, it didn't work. When I tried to start Windows with the newly available boot option, it said:

Error 22: No such partition 
This is GRUB error 22:

> No such partition - This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.       Your Windows is on sda5 instead of sda1.  I'm not sure what Windows should be listed as.  Could try hd0,2 and so on till one works, but not sure of a better answer.

Update: Try downloading [super grub disk ]("http://supergrubdisk.org")and see if that works.

---

### Post by justsomedude on 2008-10-01
We have to find out if Windows is installed to your first or second hard drive.

Could you open the file manager and take a look where Windows "root" partition (I know, Windows has no root partition. I mean the partition where the *\programs* folder and all that jazz resides) is?

This could be a b*tch, we may have to use *map* parameters. But we'll get there...

Oh, and we take another swing with:

```
title           Windows XP
root            (hd1,1)
savedefault
chainloader     +1
```

Woot! :D

---

### Post by Bucky Ball on 2008-10-01
Windoze will be on the one below Ubuntu - hd0,4

You take the sda partition number and minus 1 for hd partition number. hd starts from 0, sda from 1. :)

So, change it to hd0,4 and give that a go.

---

### Post by athrpf on 2008-10-01
justsomedude, thanks for all your help

The Program files and WINDOWS folder are in /windows/Program Files and /windows/WINDOWS (is that what you wanted to know?). I set the mount point for that partition to /windows when I installed linux. I will try the (hd1,1) now.

---

### Post by justsomedude on 2008-10-01
> **athrpf said:**
> 
The Program files and WINDOWS folder are in /windows/Program Files and /windows/WINDOWS (is that what you wanted to know?). I set the mount point for that partition to /windows when I installed linux. 

Not exactly. I was dumb, we can easily find out where this partition is with 
```

cat /etc/fstab
```

---

### Post by athrpf on 2008-10-01
(hd1,1) didn't work either, it just said

starting up ...

and a curser blinked forever. 

now the output for cat /etc/fstab :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=0e10f559-350e-4a02-adc3-b8c8840a64b1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=1bb3b796-296e-4626-91f5-149950989b13 /home           ext3    relatime        0       2
# /dev/sda5
UUID=9E6C8F276C8EF8F3 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=4770b085-f0d1-4d33-9d30-0115201ad674 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Bucky Ball on 2008-10-01
> **justsomedude said:**
> Like I said, we may need several attempts. Let's try it like this:

```
title           Windows XP
root            (hd0,4)
savedefault
chainloader     +1
```

That's what I been sayin' because hd0,4 is what the partition is. athrpf, read my previous two posts :)

---

### Post by justsomedude on 2008-10-01
Hm, strange. cat /etc/fstab tells us it's sda5.

This should have worked with 

```
title           Windows XP
root            (hd0,4)
savedefault
chainloader     +1
```

but it didn't.

What exactly did you do with testdisk?

Oh yes, Supergrubdisk metioned by Sef is well worth a shot, too.

---

### Post by Bucky Ball on 2008-10-01
Try this:

```
title           Windows XP
root        (hd0,4)
savedefault
**makeactive**
chainloader     +1
```

---

### Post by athrpf on 2008-10-01
Yes, I think (hd0,4) is the right choice too, I suppose I shouldn't have done the testdisk. What I did was follow the following instructions

After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens.

I probably killed the MBR entry for Windows with that. Google tells me for NTLDR to recover my MBR with the windows disk (which in turn would probably kill my linux boot). Is there a tool that revives windows while still leaving linux alone?

I will try getting super grub now

---

### Post by justsomedude on 2008-10-01
^^ And this:

```
title           Windows XP
rootnoverify    (hd0,4)
savedefault
chainloader     +1
```

I, justsomedude, known as Open Source Legend, hereby command Windows to boot! lol

---

### Post by Bucky Ball on 2008-10-01
[QUOTE=athrpf]I will try getting super grub now[/QUOTE]

Good choice. :)

There is a lot of good info on that site, along with this one:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by justsomedude on 2008-10-01
```
Is there a tool that revives windows while still leaving linux alone?
```

I'm not sure. I only used a Vista recovery disk once, which left other partitions alone. No clue if the XP recovery CD does the same thing.

I'd try the last to suggestions Bucky Ball and I gave you.

If you have to restore, remember you have access to your Windows partition from within linux, so **do a backup** first.

---

### Post by athrpf on 2008-10-01
Thanks alot guys! I will try the suggestions and I am confident that I will get this to work eventually

---

### Post by meierfra. on 2008-10-01
It seems that you  deleted a partition when you installed Ubuntu, and that this partition contained  the boot files for XP. 

To fix your problem: Download the following archive to your Desktop:


[http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573]("http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573")

(The archive contains the boot files ntldr, ntdetect.com and boot.ini.)

Mount you windows partition:

```
sudo mount /dev/sda5 /mnt
```

and copy the boot files from the archive  to your windows partion:


```

cd /mnt
sudo tar -xvzf ~/Desktop/Archive.tar.gz

```


Use 

```
title Windows XP
rootnoverify  hd0,4)
chainloader  +1
```

in menu.lst. Reboot and hope for the best.

---

### Post by athrpf on 2008-10-01
Awesome! Problem solved! Thank you, meierfra!

---

### Post by Bucky Ball on 2008-10-01
Excellent news athrpf! Don't forget to mark your thread solved using 'Thread Tools' so others might find meierfra's neat solution. :)

---

