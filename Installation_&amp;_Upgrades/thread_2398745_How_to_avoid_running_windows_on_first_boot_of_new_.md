---
title: "How to avoid running windows on first boot of new Dell PC?"
date: 2018-08-16
forum: Installation &amp; Upgrades
---

### Post by dankegel on 2018-08-16
Hi!
I'm installing Ubuntu on a bunch of new Dell 8930 PCs. 
They appear to ship suspended, so when you power them on, they resume to Windows Setup
rather than do a POST.  That means they ignore the keyboard, and you can't get a boot menu.
You're forced to go through Windows Setup.

But I don't want to do that, not even once, not even a little bit.  I want to abort out of
the Windows setup or not resume into it at all, and instead boot straight to an
Ubuntu usb install.

Anyone know how to coax a new Dell PC to POST rather than resume?  
(I know, I could click through and accept the windows license, and it would probably work,
but I don't want to do that.)

I did it successfully with the first two systems, but the third one refused to do anything
but a) boot loop or b) resume windows setup until I finished setup and let it boot to windows,
where I grudgingly turned off fast boot (turning off secure boot also seemed neccessary
to get out of the boot loop) and shut windows down for the first and last time.

Is there some key that 'bios' pays attention to when it's in that "I'm going to
ignore the keyboard and resume from disk" mode?

---

### Post by TheFu on 2018-08-16
Pull the HDD. Put it on a shelf.  Should you need warranty service, you'll have it.

Put in an empty replacement HDD/SSD that fits.

---

### Post by dankegel on 2018-08-16
That's good advice.    

But I'm going to keep living dangerously, and overwriting the m.2 disk that came with the systems for now.   I do have one dual boot system, so I have the bits if I need them, more or less.

---

### Post by TheFu on 2018-08-16
At least make an image of the SSD.  Use **fsarchiver** and it will compress the image and let you restore to a smaller partition.

---

### Post by oldfred on 2018-08-16
recent Dell systems have needed UEFI updates & for NVMe SSDs firmware updates.
Even if systems from same order, you may have different versions of UEFI or SSD firmware.

       Dell XPS 8920 desktop GTX 1060, needed UEFI/BIOS update
[https://ubuntuforums.org/showthread.php?t=2370434](https://ubuntuforums.org/showthread.php?t=2370434)
Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[https://ubuntuforums.org/showthread.php?t=2360929](https://ubuntuforums.org/showthread.php?t=2360929)
Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)

---

