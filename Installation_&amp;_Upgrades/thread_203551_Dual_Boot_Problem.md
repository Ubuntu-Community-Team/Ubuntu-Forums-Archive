---
title: "Dual Boot Problem"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by Gipper P on 2006-06-25
I recently decided to try linux and installed ubuntu 6.06 on my machine,  which was already running windows XP, an OS I unfortunately need to keep, after trying the live cd. Therefore I thought that a dual boot was a better, more permanent solution.

Now I only have one physical hard disk drive so I needed to partition it. I have partitioned it in the following way:

/dev/hda1 - a windows NTFS partition with XP home on it
/dev/hda5 - a windows NTFS partition with other XP proggys on it
/dev/hda6 - an ext3 partition with the /home tree on it
/dev/hda7 - swap
/dev/hda8 - ext3 with rest of ubuntu on it
/dev/hda9 - NTFS other files that i have created and saved in windows

Everything works fine in ubuntu, however when I try to boot Windows, I get the following message come up on the screen:

```
     Booting 'Windows XP Home Edition'

root (hd0,0)
     Filesystem type unknown, partition type 0x7

savedefault
makeactive
chainloader +1
```

The system then does nothing. I believe I am using the GRUB bootloader.

I'm a newbie to linux who tried something a little too hard here! But I need to be able to run windows! Is there any solution to this problem? ](*,)

---

### Post by tonyr on 2006-06-25
Can you boot Ubuntu?  If you can, open a terminal (Applications->Accessories-Terminal)
and type these two lines:
```

fdisk -l
cat /boot/grub/menu.lst

```

(that's an ELL, not an EYE, with fdisk.

and post the output here.

---

### Post by Gipper P on 2006-06-25
Thanks for the quick reply.

This is the output:

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
timeout         10

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
# kopt=root=/dev/hda8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title           Ubuntu, kernel 2.6.15-25-386
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hda8 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hda8 ro single
initrd          /boot/initrd.img-2.6.15-25-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda8 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda8 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,7)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1



I tried adjusting the figures for the (hd0,0) on the windows xp entry, but to no avail... perhaps the wrong figures? or am i completely barking up the wrong tree?

---

### Post by tonyr on 2006-06-25
OK, but I messed up on my first post.  In a terminal run
```

sudo fdisk -l /dev/hda

```

and post that output.

I don't see anything wrong with the menu.lst file.  Some people replace the **root** line
with **rootnoverify (hd0,0)** to that last section about Windows XP Home.

(hd0,0) means /dev/hda1, first device, first partition.  That matches the partition
description you psted originally.

---

### Post by Gipper P on 2006-06-25
Disk /dev/hda: 60.0 GB, 60022480896 bytes
16 heads, 63 sectors/track, 116301 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24385    12289693+   7  HPFS/NTFS
/dev/hda2           24385      116280    46315395    f  W95 Ext'd (LBA)
/dev/hda5           24386       60956    18431784    7  HPFS/NTFS
/dev/hda6   *       60957       73439     6291400+  83  Linux
/dev/hda7           73440       75520     1048792+  82  Linux swap / Solaris
/dev/hda8           75521       95497    10068376+  83  Linux
/dev/hda9           95498      116280    10474348+   7  HPFS/NTFS

---

### Post by tonyr on 2006-06-25
[QUOTE=Gipper P]Disk /dev/hda: 60.0 GB, 60022480896 bytes
16 heads, 63 sectors/track, 116301 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24385    12289693+   7  HPFS/NTFS
/dev/hda2           24385      116280    46315395    f  W95 Ext'd (LBA)
/dev/hda5           24386       60956    18431784    7  HPFS/NTFS
/dev/hda6   *       60957       73439     6291400+  83  Linux
/dev/hda7           73440       75520     1048792+  82  Linux swap / Solaris
/dev/hda8           75521       95497    10068376+  83  Linux
/dev/hda9           95498      116280    10474348+   7  HPFS/NTFS[/QUOTE]

I see a problem here. The **End** cylinder number for **/dev/hda1** is the same
as the **Start** cylinder number for **/dev/hda2**.  I interpret that to mean that
the two partitions overlap.  That can't be good. (I could be wrong, I don't completely 
understand what effect the **LBA** attached to **/dev/hda2** has). You could run
**System->Administration->Gnome Partition Editor ** and see what it has to say about
partitions definitions.

---

### Post by Gipper P on 2006-06-25
hda2 is an extended partition... i dont know if this makes any difference I am very much a newbie on the whole partition thing too!

