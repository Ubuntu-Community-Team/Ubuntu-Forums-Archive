---
title: "Trouble installing Ubuntu"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by jesusfreak107 on 2008-04-29
Ok, I want to install Ubuntu 7.10, or 8.04 on this machine:
Tochiba Satellite 1730 
700MHz Processor
192MB RAM
10GB HDD, 1 partition, NTFS
2.4GHz 108.11G Hawking SkyHawk Wireless PC Card.
Windows 98SE Pre-installed version.
CD Drive is non-functional.
Floppy 
Drive is non functional
I have a external Logitech trackball mouse installed on PS/2 slot, via USB-to-PS/2 adapter.
I CAN use SD cards, via an adapter plugged into the USB 1 slot.
New Power cord.
RAM cannot be upgraded anymore.
I have not been able so far to get an external DVD drive working, and the BIOS will not recognize it.
As far as i know, the BIOS cannot boot off of anything other than the internal CD drive, the floppy drive, and the HDD. 
13 inch screen
max resolution is 800x600
annoying low refresh rate on screen, everything has a trail.

Ok.  I want to install Ubuntu on this machine.  I have another PC running Ubuntu 7.10 (specs in signature), the only version of Windows I would ever install permanently, and of my will, is XP, and we do not have an extra copy of that. As I said, I do not have a CD drive, internal, or external, that I could boot a Live CD off of.  I can download an ISO, but it will take 3&1/2 hours (I will do it, though.).  Wubi will not work, I do not have enough RAM.  I need a way to install Ubuntu.

Thanks in advance.
:guitar::guitar::guitar:

---

### Post by kk0sse54 on 2008-04-29
You can install linux on a floppy drive and boot from there although I don't ubuntu would work for that.....

---

### Post by picopir8 on 2008-04-29
Most computer also support network boot.  If so do the following:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

That page also has a link to the mini.iso.  That can be extracted and the files copies to your flash drive and booted off that if possible.  Otherwise if you can boot off a floppy linux that allows you to access the flash drive, perhaps you can then copy the files to your hard drive to bood them (they are loaded to ram so it is okay if they are on the same drive you want to install linux to).

Otherwise, just remove the hard drive and connect it to another computer, and put the contents of the mini.iso on it.

Oh, if you do extract the mini.iso, the only change you need to do is rename isolinux.cfg to be syslinux.cfg.

---

### Post by jesusfreak107 on 2008-04-29
no, I want a full install of Ubuntu, or some variant.  Thanks anyway, though.

---

### Post by jesusfreak107 on 2008-04-29
> **picopir8 said:**
> Most computer also support network boot.  If so do the following:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

That page also has a link to the mini.iso.  That can be extracted and the files copies to your flash drive and booted off that if possible.  Otherwise if you can boot off a floppy linux that allows you to access the flash drive, perhaps you can then copy the files to your hard drive to bood them (they are loaded to ram so it is okay if they are on the same drive you want to install linux to).

Otherwise, just remove the hard drive and connect it to another computer, and put the contents of the mini.iso on it.

Oh, if you do extract the mini.iso, the only change you need to do is rename isolinux.cfg to be syslinux.cfg.
I do not know how to make a floppy drive tell the computer boot off of a USB or CD device, I have never used a floppy before.  I also do not know how to do a network boot.  I am mainly looking for a way to tell GRUB to boot off an iso file.

---

### Post by jesusfreak107 on 2008-04-29
Oh, I downloaded the installer for Ubuntu, that works through GRUB.  I do not remember where I got it, but I downloaded 2 files, 
"linux" and "initrd.gz", and told GRUB to boot off of them.  It was working, except that it needs to connect to the servers and download Ubuntu.  This would not be a problem, except that it keeps trying to use Ethernet, and I use wireless.  if anyone knows the solution to that, I would love to hear it, but I now have network access to my Toshiba, through my default computer, and I am downloading the iso at 800KB/s, and I am just going to transfer it over the network.  Therefore, I would prefer an option that enables me to boot the iso file with GRUB.  I have heard of the option where you make a fake CD drive, with a partition editor, and put the iso in there, and boot off of it, but I no not have the ability to do that in Win 98.  If you know of any tools that can do that (resize and repartition an internal HDD), I'd love to hear about them.

---

### Post by kk0sse54 on 2008-04-29
In order to make your computer boot off a USB, CD, or floppy you need to change your BIOS settings which can be easily done when your computer first is turned on and starts loading and you get the little message change settings press f12 or delete or maybe something else depending on computer. Then go to boot order or boot configuration ,again different for different computers, and just change the order which your computer looks for OS's to boot

---

### Post by jesusfreak107 on 2008-04-29
> **C!oud said:**
> In order to make your computer boot off a USB, CD, or floppy you need to change your BIOS settings which can be easily done when your computer first is turned on and starts loading and you get the little message change settings press f12 or delete or maybe something else depending on computer. Then go to boot order or boot configuration ,again different for different computers, and just change the order which your computer looks for OS's to boot
Yes, I am well aware of that.  However, this lappy is an old machine, and does not have that capability.

---

### Post by kk0sse54 on 2008-04-29
Well then sorry mate can't help you then I can get it to work on newer machines but i don't know of a way to boot off iso's on an older machine still running windows 98. Goodluck with your quest though and I hope you find an answer as I would be most interested in finding out how.
                   
                                               best of luck
                                                      cloud

---

### Post by picopir8 on 2008-04-29
> **jesusfreak107 said:**
> I do not know how to make a floppy drive tell the computer boot off of a USB or CD device, I have never used a floppy before.  I also do not know how to do a network boot.  I am mainly looking for a way to tell GRUB to boot off an iso file.

The link I provided will walk you through doing a network install.  I did not know how to do it my first time either but it was easy to follow and worked.

For the floppy approach, no the floppy would not boot the USB.  Something like floppix will boot linux off a floppy.  If you are lucky it may allow you to connect your flash card once booted, and allow you to wipe your hard drive and put the contents of the mini.iso on the hard drive.  Then reboot from the hard drive and the installer should launch.

---

### Post by jesusfreak107 on 2008-05-01
> **picopir8 said:**
> Most computer also support network boot.  If so do the following:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

That page also has a link to the mini.iso.  That can be extracted and the files copies to your flash drive and booted off that if possible.  Otherwise if you can boot off a floppy linux that allows you to access the flash drive, perhaps you can then copy the files to your hard drive to bood them (they are loaded to ram so it is okay if they are on the same drive you want to install linux to).

Otherwise, just remove the hard drive and connect it to another computer, and put the contents of the mini.iso on it.


Mine does not support network boot, and even if it did, it is wireless, so it would most likely not work.  

> Otherwise if you can boot off a floppy linux that allows you to access the flash drive, perhaps you can then copy the files to your hard drive to boot them 

How would I make such a floppy?  and what files?  Would I need to extract the contents of the .iso onto my flash drive, or would the plain iso work?

> Otherwise, just remove the hard drive and connect it to another computer, and put the contents of the mini.iso on it.

No can do.  It is a laptop, and I cannot get the case off, I have tried.  Plus, I would have to buy an adapter, and i do not have much money right now, or I would just have bought a new laptop, instead of fixing up an old one in the garage.

Any other thoughts, people?
Answers?  (besides "42")

---

### Post by jesusfreak107 on 2008-05-01
is there a bootable linux system that actually fits on a floppy?  if so, I could do that.  However, I will need a link to it, and some comprehensive directions, I am not *that* fluent with a command line, yet, I am still learning (thus the need for directions)

---

