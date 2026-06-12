---
title: "Grub Did not install"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by jwsawyer on 2007-07-05
I messed up my computer and had to reinstall ubuntu.  Grub did not install even though it said it did.  I booted with a live CD and checked the file where it is supposed to be and it was empty.

I tried all the tricks I found in various forums to include making a grub iso cd.  Nothing has worked.

On hda I have Windows XP, Ubuntu Feisty and Ubunt Gutsy.  I am unable to boot onto any of them.  There are respectively hda1, hda2 & hda3.

Until today all worked fine until I messed up Feisty and attempted to do a clean reinstall.  The MBR appears to be totally wiped clean.

---

### Post by ubuntu.daemon on 2007-07-05
heh weird, try making a knoppix live cd, bc on that there is a program call QTparted which will let you delete partitions and whatnot,which you just deleted you fresh ubuntu install, then make an alternate-install disk, and use that empty space, and do a guided install.  Then hopefully ubuntu will install grub to the mbr this time

btw what even happen when you boot?  does it say grub 1.5 loading??

---

### Post by jwsawyer on 2007-07-05
> **ubuntu.daemon said:**
> heh weird, try making a knoppix live cd, bc on that there is a program call QTparted which will let you delete partitions and whatnot,which you just deleted you fresh ubuntu install, then make an alternate-install disk, and use that empty space, and do a guided install.  Then hopefully ubuntu will install grub to the mbr this time

btw what even happen when you boot?  does it say grub 1.5 loading??

Yes it says it's loading and then it just reboots.

---

### Post by confused57 on 2007-07-05
> **jwsawyer said:**
> Yes it says it's loading and then it just reboots.
Have you tried using the live cd to install Gutsy's grub to the mbr?:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Then you might be able to use symlink to boot Feisty:
[http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink](http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink)

If you're able to boot into Feisty, maybe you could try installing grub, possibly through Synaptic Pkg Mgr.

---

### Post by ubuntu.daemon on 2007-07-05
If you are saying that it says grub 1.5 loading, then okay so now we at least know that it did install, it is just messed up.  was it after you did ubuntu feisty install that it got messed up?? or gutsy?   im guessing it probably just installed to the base of that one install hda 2 or 3, his idea seems okay, just get into a live-cd, but do a update-grub, on feisty and see what happens

---

### Post by jwsawyer on 2007-07-05
I ran the command:

sudo gedit /boot/grub/menu.lst

and all I got was an empty file.

I am on the Feisty liveCD so I don't know if that makes a difference.

---

### Post by confused57 on 2007-07-05
> **jwsawyer said:**
> I ran the command:

sudo gedit /boot/grub/menu.lst

and all I got was an empty file.

I am on the Feisty liveCD so I don't know if that makes a difference.
You need to mount your root partition to access your menu.lst:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by jwsawyer on 2007-07-06
Okay, got that.  Here is what I get:


title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3bc970a7-e0fa-4305-b975-82e209e17883 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3bc970a7-e0fa-4305-b975-82e209e17883 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by confused57 on 2007-07-06
Try reinstalling grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

root (hd0,1) should be your Feisty root partition...setup (hd0) will reinstall grub to your mbr

If this doesn't work, you could try installing Gutsy's grub to the mbr...

---

### Post by jwsawyer on 2007-07-06
I finally got it to work.  I edited the grub list and deleted all other systems except for the two I currently have on my hda drive.  I had to many copies of too many kernels, I think and it was hanging it up.

I&#314;l add the other 5 systems later when I reinstall gutsy.  Thanks for all the help.

---

