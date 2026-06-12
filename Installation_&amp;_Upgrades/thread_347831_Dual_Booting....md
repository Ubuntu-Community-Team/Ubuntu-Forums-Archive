---
title: "Dual Booting..."
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by RichComposer on 2007-01-27
Hi all,
I'm brand new to Linux & loving it so far. but i do have a question about my other Windows OS.
When booting up, it automatically defaults to Ubuntu.. how do i access my Windows partition?

It might be really simple, but i can't figure it out straight away. Need to move some importatnt work ASAP!

Many thanks for your time,

Rich W

---

### Post by kevinlyfellow on 2007-01-27
Welcome aboard...

If you navigate to /boot/grub/ and open up menu.lst you can find the grub configuration file.  Post it up here and we can check it out to make sure that everything is ok with it.

When booting up, normally you would see grub, which lets you select which operating system to boot.  My assumption is that you are either not getting this menu or windows is not listed

---

### Post by confused57 on 2007-01-27
> **RichComposer said:**
> Hi all,
I'm brand new to Linux & loving it so far. but i do have a question about my other Windows OS.
When booting up, it automatically defaults to Ubuntu.. how do i access my Windows partition?

It might be really simple, but i can't figure it out straight away. Need to move some importatnt work ASAP!

Many thanks for your time,

Rich W
Is there an option to boot Windows in the grub menu at startup?  If you don't see the grub menu, press "esc" when prompted, click the arrow "down" to highlight the Windows entry & press enter to boot Windows.  If there isn't an entry to boot Windows, boot up Ubuntu, open a terminal(Applications--Accessories--Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L".

You might also want to check your /boot/grub/menu.lst in the terminal:
```
gedit /boot/grub/menu.lst
```
menu.lst is short for menu.list

just post the entries to boot Ubuntu & Windows(if present)

---

### Post by RichComposer on 2007-01-28
Thanks for the cool response.. just immediately thought people would raise their eyebrows at another dual boot problem!

Here's what happens when i use the terminal app:

[B]Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2612    20980858+   7  HPFS/NTFS
/dev/hda2            2613        9729    57167302+   5  Extended
/dev/hda5            2613        9729    57167269+   7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1            2588       13292    85987910+   7  HPFS/NTFS
/dev/hdb2           13293       14593    10450282+   5  Extended
/dev/hdb3   *           1        2477    19896471   83  Linux
/dev/hdb4            2478        2587      883575   82  Linux swap / Solaris
/dev/hdb5           13293       14593    10450251   bc  Unknown

Partition table entries are not in disk order

Disk /dev/sda: 250.0 GB, 250059350016 bytes
81 heads, 63 sectors/track, 95707 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       95708   244198584    4  FAT16 <32M

Disk /dev/sda1: 250.0 GB, 250059350016 bytes
81 heads, 63 sectors/track, 95707 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           1       95708   244198584    4  FAT16 <32M[/B]
[/B]







Ok and here is the menu.lst that was asked for:

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
# kopt=root=UUID=d2c752c3-0852-4df7-9c8d-0e37ddfd2446 ro
# kopt_2_6=root=/dev/hdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


If you can make head or tail of it.. i'll be very grateful. I've got a good chunk of PC knowledge, but its alway daunting to start with something quite so new...

---

### Post by kevinlyfellow on 2007-01-28
The end of grub should look like this

```

## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd1,2)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb3 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd1,2)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb3 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd1,2)
kernel /boot/memtest86+.bin
quiet
boot

title Windows
root (hd0,0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST


```

I think this will do it.  It looks like your windows install is on the first partition of the first hd, if this is correct the above code will work.  if not the change the part that read root (hd0,0) to something else.  the first zero is for the harddisk number (starting with zero) and the second number is for the partition number (starting with zero)

> I've got a good chunk of PC knowledge, but its alway daunting to start with something quite so new...

don't worry about it, we all had these troubles when we just started linux.  once you get the hang of it, then you will see why everyone loves linux so much!

---

### Post by RichComposer on 2007-01-28
Thank you for the helpful info!

Interestingly, i had almost figured out what you just posted.. after much fiddling & reading today. 
With that said, the further problem i encountered was that when i attempted to change the 'menu' file.. i keep getting the message that i am not authorized to save to the 'boot' folder.
If i can bug you for that extra bit of help, i think i may be able to finally enjoy both XP / Linux together!
Probably something simple preventing me from modifying the file...

Anyhow, thanks for the help so far.. nice friendly forum.. :D 

Rich

---

### Post by eholly on 2007-01-28
you need to be su to change the grub file. 
sudo -i
password
 and then edit the file.  
you will be able to save it with the proper permissions.
 exit gets you out of super user mode

---

### Post by RichComposer on 2007-01-28
Okay, i half follow your instructions!
I understand & can become SU in the Terminal App..
I then assumed that i could just browse to the file, make alterations & then just save the file like normal.
I still got the same error message after having done that.. or am i missing the point slightly?
Go gentle, i'm only a beginner.. assume i know nothing.. (which is close to the truth with Linux!)

Many thanks,
Rich

Oh and on a lightly different angle.. if i had a partition of purely music files, created under XP, but on a different internal HDD to Ubuntu.. am i still able to access the files for use with one of the media players?
I'm assuming that because i can't 'see' the drives or partitions within Ubuntu, the two aren't compatible?
It'd just be awesome to have one single music partition that could serve both OS's, other than having to resort to an external HDD. Maybe its possible already...?

---

### Post by confused57 on 2007-01-28
> **RichComposer said:**
> Okay, i half follow your instructions!
I understand & can become SU in the Terminal App..
I then assumed that i could just browse to the file, make alterations & then just save the file like normal.
I still got the same error message after having done that.. or am i missing the point slightly?
Go gentle, i'm only a beginner.. assume i know nothing.. (which is close to the truth with Linux!)

Many thanks,
Rich

Oh and on a lightly different angle.. if i had a partition of purely music files, created under XP, but on a different internal HDD to Ubuntu.. am i still able to access the files for use with one of the media players?
I'm assuming that because i can't 'see' the drives or partitions within Ubuntu, the two aren't compatible?
It'd just be awesome to have one single music partition that could serve both OS's, other than having to resort to an external HDD. Maybe its possible already...?

To edit your menu.lst(copy & paste each line one at a time, press enter):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

then copy & paste the following at the end of the file(after ##END DEBIAN....):
```
title   Windows
root   (hd0,0)
makeactive
chainloader +1
```

If the music partition is NTFS, you can read it from Ubuntu, but it's not advised to try to write to it from Ubuntu(there is a program that you can install to allow writing to NTFS, but it's relatively experimental)...it would be a matter of mounting the partition:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by kevinlyfellow on 2007-01-29
> With that said, the further problem i encountered was that when i attempted to change the 'menu' file.. i keep getting the message that i am not authorized to save to the 'boot' folder. 

sorry about that... its hard to remember that not everyone knows about permissions...

anyways, the easiest way to edit it is of course

```
gksudo gedit /boot/grub/menu.lst
```

gedit will automatically back up for you but you should back up anyways

---

