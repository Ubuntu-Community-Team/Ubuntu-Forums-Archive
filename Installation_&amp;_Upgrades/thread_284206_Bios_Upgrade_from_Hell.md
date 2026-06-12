---
title: "Bios Upgrade from Hell"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by acolic on 2006-10-25
Hi,

just upgraded the bios on my desktop. I had to replace the whole bios chip.

I followed the instructions correctly and i'm now getting the following errors:

1: the desktop refuses to boot from a floppy. The bios is set to boot from a floppy first, the floppy is a valid windows system disk and I see disk activity on start up but the system still boots into linux first.

2: while booting into linux, regardless if I use the recovery or standard kernel option I get a variety of errors. They are different all the time. Examples are:

Bad EIP value /sbin/modprobe
Kernel Panic not syncing VFS
Unable to lcoated RSDP invalid compressed format  (err=2)
Unable to mount root fs on unknown block (0,0)
Recovery mode USB 1-1: device not accepting address 4, error -110
Recovery mode USB 1-1: device not accepting address 5, error -110

The system seems to have problems near the loading hardware modules section of startup.

Any suggestions?

Thanks

---

### Post by Rhubarb on 2006-10-25
Sounds like you may still have a problem with your BIOS.
It could be something simple like a wrong setting - if the CPU / Bus is over-clocked you'll get these symptoms.

If you can get in far enough, try selecting memtest from the grub menu.

I'm convinced this is a hardware issue, could be your BIOS, memory, CPU, motherboard.

---

### Post by acolic on 2006-10-25
I did run memtest over night and it worked fine, there were no errors with the ram. 

Though when I started the bios it would go through a memory check and tell me that there was an error with my ram. I have got this error before I changed the bios chips so this is not new. Despite the error msg I never had an problems running Ubuntu.

So I am guessing that memtest is a better memory checking then the built in bios one.

I'll play around with the settings tonight.

Thanks

---

### Post by Rhubarb on 2006-10-25
> **acolic said:**
> So I am guessing that memtest is a better memory checking then the built in bios one.
memtest should be much more accurate than the simple ram check on startup.

Good, at least you know your RAM is ok (or should be ok anyway).

If you've got any PCI(e) cards that you don't need to boot up on, like sound / TV / network, then take those out.
I know my old soundblaster live 5.1 sound card caused all sorts of weird problems.

There's a very slim chance it could be your CPU, check to see what temperature it is running at in the BIOS, or check to see that there's good contact between the CPU and the heatsink - with heatsink compound.  I've even come across a few instances where there was tape over the heat transfer compound on the heatsink - making the CPU get very hot (and unstable).

---

### Post by acolic on 2006-10-30
Well I get the system booting up now but it is totally unstable. 

I must shut off the system using the shutdown icon or the system gets out of wack. If for example an application freezes and I have to shut off the system manually by using the power button the next time the system will not start up correctly. I have tried powering off and rebooting but that fails. It seems to freeze at the part where it load hardware drivers.

I have to unplug the power cable from the computer, wait 10 minutes and then plug it back in and it will run fine.

Not a good solution.

Alex

---

### Post by Rhubarb on 2006-10-31
Hmmm, that's not good at all.
It could be a power management problem (ACPI?), but I have very little experience with it.  I read somewhere on the forums here today that might fix up your problem:
[http://www.ubuntuforums.org/showthread.php?t=288669](http://www.ubuntuforums.org/showthread.php?t=288669)
The solution was posted on page 2.

Hope you get 'er up and running soon!

---

