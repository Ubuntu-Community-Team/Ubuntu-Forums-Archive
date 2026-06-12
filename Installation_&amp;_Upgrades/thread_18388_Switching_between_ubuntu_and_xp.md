---
title: "Switching between ubuntu and xp"
date: 2005-03-06
forum: Installation &amp; Upgrades
---

### Post by aerguney on 2005-03-06
I partitioned my hd with powerquest partition magic 8.I selected ext2 as filesystem and selected primary.I installed it after C:  with a 5 gb of space and i also created a swap partiton before C: with 640 mb of space.I did them from the "install another operating system" option of PM.I set ext2 partition active and installed ubuntu.When i'm trying to choose xp as OS from the grab menu,windows seems to start but after i see windows xp preload screen it says something like "autochk failed,skipping it" and it restarts the computer.I tried to boot from xp cd to repair my xp but it starts with grab menu again(cd is primary at boot sequence).I think it's because ext2 partition can't recognize NTFS compatible xp cd.What can i do to get my xp back.I need my files in the ntfs partition,please help me

---

### Post by Udine on 2005-03-06
There must be a reason its not booting off your XP cd...go over your boot sequence in your BIOS again...Once u booted the XP cd choose repair console...there u can fix /mbr or somefin to that affect...Hope you come right...

Otherwise put the drive in another machine to get your info off...  :mrgreen:

---

### Post by doitashimashite on 2005-03-06
What does

$ sudo fdisk -l /dev/hda

give?

And how does your /boot/grub/menu.lst look like?
Must be a simple explanation for this.

---

### Post by aerguney on 2005-03-06
[QUOTE=doitashimashite]What does

$ sudo fdisk -l /dev/hda

give?

And how does your /boot/grub/menu.lst look like?
Must be a simple explanation for this.[/QUOTE]

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          84        4504    35511651   17  Hidden HPFS/NTFS
/dev/hda2            4505        4865     2899732+  83  Linux
/dev/hda3               1          83      666666   82  Linux swap

Partition table entries are not in disk order
----this is what $ sudo fdisk -l /dev/hda gives.

----And this is menu.lst file
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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option contols options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## ## End Default Options ##

title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,1)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

i am new to linux so i had to copy and paste all these garbage,sorry.And thanks for your interest.I'll be glad too much if you can solve this problem

---

### Post by doitashimashite on 2005-03-06
On one of my previous installations I had some trouble booting from XP. That was because I added an XP harddisk to the already installed Ubuntu system. I had to manually adapt /boot/grub/menu.lst in order to make this work, and it was kindof a puzzle. But after a while I got it going, with this entry:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

This is XP on the first partition of the first (primary master) disk.

If XP is not on the first, but the second partition, then change 
root		(hd0,0)
into
root		(hd0,1)

I hope this will help a bit.

---

### Post by doitashimashite on 2005-03-06
Looks like your menu.lst is okay.

But I wondered, why is your NTFS partition "hidden"?
Maybe that partition magic tool messed up the table a bit?

---

### Post by aerguney on 2005-03-06
can you please help me according to my menu.lst?i'm afraid of crashing my system by modifying menu.lst :( I think if i can boot from my xp cd,it can repair itself and that autocheck problem should be solved then(as i said,xp preload appears but after it finishes it tries to make autocheck and the computer restarts itself).How can i make my computer boot from xp cd?(cd is selected as primary device in boot sequence,there is an abnormal trouble i think)

---

### Post by doitashimashite on 2005-03-06
If your biggest problem right now is to be able to access your XP files, then what about booting Ubuntu, and from a terminal:

$ sudo mount /dev/hda1 /mnt

Then as quickly as possible, burn the important XP data to disk (or copy them to the Linux partition).

Does mounting of /dev/hda1 work?

---

### Post by doitashimashite on 2005-03-06
"burn to disk"

LOL

What I meant was "burn to CD"

---

### Post by aerguney on 2005-03-06
[QUOTE=doitashimashite]"burn to disk"

LOL

What I meant was "burn to CD"[/QUOTE]
yeah i could understand :) i don't know much about hardware and linux,i am a web designer and flash AS developer.I tried to mount to hda1 as you said but it said cannot show the content,but it could read the empty space at that partition.I am sure my files are living there but i cannot touch them :) i missed them too much

---

### Post by doitashimashite on 2005-03-06
Looking at your menu.lst again, I found out that your XP partition, though mentioned first in the table, is actually (physically) the SECOND partition on the disk:

cylinders 1-83: Linux swap
cylinders 84-4504: XP
cylinders 4505-4865: Linux

So, if I were you, I would change the line

root (hd0,0)

into

root (hd0,1)

and reboot the machine, see if XP comes alive.

---

### Post by doitashimashite on 2005-03-06
No, please forget my last suggestion. It won't work.

---

### Post by doitashimashite on 2005-03-06
When you tried to mount /dev/hda1 under /mnt, what was your exact command, and what exactly was the error message?

---

### Post by doitashimashite on 2005-03-06
If the problem with mounting your XP partition was a permission thing, then I'd suggest the following command to mount it in order to make it accessable for non-root users:

$ sudo mount /dev/hda1 /mnt -o uid=<username>,gid=<groupname>,umask=000

---

### Post by aerguney on 2005-03-07
[QUOTE=doitashimashite]If the problem with mounting your XP partition was a permission thing, then I'd suggest the following command to mount it in order to make it accessable for non-root users:

$ sudo mount /dev/hda1 /mnt -o uid=<username>,gid=<groupname>,umask=000[/QUOTE]
 yes i can reach my xp files with the last command you wrote.Thanks alot shimashite!My another problem is when i'm trying to install wine the application winetools gives an error about xdialog dependency.How can and where can i download xdialog?

---

### Post by doitashimashite on 2005-03-08
Computer /
System Configuration /
Synaptic Package Manager /
Search: xdialog

and install the package.

If the package doesn't appear, you'll have to make sure that you have the right repositories in /etc/apt/sources.list.

---

### Post by bored2k on 2005-03-08
[QUOTE=doitashimashite]Computer /
System Configuration /
Synaptic Package Manager /
Search: xdialog

and install the package.

If the package doesn't appear, you'll have to make sure that you have the right repositories in /etc/apt/sources.list.[/QUOTE]
 You can also get Crossover Office 4.2.1 wich will solve ur problem . Non-free tho.

---

