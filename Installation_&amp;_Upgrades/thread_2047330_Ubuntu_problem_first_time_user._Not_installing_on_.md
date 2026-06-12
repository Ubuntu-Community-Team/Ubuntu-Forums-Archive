---
title: "Ubuntu problem *first time user.* Not installing on USB drive."
date: 2012-08-24
forum: Installation &amp; Upgrades
---

### Post by unsatisfied on 2012-08-24
So I made my USB bootable, booted from the USB, but the only option I have to do an install on a [[COLOR=darkgreen]hard[/COLOR][COLOR=darkgreen]disk[/COLOR]]("http://forums.techguy.org/#"). 
 
The problem is that I don't have a working [[COLOR=darkgreen]hard[/COLOR][COLOR=darkgreen]disk[/COLOR][COLOR=darkgreen]drive[/COLOR]]("http://forums.techguy.org/#").
 
I wanted to install and use it from the [[COLOR=darkgreen]USB[/COLOR]]("http://forums.techguy.org/#") itself, but there's no options.
 
I am able to use the OS, but apparently it's not really *using* it entirely because it's not installed(the beauty of a LiveCD).
 
I tried to create a separate partition, but the current used one is mounted and can not unmount while used.
 
Every time I shut down and boot again, every thing is lost, no data is saved, the desktop goes back to default, and every thing is basically erased.
 
I thought Ubuntu could be installed and run from a USB like a hard disk drive.
 
This is really disappointing me, since I wasted last option resources to gain access to this operating system, and all for nothing.
 
And it's telling me that in order to use provided third-party applications, I must install on a hard disk drive, or another bootable device(I don't have any).
 
This is nonsense. I bought the USB to boot and store data there with and on the OS, but it doesn't do it.
 
I have tried multiple times to install, but for some stupid reason I can not create a partition on the USB stick because I'm using it and it is mounted, have no other drives, OS, bootable media, or the like, available to make a partition beforehand either.
 
This is absolutely ridiculous. How am I supposed to **not** use the partition I'm on when that's the only partition I have and have no other OS, computer, nothing to do this, and make another partition to install it there on the USB?
 
I have tried making a startup disc, but every time I select the .iso it shows a different file entirely instead of the right one, and the .iso is nowhere on the file system.
 
What do I do?

---

### Post by 1egoman on 2012-08-24
Hey unsatisfied,

Have you ever looked at unetbootin? It is a free piece of software that lets you make a bootable USB stick. However, you can also allocate space to save files so you can keep your files on a reboot. 

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

1egoman

---

### Post by Cheesehead on 2012-08-24
If you are new to Ubuntu, as the title suggests, you have chosen a very challenging task for yourself. It's much easier to understand what's happening and why after you have used an ordinary install for a while.

You can remake the USB stick to add persistence (easiest). The Live image you ar using is not a 'real' Ubuntu install - it's an image of a working system preserved on squashfs (read-only), and loaded at boot. Persistence will permit you to make some changes to the filesystem. It does **not** alter the read-only filesystem, but tacks on a set of addendum files. Obviously when your stick is filled, persistence ends.

Alternately, you can actually install a real Ubuntu system onto the USB stick. It will be a 100% real Ubuntu install, but very slow due to the low USB I/O speed compared to an HDD. The high I/O activity may also prematurely wear out your USB stick.

If you have multiple USB ports, it sometimes makes sense to use two USB stick, one for the system and another for your data.

If you insist on using Live environments, you'll need to learn about the command line, since you cannot change /etc/fstab without persistence. Start with the 'mount' command.

---