here is a sceenie from the gnome partition editor if it is of any use:
[[IMG]http://img529.imageshack.us/img529/4582/gparted0gy.png[/IMG]](http://imageshack.us)

also using gparted i found the start and end sectors are as follows:

hda1 => 63 - 24579449
hda2 => 24579450 - 227210239

dunno if this will be of any help

---

### Post by tonyr on 2006-06-25
[QUOTE=Gipper P]
also using gparted i found the start and end sectors are as follows:

hda1 => 63 - 24579449
hda2 => 24579450 - 227210239

dunno if this will be of any help[/QUOTE]

I guess it means that the partitions use separate parts of a common cylinder, so my
previous comment doesn't apply.

That bit about GRUB not recognizing partition type 0x7 is worrisome, since partition
type 0x7 is the correct one for NTFS. You could try my other suggestion with a little more
agression.  Replace
```

title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

```

with
```

title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
chainloader +1

```

---

### Post by Gipper P on 2006-06-25
tried changing this, but it still doesnt do anything :( 

am i just being impatient? does grub take a long time to read off NTFS or a long time to boot up windows or something? im (obviously) not entirely sure how grub works...

any other ideas people? :-k 

oh btw thanks very much tonyr for your continued support :)

---

### Post by leo_m on 2006-06-25
[QUOTE=Gipper P]Disk /dev/hda: 60.0 GB, 60022480896 bytes
16 heads, 63 sectors/track, 116301 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24385    12289693+   7  HPFS/NTFS
/dev/hda2           24385      116280    46315395    f  W95 Ext'd (LBA)
/dev/hda5           24386       60956    18431784    7  HPFS/NTFS
/dev/hda6   *       60957       73439     6291400+  83  Linux
/dev/hda7           73440       75520     1048792+  82  Linux swap / Solaris
/dev/hda8           75521       95497    10068376+  83  Linux
/dev/hda9           95498      116280    10474348+   7  HPFS/NTFS[/QUOTE]


It appears you have boot flag set on two partitions, can you unset the boot flag from the linux partition?

Use fdisk /dev/hda and then use the 'a' command to toggle boot flag for the linux partition hda6 in above.

Tell what happens then...I think that hda6 is your linux boot partition.

---

### Post by aceron on 2006-06-25
actually I've been having the same problem.  I had ubuntu entirely on my laptop, then i just use my windows recovery cds to wipe it out (i had dapper running on my desktop).  But windws would never boot, grub was still in the mbr.  So i installed dapper via live cd on a seperate partition keeping windows on the hd.  at first grub did not even see the xp drive, i fixed that but now when i try to load it from grub it flashes:
savedefault
makeactive
chainloader +1
then comes back to grub boot sreen (i can get into dapper just fine from this though)
my grub menu looks the same as gipper p 
so i'm really interested in a solution to this as well.
gipper... does your grub freeze when you hit enter to boot xp from grub or does it come back to the menu almost instantly as well?

also if in uninstalled grub from the mbr, would i then boot from windows?
if so then i could reinstall grub from there an it sould find xp since its reinstalling grub eh?!

---

### Post by Gipper P on 2006-06-26
leo_m: thanks for the help, but trying the command 'fdisk /dev/hda' created the following error message: 
'Unable to open /dev/hda'

am i meant to be running this command in an ubuntu terminal or off a live cd or a system recovery disk or other?

I am also under the impression that hda6 is the linux partition... but i only put /home on there during the installation... unless thats something else i have got wrong! :rolleyes: 

aceron: my grub freezes. maybe a reinstallation is a good idea.... but its just another thing for me to get wrong ;) 

thanks everyone for your input so far! I wonder if there is something else I have overlooked...

---

### Post by Haegin on 2006-06-26
I am suffering the same problem (my grub freezes when I select Windows with the 0x7 message).

This seems to be a bug in grub in ubuntu:
**[https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/10661](https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/10661)**

I'm going to look into LILO after trying the rootnoverify thingy...

---

### Post by leo_m on 2006-06-26
[QUOTE=Gipper P]leo_m: thanks for the help, but trying the command 'fdisk /dev/hda' created the following error message: 
'Unable to open /dev/hda'

am i meant to be running this command in an ubuntu terminal or off a live cd or a system recovery disk or other?

I am also under the impression that hda6 is the linux partition... but i only put /home on there during the installation... unless thats something else i have got wrong! :rolleyes: 

aceron: my grub freezes. maybe a reinstallation is a good idea.... but its just another thing for me to get wrong ;) 

thanks everyone for your input so far! I wonder if there is something else I have overlooked...[/QUOTE]


Looking back at your post and one prior to it where you showed the partitions, I noted that you had run the fdisk command in a terminal window as :

```
sudo fdisk -l /dev/hda
```

Do the similar thing now: 

```
sudo fdisk /dev/hda 
```in a terminal window.

---

### Post by tonyr on 2006-06-26
The bug noted by **Human Prototype** is very interesting reading.  There are 
several possibilites to explore there.  The one that seems most likely to me is that
the partition table on the drive is in some slightly confused state.  If you can look
at the Disk information in your BIOS (CMOS SETUP during boot), and if it has
a controi to select between CHS and LBA, and it is set to CHS, try resetting ot
to LBA.   There are some other suggestions in there about repairing the partition
table (as there are here, as I recall).   The report generated by Partition Magic in
ine of the links in the bug report shows that the partition table can get messed up,
and it doesn't seem to me to be by accident. If the partition table is really messed up
LILO is not going to help, since I don't think it does anything to the partition
table.  It may be more forgiving in interpreting it, however.

---

### Post by Gipper P on 2006-06-27
thanks for all your help guys, but I had to give up on this and resort to formatting all the partitions on my hard disk (managing to save my important documents beforehand) and reinstalling windows... cowards way out I know but I needed to get back in with windows :( 

suffice to say I was most impressed by what i saw of ubuntu and will definately try another permanent installation at a less busy time! :D

---

