---
title: "Installing 12.04 with wubi not working"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by ckrudelux on 2012-06-07
Hi everyone!
I found my self in a odd situation all my installs of Ubuntu has been easy and working like a charm until my newest member in my computer family didn't want to play nice at all.

The computer is a Dell Latitude c400 the USB port is broken so I can't start it with a USB drive and I got no CD drive for it.

Then I got it windows xp was and is installed on it filled with crap. I downloaded a wubi.exe and started installing the Ubuntu operating system.

It rebooted and first thing I got was an prefix error and sits like that for a couple of mins then I get into the ubuntu system where it is going to finish the install after formatting some file it just stops and does nothing with the load cursor on the screen.

I can how ever while it's booting up to Ubuntu change to boot to demo instead of completing the install.

I've tried a netboot but don't work get a similar result as then I try to complete the install it just leaves me with a blank screen, in detail:

downloaded the linux file and initrd.gz from cdimage.ubuntu.com/netboot

booted into them with grub followed the instructions where it basically asked me to set the keyboard layout and then it loads usb drivers and after that the screen is blank, get some graphical issues during this setup but it's still readable.

Any Idea on what to do, don't use to complicated terms or add description to what it is so I learn the terminology of what you are talking about.

What I want is to format the disk and have a fresh install but I would be happy just to have it installed as it looking now.

---

### Post by ckrudelux on 2012-06-11
*Bump*

---

### Post by coffeecat on 2012-06-11
According to what I've found by googling, your Dell Latitude c400 is a 10-year old design with the legacy Intel 830M graphics chipset. My guess is that the problems you are seeing with your wubi install are mostly to do with trying to run this graphics type. I have no experience of it, but I would imagine the chances of getting an up-to-date version of Ubuntu (or any Linux distro) running with that graphics chipset are low. Perhaps someone else has a more optimistic view. 

Another factor is the RAM. According to one page I found the C400 came with only 128MB, but was upgradable to 1024MB. How much RAM do you have?

Even if you found a version of Linux that would handle that graphics chipset, the facts that your USB port is not working and that you have no CD drive make it impossible to run installation media with that machine. A net install usually require you to run the mini iso from a USB device or CD so that you can format the HD prior to installation. The only way I can think of to get around all that is to take out the hard drive and attach it in some way to another machine which you can use to install something to the HD. You need to know how to direct the installation of grub to the proper place if you do this and, of course, unless you use a machine with the same 830M graphics, you won't be able to test whether this is going to be a problem with whatever you install.

---

