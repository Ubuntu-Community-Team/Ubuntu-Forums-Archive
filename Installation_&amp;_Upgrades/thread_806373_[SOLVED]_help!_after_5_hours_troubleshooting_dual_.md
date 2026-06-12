---
title: "[SOLVED] help! after 5 hours troubleshooting dual boot install, still can't load eith"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by conphuzed on 2008-05-24
_background_

installed ubuntu 8.04 with an existing windows XP by resizing XP partition manually and using the remaining space to install ubuntu. i am writing this post from withing the LiveCD environment b/c at this point, after many hours of troubleshooting online and slow LiveCD reboots, i still can't access either O/S.

install went fine. directly after, i reinstalled grub from within the LiveCD environment b/c when i booted Windows would load without giving me the option to select linux. this worked, so i have a grub menu come up when i boot

_what happens_

however, here's what happens next:

[COLOR="Red"]1) when i select the linux O/S, it gives Error 22: no such partition and i can press any key to return to grub
2) when i select the XP O/S, it says "Starting up..." and just sits there and i have to ctrl+alt+del to restart again. *UPDATE* it now also says "NTLDR is missing"[/COLOR]

_what i've tried_

the following things have had no effect on the above behavior (it's always exactly the same)

1) setting the boot flag on the linux partition (it was originally on the windows partition)
2) mounting the linux partition (it originally was 'not mounted'); i have succeeded in mounting it while in the LiveCD environment (i.e. it pops up on my desktop and is listed as 'mounted' in Gparted) but i suspect this is not saved when i exit and reboot b/c the problem persists and when i load the LiveCD again all the stuff i changed is back to what it was originally (not mounted)
3) to remedy the above, i tried creating a new user account with admin privileges in the LiveCD environment and logging in under this account. the same thing happened as when i was just logged in as 'ubuntu'
4) i also tried loading LiveCD with 'persistence' at the end of the set of commands that come up when i press F6. i typed 'persistence' at the end, tried it with the '--' at the end removed and without removing the '--', and when i pressed enter after typing it i'm not sure if it saved it cuz it just loaded LiveCD like normal. anyway, hopefully it saved it. either way, this had no effect
5) also tried combining steps 4 and 5 (booting LiveCD w/ persistence and creating a new user account). no effect
[COLOR="Red"]*UPDATE*[/COLOR] 6) heres another thing that happens:
> ubuntu@ubuntu:~$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
cp: cannot stat `/boot/grub/menu.lst': No such file or directory
and also if i try to edit menu.lst it opens a blank document. so it's as if this file doesn't exist.
[COLOR="Red"]*UPDATE*[/COLOR] 7) i also tried restoring grub after mounting the boot partition according to this guide: ubuntuforums.org/showthread.php?t=224351, to no avail.

> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41e2f3ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  1953520064   976760001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc03cc03c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976773167   488386552+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00038f70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdd: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x76be0773

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63    35166284    17583111    7  HPFS/NTFS
/dev/sdd2        35166285    72292499    18563107+   5  Extended
/dev/sdd5   *    35166348    70653869    17743761   83  Linux
/dev/sdd6        70653933    72292499      819283+  82  Linux swap / Solaris

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa1cd9667

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63   312576704   156288321    7  HPFS/NTFS

[COLOR="Red"]*UPDATE*[/COLOR] managed to find a non-blank menu.lst:

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
# kopt=root=UUID=13b341dc-770e-4d23-9e80-c1ba6e685df8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd4,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd4,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=13b341dc-770e-4d23-9e80-c1ba6e685df8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd4,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=13b341dc-770e-4d23-9e80-c1ba6e685df8 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd4,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde1
title		Microsoft Windows XP Home Edition
root		(hd4,0)
savedefault
makeactive
map		(hd0) (hd4)
map		(hd4) (hd0)
chainloader	+1
```

NOTE: i am very new to linux and very clueless w/ regards to linux, particularly using the terminal commands, etc., so please be very explicit in your responses.

i would appreciate any help. i am currently locked out of my computer. thanks!!

---

### Post by Pumalite on 2008-05-24
This might help:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by conphuzed on 2008-05-24
unfortunately those are generic guides, similar to those i followed to install, and don't really help. this seems to be a fairly specific issue. thanks for replying, though.

---

### Post by Herman on 2008-05-24
The output from the command 'sudo fdisk -lu', or a screencap from Gnome Partition Editor is very often useful in diagnosing boot loader problems. 
```
sudo fdisk -lu
```If you can run that command from a terminal in your live CD it may help someone help you.
'Applications'-->'Accessories'-->'Terminal'.
> but i couldn't do it because now all of a sudden, with both user accounts (original and the one i created), i can't do anything. i.e., when i try to make a directory, for example, it says permission denied. when i type fdisk -l, nothing happens (it shows another prompt). so now i have no idea what's going on.The 'sudo' prefix to your commands is needed for certain commands that can be related to security or give you access to files which can be edited to cause system-wide changes to the behaviour of your operating system. In a hard-disk-installed operating system the word 'sudo' causes the operating system to ask for your password before it will run the command.

