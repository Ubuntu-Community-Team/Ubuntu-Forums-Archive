---
title: "Installation Questions (NOT THAT BASIC)"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by GuitarRocker2562 on 2006-06-18
Ok, right now I have windows XP MC on my PC. The Harddrive is 200GB and I connect to the internet using the NETGEAR WG111 v2 wireless adapter. 


This is what I want to do:

"Install Ubuntu 6.06

Install Windows Vista B2

Keep Windows MC

Triple Boot them."

So ok, How exactly do I do this (I don't care if my files get erased). Also like I mentioned I have a NETGEAR WG111 v2 wireless adapter, what do I need to do to get this to work in 6.06???


PLEASE HELP, I AM A LINUX NOOB, SO CAN YOU MAKE IT IN TERMS I CAN UNDERSTAND!!!!!!!!

Thanks!!!

---

### Post by GuitarRocker2562 on 2006-06-18
Why won't anyone help???!!!???!!!

---

### Post by aysiu on 2006-06-18
[QUOTE=GuitarRocker2562]Why won't anyone help???!!!???!!![/QUOTE]
It's usually because people don't know the answer.

---

### Post by GuitarRocker2562 on 2006-06-18
I think I found a site with the triple boot thing, could someone test it or let me know if it looks like it will work?


Quote:

"As I recall, this is possible without too much difficulty. If you install a linux boot loader, make SURE you install it to the same partition that Linux resides in. DO NOT install the boot loader to the MBR. Next, copy the 1st 512 bytes of the Linux partition to a file. You can do this with a "dd" command as follows:

dd if=/dev/hda? of=/floppy/bootsect.lnx bs=512 count=1

Make sure you replace /dev/hda? with the appropriate string for your linux partition (it may be /dev/sda?, depending on your OS). Also, replace the output destination as appropriate. I've assumed that /dev/fd0 is mounted to /floppy, here. Make it an MS-DOS formatted floppy, since you'll need to read the file w/ Windows.

Next, boot into Windows and copy bootsect.lnx to the root of your C: drive. Add a line in boot.ini that reads:

C:\bootsect.lnx="Ubuntu"

(replace the text in quotes with whatever you want) Happy booting!"


Also, does anyone know how to get the NETGEAR WG111 v2 to work (or is it alredy supported in 6.06?)

Thanks

---

### Post by aysiu on 2006-06-18
I would install Grub to the MBR. Grub, 90% of the time, automatically detects Windows and adds Windows to the boot menu.

Windows, on the other hand, needs to be forced to recognize Ubuntu (hence, all that *dd if=* crap).

I don't know what Windows MC is, but if you have Windows installed first, install Ubuntu second, and everything should be good.

Desktop CD:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

Alternate CD:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

I don't know anything about Netgear, but you can generally see how well things are supported when you boot up the live CD, which gives you a preview of how Ubuntu will run on your computer (well, it'll run a bit more slowly in the live session, of course).

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport) may not be a bad place to look, too.

---

### Post by eternalsword on 2006-07-16
for netgear wg111, check out my thread at [http://www.ubuntuforums.org/showthread.php?t=212365](http://www.ubuntuforums.org/showthread.php?t=212365)

---

### Post by ader10 on 2006-07-16
Install linux last. You don't want to have everything installed and then loose it because of the windows boot loader. With that out of the way, you should partition the hard drive with something like QTParted, which you can get on a knoppix live cd. Make sure to leave room for xp and "mc" while keeping at least 300 mb of swap space for linux and at least 2 gb of space. You should probably go with 1 gb of swap space and evenly distribute the other partitions. Make sure not to delete any data and back up your system. Don't forget to configure grub to be able to boot from all your operating systems.
Hope that helped.

---

### Post by eternalsword on 2006-07-16
what this guy wants is to triple boot Windows XP (Media Center Edition), Windows Vista, and Ubuntu.  First, you should get XP and Vista set up.  Maybe check out [http://www.lifehacker.com/software/top/windows-vista-beta-how-to-dual-boot-windows-xp-and-windows-vista-179906.php](http://www.lifehacker.com/software/top/windows-vista-beta-how-to-dual-boot-windows-xp-and-windows-vista-179906.php)

but make sure to leave space for 512 MB for swap and your ubuntu partition.
once you have XP and Vista up, then install ubuntu and install grub to the MBR.  Grub will automatically detect both of the Windows Partitions and then you should be able to triple boot.

---

### Post by PingunZ on 2006-07-16
first you install vista on the partition you created before in XP 
then you install ubuntu with the Grub MBR on another partition
Now you'll have the choice of XP, Vista and Ubuntu at startup ;)

Btw: I hope you have a good computer cause vista is realy slow

Grtz PingunZ

---

### Post by bigken on 2006-07-16
when install windows os you always install the oldest one 1st so it would be winxp then vista then ubuntu ;)

---

