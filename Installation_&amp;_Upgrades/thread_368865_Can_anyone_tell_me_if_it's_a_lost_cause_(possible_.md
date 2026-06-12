---
title: "Can anyone tell me if it's a lost cause (possible hadware incompatibility)?"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by djrobthaman on 2007-02-23
Hi,

I've got a question about hardware compatibility, because I've been trying for ages to get ubuntu to install on my PC and it never has no matter how hard I try.  The problem generally is that the liveCD will boot to GRUB, but when I make the install selection I get a message like "Booting from Linux kernel... done" and then three lines of errors:

[32.11117] PCI: Cannot allocate resource region 2 of device 0000:01:00.0
[32.11157] PCI: Cannot allocate resource region 0 of device 0000:02:00.0
[32.11211] PCI: Cannot allocate resource region 2 of device 0000:01:00.1

The actual numbers on the left in the errors are never the same but are of the same type.

I've looked at the hardware compatibility page and I don't know if maybe I've found an incorrect page, but it doesn't seem like a very long list and I just want to make sure I get the final word as to whether the problem is hardware or me not doing something correctly.

Here are my stats:

Video:
ATI 100-714600 Radeon X1300 256MB DDR PCI Express x16 All-In-Wonder 2006 Edition Video Card

Memory:
G.SKILL Extreme Series 1GB 240-Pin DDR2 SDRAM DDR2 533 (PC2 4200) Desktop Memory Model F2-4200PHU1-1GBLA

Keyboard/Mouse:
IOGEAR GKM541R 2-Tone USB RF Wireless Standard Multimedia Keyboard/Mouse Combo

Motherboard:
Foxconn 925XE7AA-8EKRS2 LGA 775 Intel 925XE ATX Intel Motherboard

Hard Drives:
Seagate Barracuda 7200.10 (Perpendicular Recording) ST3320620A 320GB 7200 RPM IDE Ultra ATA100 Hard Drive (X2)

Western Digital Caviar SE WD2000JB 7200 RPM Ultra ATA100 200GB

Also a 100GB disk I salvaged from a Dell machine

CPU:
Intel Pentium 4 541 Prescott 3.2GHz LGA 775 Processor Model BX80547PG3200EK

Thanks a bunch,
Douglas

P.S.  I know I've made another post about this in another area of the forum, but it only recently occurred to me that it could be hardware and if that's the case no matter how hard I try my PC will never have ubuntu on it.  So, please don't kill me because I'm sounding repetitive.

---

### Post by bernied on 2007-02-23
Just a thought but if this is really important to you, you could try taking hardware out before you attempt the install. For example, you could remove two of the hard-drives (I can't say which is the best one to leave in).

Does the motherboard have integrated video? If yes, then you could pull the ATI card out and run the video from the MoBo.

Be warned that this will definitely cause you some pain later as you start putting the stuff back, and not just because it might be incompatible. Disk drives will change order, and therefore names will be wrong (/etc/fstab will need work, as will the bootloader grub).

Have you tried any other linux live-cd flavours in the machine? Any luck?

---

### Post by djrobthaman on 2007-02-23
I haven't put on a liveCd version... but I have gotten suse to work (every version since the last 9.x release)

No onboard video ( :'( )

I guess I could try taking out hard drives and such.  I'm just so upset because ubuntu works on my brother's crappy dell but not my machine which is pretty good.

Damn.

Thanks for the advice,
Douglas

---

### Post by bernied on 2007-02-23
There are other ways, but they are also messy. Have you considered trying an unstable/testing version - [Feisty](http://cdimage.ubuntu.com/releases/feisty/herd-4/)? Could also be scary - they're very open about the number of bugs still in it. Due for release in April.

It's not working on your machine because it is new hardware - support for new stuff takes time and the developers need to know that it's not working. Developers don't hang out here.

---

### Post by djrobthaman on 2007-02-24
K.  Thanks bernied.  

BTW, you wouldn't happen to know where I could send a request for hardware support would you?

Douglas

---

### Post by bernied on 2007-02-24
I don't know, but I'd guess you would want to be sure of which bit it was that wasn't working, before submitting any bug.

---

