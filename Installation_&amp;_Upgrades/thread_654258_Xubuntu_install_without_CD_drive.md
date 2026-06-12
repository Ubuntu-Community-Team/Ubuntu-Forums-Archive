---
title: "Xubuntu install without CD drive?"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by Taxi on 2007-12-30
I've got an old laptop (CTX EzBook 700E) I'm trying to resurrect. It's got 96 megs of RAM, a 233 MHz processor, and a 6 gig HD. I'm thinking Xubuntu would be perfect for it (and me - I'm already an Ubuntu user but I tried Xubuntu a little from a Live CD and I think I might end up liking Xfce better than GNOME anyway). However, there are a couple problems outside of the limited system resources (not enough RAM for the Xubuntu Live CD, but the Alternate Install disc should work):

1) No CD drive. There is one, but I can only rarely get it to recognize discs despite doing my best to clean dust off of the lens and out of the drive in general (though it wasn't really visibly dirty to begin with). I'd be happy to try until it worked, but from what I've read about the laptop model online I don't think it is capable of reading burned CD's at all. It does have a working floppy drive, though.

2) The laptop cannot boot from USB.  I have a 1 gig thumb drive and a USB CD drive if it's possible to boot something from floppy that will recognize and allow me to install from one or both of them.

2) No on-board or PCMCIA ethernet card. I'd have to connect to the network via a USB-ethernet adapter (Belkin F5D5050). I don't really know how net installs work, so I don't know if it would be possible to start up that kind of driver.

Can anyone suggest ways this can be done? Based on my inexperience, easier is definitely better, but I'd appreciate hearing any options, especially if you can also point to a good tutorial so I can decide which might be best for my situation.  Thanks!

---

### Post by p_quarles on 2007-12-30
Yes, you can use a boot floppy to initialize installation from the USB CD drive. Here's a guide:
[https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies)
and another one:
[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

Yes, it will be slightly more complicated than the regular installation procedure, but if you're willing to put the time in, it'll get the job done.

By the way, Xfce4 is growing out of its reputation as a "light" desktop. I seriously doubt that you're going to get much performance out of a 96 MB machine. I would humbly recommend Fluxbuntu, a Fluxbox-based flavor of Ubuntu:
[http://fluxbuntu.org/](http://fluxbuntu.org/)

That will certainly run on your system. Don't expect miracles, but you'll get much better performance than with Xubuntu. There are also the lightweight distros: Damn Small Linux and Puppy Linux. I haven't tried either, and have heard they can both be kind of a pain to set up. But they will run decently on as little as 32 MB of memory.

Btw: I use Fluxbox on my desktop and laptop, both of which have 1 GB of memory. It's not just lightweight, it's also a very cool GUI, and almost infiinitely customizable. Fluxbuntu is a good place to start, though, because it comes with a lot more functionality than the default, unconfigured Fluxbox setup.

---

### Post by seshomaru samma on 2007-12-30
I had a similar situation with an old Toshiba laptop , no CD , no bootable usb , no floppy.
It was running win2k. At first I tried PXE boot install but at the end I used [Lubi]("http://lubi.sourceforge.net/lubi.html") to install Ubuntu from the windows partition. For a 96MB box you should install Ubuntu Server and then add a light desktop environment like Fluxbox or IceWM
If you have a running OS you can do that.
Another option is to take the harddisc out and install using another box, Ubuntu should recognise the new hardware once you put it back in the original box

---

