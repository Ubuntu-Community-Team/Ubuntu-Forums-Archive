---
title: "After dapper install, Grub won't load windows"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by th3james on 2006-07-03
I just managed to convince my friend to try ubuntu on his laptop, but grub gives me this error when i try to boot windows

```

Booting 'Microsoft Windows XP Professional'

root (hd0,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1


```

 He had a full 40 gb drive with an NTFS windows partiton. I re-partitioned this using the liveCD (recieved my shipit stuff today :D) with gparted to this scheme

ntfs       22gb  - windows resized
fat32     3.5gb - new partition to exchange between windows/linux
ext3      10gb  - ubuntu

when re-sizing the ntfs partition, it took a very long time (about 10 mins). Anyway, the ntfs partiton seems intact, because i can read it in linux

I've rooted around on the internet, and found this old Bug:
[https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/10661]("https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/10661")
However, im not to sure if this is the, or if it is, how to fix it. There is no parameter in his bios to change the boot type to LBA instead of automatic.

Please help, i don't want to put a potential ubuntu user off!

---

### Post by theredcross on 2006-07-03
check fdisk to make sure its recognizing the partition and that it recognizes that it is NTFS, try checking /etc/grub.conf and looking to see if there are any simple typos or misspelled words, little things like that have got me in hours of trouble. if they seem fine and you still can't figure it out, it would be wise to print out both in this thread so we can check it as well.

---

### Post by th3james on 2006-07-03
fdisk:
```

james@jamescox:~$ sudo fdisk -l /dev/hda

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2948    23679778+   7  HPFS/NTFS
/dev/hda2            2949        3396     3598560    b  W95 FAT32
/dev/hda3            3397        4799    11269597+  83  Linux
/dev/hda4            4800        4864      522112+   5  Extended
/dev/hda5            4800        4864      522081   82  Linux swap / Solaris

```

I couldn't find /etc/grub.conf, so instead here is my /boot/grub/menu.lst
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
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by catlett on 2006-07-03
misunderstood the issue

---

### Post by catlett on 2006-07-03
Try editing the grub menu to say rootnoverify instead of root. Hopefully that will get grub past the confusioin about root.

```
title		Microsoft Windows XP Professional
[COLOR="Red"]root[/COLOR]		(hd0,0)
savedefault
makeactive
chainloader	+1

```
```
title		Microsoft Windows XP Professional
[COLOR="Red"]rootnoverify	[/COLOR]	(hd0,0)
savedefault
makeactive
chainloader	+1
```

Grub must be getting confuse because your windows partition is being recognised as High Performance Filesystem and New Technology Filesystem (i.e. HPHS and NTFS) Let's hope that rootnoverify gets grub past the filesystem type.
What kind of computer is this? Did you or your friend format the drive before?

---

### Post by theredcross on 2006-07-03
and i meant to say /etc/fstab instead of grub.conf, but looks like catlett is on the right track.

---

### Post by th3james on 2006-07-03
i tried the rootnoverify option, slightly differn't error message
```

Booting 'Microsoft WIndows XP Professional'

rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1


```

BTW, here is the partiton layout

/dev/hda1 = windows ntfs
/dev/hda2 = fat32
/dev/hda3 = ubuntu ext3
/dev/hda4 type extended
     /dev/hda5 = swap

---

### Post by th3james on 2006-07-03
Just seen your new post, yes, it appears to have removed the Filesystem type error, but still no mount. The computer is a toshiba satellite laptop, and all the partitioning was done in the ubuntu livecd, before that is was the default factory windows install. I did the partitioning myself. Could it be a problem with the ntfs partition? It still mounts fine in ubuntu

---

