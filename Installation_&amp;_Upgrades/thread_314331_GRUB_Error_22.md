---
title: "GRUB Error 22"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by cranduit on 2006-12-07
Hi all, I recently installed Ubuntu to try it out.  Well, the first  time I booted without the disc I had a problem loading GRUB, Error 22 as stated in the topic.

After a couple of tries, I decided to see if I could get back into Windows XP.  Well, that didn't work either.  I ran the recovery console, did both fixboot and fixmbr about 5 times each and I get one of two errors.

If there is no disc in the drive, GRUB Error 22
If there is the XP disc in the drive, Error loading OS

So the question is, is there a way to get back into XP without refomatting.  I've done that twice in the past month already and I'm getting sick of calling Microsoft.

---

### Post by bulldog on 2006-12-07
22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

Do you have one hard disk?
Is it properly being recognized in your BIOS?

If you can boot from the live cd can you give us the output of ```
fdisk -l (l as in like)
``` which you can type in a terminal.

---

### Post by cranduit on 2006-12-07
I have 3 hard disks, 2 IDE, 1 SATA, all recognized by BIOS.

```
Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1            7266       14946    61697632+   f  W95 Ext'd (LBA)
/dev/hdb2               1        7265    58356081   83  Linux
/dev/hdb5            7577       14946    59199493+   7  HPFS/NTFS
/dev/hdb6            7266        7576     2498044+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36481   293033601    7  HPFS/NTFS

```

---

### Post by bulldog on 2006-12-07
Do you know from which drive you're booting,because I think your GRUB is pointing to the wrong drives.
If you're on the live cd mount your ubuntu partition,
```
sudo mkdir /mnt/rescue
```
```
sudo mount /dev/hdb2 /mnt/rescue
```
To find your menu.lst to post it here,
```
cat /mnt/rescue/boot/grub/menu.lst
```

**EDIT**
Which partition is your windows install?
I see two bootable NTFS partitions,one on hda1 and one on sda1.

---

### Post by cranduit on 2006-12-07
It's showing Vista/Longhorn but that's not installed anymore.  Only XP is installed still on hda1

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
# kopt=root=UUID=da95361c-1e74-42dc-9cc0-98075a3054cf ro
# kopt_2_6=root=/dev/hdb2 ro

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

```

---

### Post by bulldog on 2006-12-07
Okay and now I need to know on which disk is GRUB installed.
This disk should be the default boot disk.

**EDIT:**
Some things to consider.
Installing GRUB on the disk where your ubuntu is,has some advantage.
You can reinstall windows [on the same place] without reinstalling GRUB.
You can set windows to boot by default in GRUB if you want,but if GRUB is failing,like now,you can boot windows by setting this drive as boot device in your BIOS,with it's own boot loader. 
So you can always boot an OS if things go wrong.

We can reinstall GRUB to the ubuntu disk in 5 minutes if you want to do so.
Than you have to reinstall windows boot loader with the windows install disk.

---

### Post by cranduit on 2006-12-07
I believe it said it was installing it on hd0.  Otherwise I believe it would be hdb1.  Is there a way to check?

---

### Post by rsambuca on 2006-12-07
I had a similar problem when I was fiddling with my bios settings.  Before doing to much, I would just do a quick check in your bios to check the order of the hard drives on your system.

---

### Post by bulldog on 2006-12-07
Look at my previous post and let me know what you think about it.
You need to have a windows install disk to accomplish this though.

GRUB will install to (hd0) by default,but there's a but,if you set the Sata disk as boot device,this will be (hd0) :D 
So if you boot from Sata and I think you do,than we have to rearrange your grub or reinstall it on the ubuntu disk.

Hi rsambuca,yes looking in the BIOS is the easiest thing to do.

---

### Post by cranduit on 2006-12-07
If it is booting from the SATA drive, then it shouldn't be, the only thing that is on there is music and movies.  I checked the BIOS order and it was hda, hdb, sda.

With the GRUB reinstall would I need to do a full windows reinstall?  I know I tried the fixmbr and fixboot commands at the recovery console.

---

### Post by bulldog on 2006-12-07
If we reinstall GRUB you only have to fix the windows disk MBR with the recovery console.
This isn't a must but can come in handy when you run into trouble with ubuntu.


**EDIT:**
When you boot from hda = (hd0) than all should work well.
In that case is ubuntu (hd1) and that is correct.
GRUB points to the correct disk an partitions.

---

### Post by cranduit on 2006-12-07
Ok, how would I go about doing that?

---

### Post by bulldog on 2006-12-07
Reinstalling GRUB you mean?
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

You have to watch the setup line.
If the find command tells you (hd0,1) you setup (hd0) id it says (hd1,1)you do setup (hd1)

---

### Post by cranduit on 2006-12-07
Yes, I tried reinstalling GRUB from the live CD and ```
find /boot/grub/stage1
``` displays (hd1,1).  I tried ```
root (hd1,1)
setup (hd1)
``` to set it up, but it still works like it did before.

---

### Post by bulldog on 2006-12-07
It said (hd1,1).
Now you have to go into your BIOS and set the ubuntu disk as default boot device.
Be sure this is the one.

Now we have to altering GRUB again,because ubuntu will be on (hd0) than.
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
# kopt=root=UUID=da95361c-1e74-42dc-9cc0-98075a3054cf ro
# kopt_2_6=root=/dev/hdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows Vista/Longhorn (loader)
root            (hd1,0)
map    (hd1) (hd0)
map    (hd0) (hd1) 
savedefault
makeactive
chainloader     +1

```
Copy this over your menu.lst and save it as menu.lst.
Set your hdb as boot device [the one with ubuntu on it]
Try to boot windows as well as ubuntu.
Then recover the MBR with the windows disk.
Run the windows install till you get three options,
1:Install windows
2:Repair a windows install
3:exit
Choose option two,you go to a console where you will be asked to logon a windows install [which is listed with a number],
Choose the right one,not the Vista,give your administrator password,and run fixboot and fixmbr.
Exit the windows cd and it should be able to boot on it's own boot loader when you select this disk in the BIOS to boot from.

---

### Post by cranduit on 2006-12-07
Ok, I changed the boot priority and it still came up with hd1,1.  However, I tried booting and now it will let me pick from the list and load Windows.  No I'll just have to read up on how to edit the grub menu.lst.  :D 

Thanks.

**Edit**
Well, that was short lived feeling of joy.  I went to load Ubuntu and now it says the partition can't be found.

**Edit 2**
Ok, I did what you said, but now the recovery console won't let me fixmbr.  It doesn't have any text with the command, it just thinks about it and then moves on.  fixboot works fine though.

---

### Post by bulldog on 2006-12-07
Can you still boot windows from GRUB?
It has nothing to do with the Vista install on sda?

If you can boot windows,have a look at your boot.ini to see which operating systems are listed there.
If there's a Vista,try to remove that one,if Vista isn't on your disks anymore.
More info is here,

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors)

---

### Post by cranduit on 2006-12-07
If I use the original menu.lst I posted, I can boot windows.  If I use the edited menu.lst, I cannot.

---

### Post by bulldog on 2006-12-08
Well let me see the original menu.lst please :D 
We're half way than.

---

