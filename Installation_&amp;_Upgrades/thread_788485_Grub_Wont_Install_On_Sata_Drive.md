---
title: "Grub Wont Install On Sata Drive"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by akhirah on 2008-05-09
Much needed help required for a noobian.  Thanks in advance for those who respond.

My setup:

IDE PRIMARY MASTER: 80GB WESTERN DIGITAL
IDE SECONDARY MASTER: DVD WRITER 1
IDE SECONDARY SLAVE: DVD WRITER 2
SATA 1: 250GB HITACHI DESKSTAR
SATA 2: 250GB HITACHI DESKSTAR
SATA II: 200GB SEAGATE BARRACUDA (SET TO IDE IN BIOS)

I initially installed 3 operating systems on the 80GB Western Digital Drive without any hic-cups...grub installed fine and I was able to select and run each operating system.

I decided that I wanted to install all the OSs onto the faster and higher capacity 200GB seagate drive.

I installed XP first and created 4 partitions as follows:
30GB - XP
30GB - VISTA
30GB - UBUNTU
2GB - SWAP
Remaining space I left unallocated.

I installed the OSs in the following order XP, vista then Ubuntu. Upon 92%ish completion of the Ubuntu install it reported error - unable to install GRUB - fatal error! Oh no weep weep!

So I wiped the 80GB, created a 50GB partition and installed ubuntu on that instead, thinking it will create a boot loader including links to XP , vista and ubuntu (on 200GB Seagate). Which it did but none of them work! Except the ubuntu on the 80GB Hard Drive. Here is the output of the menu.lst file>>>
-------------------------------------------------------------------------
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=c9132b99-a1bc-41e8-89ba-941b7e68d389 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=c9132b99-a1bc-41e8-89ba-941b7e68d389 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.04 (8.04) (on /dev/sda6)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda6 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
------------------------------------------------------------------------

OPTION 1 PREFERENCE:

I would prefer to remove 80 GB Hard Drive and if possible install grub on the 200gb seagate. If not possible then,

OPTION 2:

Edit the above menu.lst to allow active/working links to XP, Vista, Ubuntu (On 80GB) or....

OPTION 3:

You recommendations.

Thanks again in advance

---

### Post by logos34 on 2008-05-09
Try this:

-remove the ide disk

-go into the Bios at startup and change the device boot order to 1. cdrom 2. hard disk.  Find the hard disk boot order submenu and change it so that the 200 gb sata is first.

-boot the ubuntu live cd and [write grub to the mbr of the 200 gb drive]("http://ubuntuforums.org/showthread.php?t=224351").

-reboot to the grub menu screen.  Press 'e' on ubuntu, 'e' again on the 'root' line and change to (hd**[COLOR="Blue"]0[/COLOR]**,5). 'enter' and 'b' to boot

-Hopefully that will get you into linux.  Then make the change permanent in grub:

**gksudo gedit /boot/grub/menu.lst**


change the root and 'groot' lines for ubuntu to (hd0,5).  Take out the map lines for windows:

> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd**[COLOR="Blue"]0[/COLOR]**,0)
savedefault
makeactive
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
root (hd2,0) -- **if this doesn't work try hd[COLOR="Blue"]1[/COLOR],0 (edit map lines too) **
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

---

### Post by akhirah on 2008-05-09
Try this:

> **logos34 said:**
> -remove the ide disk

Just to clarify, (which I forgot to mention, really sorry, the noobness shows!) I tried installing ubuntu on the 200GB twice, the second time round I disabled the IDE Primary Master and set the 200GB as HD Boot..same error -cant install grub

Do i need to physically disconnect the device? Is that necessary?

> **logos34 said:**
> -boot the ubuntu live cd and [write grub to the mbr of the 200 gb drive]("http://ubuntuforums.org/showthread.php?t=224351").

(Point to note, the 80GB HD is still physically connected to mobo but disabled IDE Master in BIOS) I followed the instructions in that link you provided without success. Using the command:

find /boot/grub/stage1

Error 15:File not found 
(To some extent I expected this as grub is not installed anywhere on the machine..am i correct? as it was unable to install it during setup)
I tried manually mounting to the Ubuntu installtion on the 200GB HD to run grub but that reported the same error 15: file not found

My suspicion (semi-educated guess) is that the problem relates to the Hard Drive connected to the SATA II port...? wat ya think?

---

### Post by Pumalite on 2008-05-09
See if Super grub can boot Ubuntu:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.

---

### Post by Pumalite on 2008-05-09
Something to read:
[http://ubuntuforums.org/showthread.php?t=46003](http://ubuntuforums.org/showthread.php?t=46003)

[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by logos34 on 2008-05-09
> **akhirah said:**
> Do i need to physically disconnect the device? Is that necessary?

Isn't that what you want?

> OPTION 1 PREFERENCE:

I would prefer to remove 80 GB Hard Drive and if possible install grub on the 200gb seagate. If not possible then,

> (To some extent I expected this as grub is not installed anywhere on the machine..am i correct? as it was unable to install it during setup)

yeah, forgot, you're right.  Use Super Grub disk like Pumalite suggested to boot into ubuntu. then run

**sudo grub-install /dev/sda** (or whatever the drive is seen as)

**sudo update-grub**

Hopefully that will work

---