### Post by catlett on 2006-07-03
I was reading the bug report and it may have to do with the partitioner. HPFS is old and a newer XP install wouldn't have anything formatted as HPFS (although I don't know for sure where the computer comes from or if it was partitioned before)
Anyways do one thing to help trouble shoot. Go to System<Administration<Gnome Partition Editor. This is gparted the partitioner the live cd used.
If it isn't listed install it with ```
sudo apt-get install gparted 
```
Once you can get to it, run it. Your hard drive will come up as a bar graph. See how your windows partition is labeled. Is it ntfs, hpfs or unknown?

---

### Post by th3james on 2006-07-03
Thanks for your continuing help

its labeled as NTFS

---

### Post by catlett on 2006-07-03
Let's try one last thing before you make a decision to reinstall the windows bootloader and you will be able to boot to windows but not ubuntu.
If you want a work around there is one where you restore windows mbr. Then reinstall ubuntu wqith the alternate install cd. This time puttinmgh grub onm a floppy and leaving the mbr alone.
My last suggestion would be to update grub and hope it corrects itself. Enter ```
sudo update-grub
``` If that doesn't work and you want to restore your windows mbr just post and I'll give you the directions.

---

### Post by th3james on 2006-07-03
sadly the grub update didn't help
would there be any point in re-installing grub from the livecd? Could it have been anything to do with the bios like was suggested in the thread?
I really want to get both sytems booting asap. If i were to re-install the windows bootloader, how would i then get ubuntu booting as well?

---

### Post by th3james on 2006-07-03
Oh, one other thing, the laptop has no floppy drive, so grub on a floppy is impossible

---

### Post by catlett on 2006-07-03
This may not be the prettiest way to do it but at least I can say for sure it will work. You need 2 things. A windows install cd and the Ubuntu Alternate Install CD.
If you don't have a windows install disk just download an XP install disk with bittorrent. Go to any site (Pirate's Bay, Torrent Spy) they all have copies for download. You don't need an activation key to get into the recovery mode.
The Alternate Install CD can be downloaded at the ubuntu download site.

First you have to re-install windows bootloader. Boot to the install disk. It will come to a prompt where it will ask you if you want to install or enter recovery (or rescue I forget). Just enter R and the recovery session starts. Next it will give you a list of window installations and which one you want to use for the recovery. You only have 1 so enter 1 and press enter. It will ask you for an administator password. Just enter your windows password (as you know a regular window's account is setup as administrator). This will get you a command prompt i.e. C:\ . Enter ```
fixmbr
``` It will give you a warning about overwriting the mbr etc. Just enter Y and let it do it's thing.

Now your system will boot to windows like usual.

Next get the Alternate Install CD. Go through the install like before. Just use the same partitions. The difference will come at the end. At the end of the alternate install cd (and not with the live cd) it will ask you if you want to install grub to the mbr. So no. Put a floppy into your floppy drive. The next page will ask you where you want to install grub. Enter ```
/dev/fd0
``` This will install grub to the floppy disk. The install will finish.

Your computer will now boot to windows if you don't do anything. If you put the floppy in before you startup then your computer will boot to grub and ubuntu.

It isn't the best solution but it will work. Wait a minute I just thought of something. This is a laptop. Do you even have a floppy drive?

---

### Post by catlett on 2006-07-03
I just saw your post after I posted. You can try this.

This is what Herman suggests as an alternative to Grub. [http://gag.sourceforge.net/index.html](http://gag.sourceforge.net/index.html) It is called GAG (graphical boot manager. the initials in spanish are gag) I never tried it but it seems simple. You download it and install it to a floppy or a cd rom.
It appears the easiest way would be to burn the iso, that is in the download after you unzip it, to a cd and boot to it.

Hermanb's site is in my signature under "How To Install Ubuntu - Alternate Install CD" He has a page on GAG.

---

### Post by th3james on 2006-07-03
Thanks, I'm looking into GAG, it looks like the solution to my problems! Hopefully it works as it says it does

Thanks again

---

### Post by th3james on 2006-07-03
When i try to boot windows with gag, im just presented with a blank screen and a blinking cusor, so i think the windows partition must be borked... oh well, thankfully all the of data has been backed up, looks like I'm gnna have to do a windows reinstall....

---

### Post by catlett on 2006-07-03
Wow that's terrible. Thank goodness you backed up.
I'll make one suggestion. If you are going to re-install. I would reformat your whole hard drive and start from scratch.
I prefer gparted live. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) It's gparted but it runs off a live cd. The benefit is the hard drive is not mounted and all the changes can take effect right away. It's a small download, only 30mb, and I have had only good results.

---

