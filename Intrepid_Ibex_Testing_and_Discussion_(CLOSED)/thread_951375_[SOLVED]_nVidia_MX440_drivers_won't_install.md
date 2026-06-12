---
title: "[SOLVED] nVidia MX440 drivers won't install"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Tails5 on 2008-10-18
Hi, I've only just recently installed Ubuntu (8.10 Intrepid Ibex) and I can't make my graphics drivers work, every time I use the install that comes up about "Proprietry Drivers" if I choose 78 or 96 it just says "Installing" then dissapears or crashes at the end. If I run the installer from nVidia, it fails to download the kernel from it's website and then fails to build the kernel for my build. My hardware is:

nVidia GeForce MX 440
AMD Athlon XP 1800+ @ 1.54GHz
512MB RAM
/dev/hda = 80GB Windows Vista drive (SMART Failure)
/dev/hdb = 8GB HD, Partitioned as follows:
[LIST]
[*]hdb1 = Windows ME
[*]hdb2 = Windows 98
[*]hdb3 = FAT32 Storage Drive
[*]hdb4 = Extended Partition
[LIST]
[*]hdb5 = 512MB Linux Swap Space
[*]hdb6 = 6GB Ubuntu (mount: /)
[/LIST]
[/LIST]

I'm also downloading the ISO for Ubuntu 8.04 to test if it will be any different, not being a beta and all. But I'd prefer to not have to reformat my Linux partition.

---

### Post by Elfy on 2008-10-18
Old nvidia legacy cards do not at the moment work with the new xorg in intrepid.

[http://ubuntuforums.org/showthread.php?t=870981](http://ubuntuforums.org/showthread.php?t=870981)
[http://www.nvnews.net/vbulletin/showthread.php?t=113974](http://www.nvnews.net/vbulletin/showthread.php?t=113974)

You can use the nouveau driver, but it does not at the moment support 3d or tvout - 
[http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)

I had some issues with it to start with but it does work now for me, but there are some issues with cpu and memory usage when using nouveau, I don't think I'd try with 512Mb.

8.04.1 is fine with the driver, I am running both at the moment

---

### Post by robert shearer on 2008-10-18
> 8.04.1 is fine with the driver, I am running both at the moment

Yes, same here. +1

---

### Post by Tails5 on 2008-10-18
Thanks, my Hardy Heron download will be done in four and a half hours, when Intrepid is out of beta do I just upgrade and my drivers will work again?

---

### Post by Elfy on 2008-10-18
Unfortunately it's not as simple as that, your graphics card will only work as it has up until now when nvidia bother to release the driver.

If you look at the nvidia forums you will see that other distros, which started using the new xorg before, have been waiting for longer.

---

### Post by Tails5 on 2008-10-18
Okay - Thanks for your help, I guess I'll be sticking with Hardy Heron for a while - unless I get a new card. *marks thread as solved*

---

### Post by Elfy on 2008-10-18
Yea - I'm hanging on to the card for the moment, I really need new mobo, processor, memory and graphics so it can wait - unfortunately lol

If it all gets sorted and I remember I'll post back here, if you're subscribed to it you'll get to know.

But I don't hold out a lot of hope tbh..

---

