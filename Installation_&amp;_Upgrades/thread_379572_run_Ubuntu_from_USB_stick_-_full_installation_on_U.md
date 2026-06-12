---
title: "run Ubuntu from USB stick - full installation on USB stick"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by alperyilmaz on 2007-03-08
I want to install ubuntu on a usb stick (2GB). I don't want an installation acting like liveCD (or let's call it liveUSB) with limited capabilities. On internet, most of the instructions involve creating FAT partition and ext2 partition, named casper-rw. Then liveCD contents are copied to FAT partition, USB drive is made bootable and ... 

But this is not a fully functional installation. when you install ubuntu on your harddrive you observe the following behavors:
- there are ext2 and swap partitions
- you are asked to enter user password
- all the installed software is kept

you don't have these behavors from a usb installation..

Can someone help me to make a full install of Ubuntu on a USB stick? 
My aim is to have openoffice installed and on the other hand I'll study perl and bioperl programming (LiveCD and LiveUSB does not keep the files saved) and explore Ubuntu. A minimal installation is also fine, but I need a FULL installation. 

I hope there's someone out there who can help..

thanks,
alper

---

### Post by eapache on 2007-03-08
I'm not entirely sure if you have room for a full install on only 2Gb, you might want to try xubuntu instead.

For the installation, I think you can just mount the usb stick from livecd, then format and install on it as you would any other disk... I don't know if that will work, but it's worth a shot if you have the time. Sorry I can't be of more help.

---

### Post by frodeaa on 2007-03-23
I actually did this yesterday on a 4GB Cruzer stick, and it works just fine. However you won't be able to install it on a 2GB stick I believe.

I did some partitioning, and when I had the main size set to around 2000MB I got a message saying it had to be at least 2GB. Then you need the swap drive of at least 256MB on top of that, which means a 2GB (which is actually around 1.8 or 1.9GGB) is too small.

Anyhow, what I did to install it was the following:

1. Download LiveCD.
2. Remove my internal harddrive (to make sure you don't mess it up).
3. Boot LiveCD.
4. Insert USB stick, Ubuntu should find this automagically and mount it for you (did for me at least).
5. Run the install from the desktop.
6. Put in your info and partition options.
7. Install GRUB on hd0, which should be default. This is why I removed my harddrive. I'm pretty new on Linux and I couldn't figure out if it thought hd0 was my actual harddrive or my USB stick. Better safe than sorry.
8. Reboot and set BIOS to boot from USB

Now I have to say that performance wise it's not very impressive. It's at times quite sluggish, especially when minimizing and maximizing windows, as well as when you open and close programs. For some reason my internet is also paingfully slow. It takes between 5 and 30 seconds from I type in an URL to it actually starts loading it. When it firsts starts though, it's quick. I was downloading updates at 105-110KB/sec, which is close to my maximum, but it took about 30 seconds from I clicked the "update" until it actually started.

I was thinking about using Ubuntu on a USB drive for a completely seperated PHP/C++ coding enviroment, so I didn't have to mess around with my Vista installation, but the performance issues running from the USB drive has kinda made me reconsider. Maybe there's some sort of tweak I can do to make it a little more responsive... I'll have to try a few things out I guess.

---

