---
title: "Installing Kubuntu 5.10 (BB) on SATA issues"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by timas on 2006-03-14
Hey folks,

Okey, I'm throwing my towel into the ring, I can't seem to find the right way to make it work, so I'ma ask on here to see if someone has some past experience with this..

I've got a fairly new Dell system, equiped with a single SATA drive on which I attempted to install Kubuntu 5.10 from the DVD, as you might have guessed from the post title, this aint working..

At first, I had a problem with the installer just simply stopping at somesuch like "Failed loading the installer components from CD".. Some googling later I found that my installer stopped with this as the last message in the debugger: "menu item load-cdrom failed"..

So, I google more, I find out a lot of people had trouble with bad CD's... I figure, sure, why not, lets burn the CD.. I download the ISO, burn it at the slowest possible speed, and reboot.

Again, no good. Exactly the same issue as before.. I google more, browse forums, mailing lists and try something with me manually inserting modules before the installer starts to load the drivers for my CD drive, I can happily insmod the modules, but it makes no difference. 

You guessed it, more google.. at this point I'm getting fairly frustrated.. then finally I wake up and take a look in my bios, I change my SATA settings from 'normal' to 'combined' which is described as the compatability mode for older OS'es.. again with the issues while installing.. but now I attempt another install with 'noapic nolapic' which it happily does.. right onto the part where I have to partition a drive.. I can't get past this part because there just aren't any drives in the installer.. I figure, lets try noapic and nolapic appart from each other.. noapic is a no go, same issue as above.. nolapic takes me to another issue, it appears to find my drive and continue on, but it makes a rukus about a shared IRQ for APIC and USB..

I would really like to get this to work.. I've considered waiting on Dapper Drake, but I'd prefer to just get it working now.. Does anyone have any past experience or ideas or perhaps a plain and simple list of steps to take to make it work?

thanks a ton in advance!
-Tim

---