Regards, Herman :)

---

### Post by conphuzed on 2008-05-24
yes i realized this just now ; ) sorry a/b that. i have added the fdisk output to the original post. thanks very much for your help

---

### Post by Bakon Jarser on 2008-05-24
what does your menu.lst file look like?

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by conphuzed on 2008-05-24
> **Bakon Jarser said:**
> what does your menu.lst file look like?

hi Bakon Jarser. yes i just edited my post as you were posting this...menu.lst appears blank (see original post for details)

---

### Post by Bakon Jarser on 2008-05-25
It looks like you may have tried this but in case you didn't:

Boot into the live Ubuntu cd.

When you get to the desktop open a terminal and enter.

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

grub >find /boot/grub/stage1

Whatever was returned for the find command use it in the next step (you are still at grub>.

grub >root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

grub >setup (hd0)

Then exit the grub shell

grub> quit

---

### Post by conphuzed on 2008-05-25
^^ yes i tried that : ( thanks for your help either way.

(i hate to whine even more, but i still don't really understand how all these guides and tutorials have you making changes through the LiveCD; i thought the whole point of the LiveCD is you can't change anything? as far as i can tell, none of the things i do are saved when i exit, even when i make a new user account)

---

### Post by pietjanjaap on 2008-05-25
First read everything you can find about grub, menu.lst

see if you have a backup file of menu.lst(name is different), put this back, with the right name.

Then boot normal:
choose ubuntu: try different harddsik to start, push "e" then you can change the hd to start, hd0,0 hd0,1 hd1,0 hd1,1 , first  is harddisk number, second is partion number. try all you have on haddisks.
Same is for windows

Let us see your menu.lst

This is how ubuntu starts:
- choose the harddisk to boot from.
-grub starts(if you don't see menu, reinstall grub(with superdisk)
-in grub choose linux/win then error, menu.lst is not good, change the haddisk numbers.


If you boot with supergrub then you can jump to win/linux without fixing everything, if you need it fast.

---

### Post by Bakon Jarser on 2008-05-25
You can access any drive that isn't encrypted with a live cd and change any files you want to.  This is why having a password on your OS doesn't make it secure.  Anyone with physical access to your machine can own it.

---

### Post by Bakon Jarser on 2008-05-25
So you can boot the live cd and access all files on the linux partition right?  Let's see if menu.lst is really there and if it's really blank.  From the live cd open nautilus as root.

```
gksudo nautilus
```

navigate to your linux partition which I think should be /media/sdd5.  From there go to /boot/grub and see if there is a menu.lst there and if there is see if it is really blank.

---

### Post by conphuzed on 2008-05-25
thanks for all your help so far guys. while you were writing, i managed to open a non-blank menu.lst by navigating to the newly mounted linux boot partition and finding it in /boot/grub instead of using the terminal.

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
# kopt=root=UUID=13b341dc-770e-4d23-9e80-c1ba6e685df8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd4,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd4,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=13b341dc-770e-4d23-9e80-c1ba6e685df8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd4,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=13b341dc-770e-4d23-9e80-c1ba6e685df8 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd4,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde1
title		Microsoft Windows XP Home Edition
root		(hd4,0)
savedefault
makeactive
map		(hd0) (hd4)
map		(hd4) (hd0)
chainloader	+1
```

---

### Post by Bakon Jarser on 2008-05-25
> **pietjanjaap said:**
> First read everything you can find about grub, menu.lst

see if you have a backup file of menu.lst(name is different), put this back, with the right name.

Then boot normal:
choose ubuntu: try different harddsik to start, push "e" then you can change the hd to start, hd0,0 hd0,1 hd1,0 hd1,1 , first  is harddisk number, second is partion number. try all you have on haddisks.
Same is for windows

Let us see your menu.lst

This is how ubuntu starts:
- choose the harddisk to boot from.
-grub starts(if you don't see menu, reinstall grub(with superdisk)
-in grub choose linux/win then error, menu.lst is not good, change the haddisk numbers.


If you boot with supergrub then you can jump to win/linux without fixing everything, if you need it fast.

super grub is a great program

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by confused57 on 2008-05-25
If your bios can be set to boot first to the drive with Ubuntu, you might try installing grub to the drive's mbr, using the instructions of Bakon Jarser, except setup (hd4):
```
sudo grub
find /boot/grub/stage1
```
this should return root (hd4,4), then:
```
root (hd4,4)
setup (hd4)
quit
```

You should get a grub boot menu when you boot first to the Ubuntu drive, but you'll need to change the root designation...highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd4,4) to (hd0,4), press "enter", then "b" to boot.    This change is temporary, but if it works you can make it permanent.

Added:  I would also recommend, as was suggested, to burn a copy of SGD if you're able to boot into Ubuntu.

---

### Post by Bakon Jarser on 2008-05-25
I think we might be getting somewhere.  Grub might have got a couple of numbers wrong.  Are linux and windows on the same drive?

---

### Post by Bakon Jarser on 2008-05-25
> **confused57 said:**
> If your bios can be set to boot first to the drive with Ubuntu, you might try installing grub to the drive's mbr, using the instructions of Bakon Jarser, except setup (hd4):
```
sudo grub
find /boot/grub/stage1
```
this should return root (hd4,4), then:
```
root (hd4,4)
setup (hd4)
quit
```

You should get a grub boot menu when you boot first to the Ubuntu drive, but you'll need to change the root designation...highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd4,4) to (hd0,4), press "enter", then "b" to boot.    This change is temporary, but if it works you can make it permanent.

Added:  I would also recommend, as was suggested, to burn a copy of SGD if you're able to boot into Ubuntu.

Wouldn't that set it up on the fourth partition of the first drive?  He only has one partition on the first drive.  If he was going to do that I think he'd need to change it to (hd0,0), or am I missing something?

Edit:  I like how confused answered a post by conphuzed :)

---

### Post by confused57 on 2008-05-25
> **Bakon Jarser said:**
> Wouldn't that set it up on the fourth partition of the first drive?  He only has one partition on the first drive.  If he was going to do that I think he'd need to change it to (hd0,0), or am I missing something?
(hd4) is the mbr of the Ubuntu drive, which is where he would need to install grub's IPL if he decides to boot first to this drive.  On a computer with multiple hard drives, I feel it's easier to boot first to the Ubuntu drive, then add an entry to boot Windows on another drive.

> Edit: I like how confused answered a post by conphuzed
Yes, I thought it was rather apropos that I attempt to assist...LOL

---

### Post by conphuzed on 2008-05-25
success! i have now booted into ubuntu. confused, this is the part of your post that i used:

> You should get a grub boot menu when you boot first to the Ubuntu drive, but you'll need to change the root designation...highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd4,4) to (hd0,4), press "enter", then "b" to boot. This change is temporary, but if it works you can make it permanent.

i didn't do the other stuff.

[COLOR="Red"]*remaining issues:[/COLOR]

1) you mentioned i can make this permanent...how?
2) Windows does not work (same error as before). i tried changing root (hd4,0) to (hd0,0) for Windows through grub, but this gave the same result. what should i change it to?

thanks so much for all the help

---

### Post by confused57 on 2008-05-25
> **conphuzed said:**
> success! i have now booted into ubuntu. confused, this is the part of your post that i used:



i didn't do the other stuff. you mentioned i can make this permanent...how? also i am going to check now to see if Windows works

thanks so much for all the help
Glad it worked...to make it permanent, open a terminal:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
change the root for your Ubuntu entries to (hd0,4)...also, be sure to change the line with #groot to (hd0,4).

If Windows is on a different drive than Ubuntu, you'll need map lines, e.g.:
```
title Windows <---Use any name you like
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
This entry would work if Windows is on the first partition of drive (hd1)...2nd partition would be (hd1,1).

You could also try using root (hd2,0), if (hd1,0) doesn't work:
```
title Windows XP
root (hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```
A similar entry could be made for (hd3,0), if neither of the above works...add the Windows entry to the very end of your menu.lst...after the line ###END DEBIAN AUTOMAGIC...

---

### Post by confused57 on 2008-05-25
I just noticed that Windows & Ubuntu are on the same hard drive, therefore you don't need the map lines e.g.:
```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```

---

### Post by conphuzed on 2008-05-25
okay i followed your instructions confused and everything works. thank you so much confused and everyone who helped me in this thread. time to start figuring out how this new o/s works!

cheers

---

### Post by adrian15 on 2008-05-27
> **confused57 said:**
> I just noticed that Windows & Ubuntu are on the same hard drive, therefore you don't need the map lines e.g.:
```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```

Hi Confused,

With those people with so many drives or with bad detected drives I have written a kind of [howto on the hard disk boot order](http://www.supergrubdisk.org/wiki/GrubHardDiskOrder).

Please feel free to use it in your answers.

And if you want to improve it by adding an actual example (about ubuntu not generating a valid menu.lst) you are also welcomed to do so.

adrian15

---

### Post by confused57 on 2008-05-27
> **adrian15 said:**
> Hi Confused,

With those people with so many drives or with bad detected drives I have written a kind of [howto on the hard disk boot order](http://www.supergrubdisk.org/wiki/GrubHardDiskOrder).

Please feel free to use it in your answers.

And if you want to improve it by adding an actual example (about ubuntu not generating a valid menu.lst) you are also welcomed to do so.

adrian15

Thanks Adrian,
    Your howto looks very helpful, I have  bookmarked the link and I know it will definitely help users with multiple hard drives.  I have one pc with 3 hard drives & have had 2 different distros(Mepis & Sabayon) incorrectly assign the grub boot order compared to bios boot order. I was able to modify the grub menu of the 2 distros, but Super Grub Disk would have made it easier.

Jim

---

