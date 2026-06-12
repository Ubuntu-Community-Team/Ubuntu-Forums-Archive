---
title: "GRUB Error 22"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by Joose BuckaLoose on 2007-03-03
I just bought a new 120 GB Hard drive to install Ubuntu on, and after installing grub is giving me problems.

When I start my computer I get:

```
Grub Loading stage1.5.

GRUB loading, please wait...
Error 22
```

And I can not boot my computer.

I looked around the forums and I can't find a solution

I have three SATA hard drives in my computer:
1) 74 GB Windows XP Professional
2) 120 GB for my new Ubuntu install
3) 500 GB NTSF for storage

Here is the output of fdisk -ul from the live CD:

```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   145195469    72597703+   7  HPFS/NTFS

Disk /dev/sdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders, total 241254720 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     4096574     2048256   82  Linux swap / Solaris
/dev/sdb2         4096575    45062324    20482875   83  Linux
/dev/sdb3        45062325   241248104    98092890   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976772159   488386048+   7  HPFS/NTFS

```

Any help would be greatly appreciated

---

### Post by taurus on 2007-03-03
Did you install GRUB to /dev/sda?

---

### Post by Joose BuckaLoose on 2007-03-03
The installer installed it to (hd0) so I'm assuming by the fact that 1) My BIOS is set to boot of sda and NTLDR is no where to be found that yes it did.

---

### Post by rsambuca on 2007-03-03
This happens a lot because grub has to "guess" the order of the drives in the bios, and sometimes it guesses wrong.

If you give us the output of your /boot/grub/menu.lst and your /boot/grub/device.map, we should have you up and running in no time.

---

### Post by Joose BuckaLoose on 2007-03-03
Okay well tell me if what I did was wrong.

I booted up using the live CD and mounted the hard drive to /media/ubuntu so here is

/media/ubuntu/boot/grub/menu.lst

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
# kopt=root=UUID=4d6e591e-baef-4d26-80a7-a36e3e4f12d9 ro
# kopt_2_6=root=/dev/sdb3 ro

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

And here is /media/ubuntu/boot/grub/device.map

```
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc

```

Hope this helps. I can't wait to finally get this up and running!

---

### Post by rsambuca on 2007-03-03
Do you know how you partitioned that new 120 GB drive when you installed ubuntu?  I see that you have a swap as partition 1, and then there are 2 more partitions on that drive.  Do you know what they are?

---

### Post by Joose BuckaLoose on 2007-03-03
Yes:

/dev/sdb1              63     4096574     2048256   82  Linux swap / Solaris

is obviously swap 

/dev/sdb2         4096575    45062324    20482875   83  Linux

is /home

/dev/sdb3        45062325   241248104    98092890   83  Linux

is /

---

### Post by rsambuca on 2007-03-03
Can you check the order of the drives in the Bios?

---

### Post by Joose BuckaLoose on 2007-03-03
The boot order is:

1 My 74 GB HDD with Windows XP on it (sda) (hd0 where I installed grub on)
2 My 150 GB HDD with ubuntu on it (sdb)
3 My 500 GB HDD NTFS for storage (sdc)

---

### Post by rsambuca on 2007-03-03
Hmmm...   Now I am confused:-k 

The fact that your rig gets to Stage 1.5 error 22 means that that it is in the MBR, but it is pointing to a nonexistent partition.  However, Bios indicates the correct order of drives, your device.map matches the bios, the menu.lst looks correct.

Sorry, the only thing I can think of now is just to re-install grub from the liveCD terminal.

---

### Post by Joose BuckaLoose on 2007-03-03
How would I go about doing that?

---

### Post by rsambuca on 2007-03-04
From the live cd, enter in a terminal```
sudo grub
```

at the grub prompt,```
find /boot/grub/stage1
```

whatever is spit out for the stage 1 instructions eg (hd1,2), enter with the root command```
root (hd1,2)
```

then write the instructions to the MBR```
setup (hd0)
```

Type quit to exit grub.  Cross your fingers and reboot.

If that doesn't work, you might just try in a terminal```
sudo grub-install
```

---

### Post by Joose BuckaLoose on 2007-03-04
No luck :(

Any other suggestions?

---

### Post by rsambuca on 2007-03-04
Are you sure that you checked the boot order of the hard drives in your bios?

---

### Post by Joose BuckaLoose on 2007-03-04
Yep,

The boot or is exactly as I stated above

---

### Post by rsambuca on 2007-03-04
Sorry, out of ideas here.  Hopefully someone else can help you out.:confused:

---

### Post by bikeboy on 2007-03-04
Hmm I may be completely wrong but...Your menu.lst has the linux kernel at (hd1,2) but you say your root partition is /dev/sdb3. /home is on /dev/sdb2. Perhaps grub should be looking for the kernel at (hd1,3)???

---

### Post by rsambuca on 2007-03-04
The menu.lst is how it should be, given what we know.  Grub numbers start at 0, not 1, thus the third partition is in fact 2!

---

### Post by bikeboy on 2007-03-04
Ah ok. Just an idea.

---

### Post by confused57 on 2007-03-04
> **Joose BuckaLoose said:**
> No luck :(

Any other suggestions?
As rsambuca mentioned, with all the information you've supplied, your system should boot...does Windows boot from grub?  If not, you might want to restore your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Once you're able to boot Windows, you might want to try a different installation setup.

In bios, set your hard drive boot order as sdb, sda, sdc...then install Ubuntu to sdb, do a manual partitioning, but I'd suggest to do it a little differently:

sdb1...primary partition for root(/)
sdb2...primary partition for home
sdb3...swap

or

sdb1...primary partition for root
sdb2...extended partition(which will be automatically created, if you make home & swap logical partitions)
sdb5...logical partition for home
sdb6...logical partition for swap

the benefit of the 2nd setup is that you could add more partitions without the restriction of 4 primary partitions on the hard drive.

Just some ideas for you to consider, unless you're able to find a solution to boot your current setup.

Did you happen to partition & pre-format your 2nd hard drive with something like Partition Magic or did you use the live cd's partitioner?

---

### Post by Herman on 2007-03-04
> Did you happen to partition & pre-format your 2nd hard drive with something like Partition Magic or did you use the live cd's partitioner?You could try running a filesystem check.                   [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem")
You can run the filesystem check from a [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php")
or from your Ubuntu 'Desktop' Live/Install CD, (as long as the filesystem is not mounted at the time). If you use your Ubuntu Live CD, just use 'sudo' before the fsck command. A filesystem check has cured error 22 for me before.

If that doesn't help then another thing you can try is to use a grub CD, such as [Super Grub Disk.]("http://supergrub.forjamari.linex.org/")
You can either use it in menu mode, or press 'c' from a menu for [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
Grub's command line interface is interactive, so yuou should get feedback that will give you information about what could be wrong. Take notes as this can be useful for getting more help and for editing your menu.lst to fix the problem.

Regards, Herman :)

---

