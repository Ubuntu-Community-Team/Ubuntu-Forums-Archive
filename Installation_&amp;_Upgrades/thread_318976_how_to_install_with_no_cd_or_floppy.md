---
title: "how to? install with no cd or floppy?"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by Wall86 on 2006-12-14
ok, i have an old dell latitude c400, and i was wondering if there is any way to install ubuntu besides using a cd-rom drive or floppy drive.

i have not been able to figure out how to boot to a usb flash drive

i do have an e-net port, as well as a wireless b card

anyone know of any other ways?

any help is greatly helpful.

---

### Post by K.Mandla on 2006-12-14
> **Wall86 said:**
> ok, i have an old dell latitude c400, and i was wondering if there is any way to install ubuntu besides using a cd-rom drive or floppy drive.

i have not been able to figure out how to boot to a usb flash drive

i do have an e-net port, as well as a wireless b card

anyone know of any other ways?

any help is greatly helpful.
[Netbooting]("https://help.ubuntu.com/community/Installation/Netboot") might be an option. Or maybe an external drive that might boot (I forget what the BIOS is like on the C400; I think my Inspiron 8000 allows booting from an external device).

You might also consider pulling the drive, installing it on another machine and then putting it back in the C400. Reconfiguration might take some effort, though.

Also, supposedly, you can zip an entire installation, copy it to a hard drive, unzip and recofigure. I've never done that, although in some strange way, it sounds like fun. :shock:

---

### Post by Wall86 on 2006-12-14
ok, is there any way to boot to a dos prompt? without using a diskette or cd? if so i could consider just placing all of the files onto the HDD then just running them right off of the drive? i could also see this not liking this due to the formating of the hard drive during install tho..

how hard would it be to reconfigure an install? i have been a windows user (yuck) and im currently trying to slowly move to ubuntu, and i have very little experience with linux, could this be a viable idea for a person like me? and would it help me learn a lot?

---

### Post by K.Mandla on 2006-12-14
That might be the tricky part. Check the BIOS, but I think the C400 is analogous to my I8000, and in that case you might be able to boot from an external device. But then again, you might be limited to modular drives. 

I think with that series you'll need either a floppy or a CD-ROM to get anything done. I know my I8000 won't boot from USB, unless I have a CD-ROM on hand and a CD with USB drivers in place. 

In addition, installing Ubuntu *from *a flash drive is one of those elusive things I've been fighting for a year or so. I'm not aware of any way to do it, to be honest.

Reconfiguring isn't impossible, but it would be one of those teeth-gnashing, hair-pulling things that isn't really the best idea if you're new to Linux on the whole. Ubuntu is very forgiving, on the grand scale of things, but trying to tinker with all the stuff that would need changed ... well, I don't think I would really want to go that route if I didn't have to.

Have you looked into spare parts for it? Modular CD-ROM drives for that series [run less than $10 on ebay]("http://cgi.ebay.com/DELL-INSPIRON-LATITUDE-CD-ROM-CD-DRIVE-C610-C400-C600_W0QQitemZ170060668478QQihZ007QQcategoryZ177QQssPageNameZWDVWQQrdZ1QQcmdZViewItem"), and it would save you a mound of stress.

---

### Post by Wall86 on 2006-12-14
the only prolbem i have really found, is how dell made it so you also need the modeluar bay as well, this is a very small lightweight laptop,

would there be a way of my installing over network? and how difficult could this process go? using the most recent release of ubuntu. I just had a very bad experience with vista rc1 on my desktop, and i do not feel like fiddling too much right now.

for doing a network boot, would i possibly need a floppy drive to tell it to boot from network? like how exactly would something like that work?

---

### Post by K.Mandla on 2006-12-15
That's usually the case. If you don't have a CDROM, you really need a floppy drive. 

Netboot isn't impossible, but it does require a few more steps, plus a host machine to connect to. And unless I'm mistaken, you have to have a floppy to trigger the netboot.

The only other solution I can think of is to pull the hard drive, copy the installation ISO to the drive, set up Grub to boot the ISO, then install it to another partition. But that's some serious acrobatics, and a huge pain just to install.

By the way, is this your machine?

[http://www.mrnotebook.com/active%20systems/C400.htm](http://www.mrnotebook.com/active%20systems/C400.htm) 

If so, shouldn't you have an external floppy or external optical drive?

---

### Post by shiggs on 2006-12-15
> **Wall86 said:**
> the only prolbem i have really found, is how dell made it so you also need the modeluar bay as well, this is a very small lightweight laptop,

would there be a way of my installing over network? and how difficult could this process go? using the most recent release of ubuntu. I just had a very bad experience with vista rc1 on my desktop, and i do not feel like fiddling too much right now.

for doing a network boot, would i possibly need a floppy drive to tell it to boot from network? like how exactly would something like that work?


as said network boots are tricky, but should be able to set it up in your bios, (look for boot order) not all machines support it and not all network cards (NICs) are widely supported

what about using a USB flash drive?

---

