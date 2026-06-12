---
title: "Last hope for help? unable to boot from cd"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by dxs on 2007-09-16
Ok, I'm very sorry if this is a dupe but I've checked quite a bit and nobody seems to be having this issue.

The problem is:  When booting an install of ubuntu (or any distro) I a change to select the install type and then hit enter.  I get 2 lines of text

Loading vmlinuz.......
Loading /install/initrd.gz......

Now, my issue is that my system will freeze while loading "dots" on 1 of these two lines.  It seems random which line it will be on any given attempt.  Then the sceen goes blank and the cd drive eventually powers down.  The system is now totally unresponsive and I have to use the reset button to power cycle it.

The system specs are:

DFI Infinity RS482 MB
AMD64 3000+ CPU (939)
2 Gigs (4 sticks) of Kingston Hyper (value) running in dual channel mode
Onboard ATI x200 express video
onboad nic (disabled in bios)
onboard audio (disabled in bios)

I have 1 ide hd at 160gig and 1 ide dvdrw drive, I also have a 400g sata drive but I have disabled all sata in the bios when trying to diagnose the problem.

I normally have this machine running windows vista media center without any problems.  Before that it was running windows xp media center 2k5 without any problems.  I'm not sure what the problem is and I seem to find other people on these boards using linux on this mb.  Does anyone have any ideas?

I have tried the following things:

noacpi noapic noapm irqpoll nosplash

and I have tried these in a number of combinations.

Please help, I'd love to move from vista mce to mythtv but I clearly can't do that without getting linux unstalled first

TIA!!!!

---

### Post by richardward101 on 2007-09-16
if it freezes at the dots then boot parameters probably won't help, as thats grub loading the kernel and asoociated bits into memory before it even boots the kernel. Try re-burning the cd, then post back if that doesn't help

---

### Post by Pumalite on 2007-09-16
This is your problem: Onboard ATI x200 express video
Try burning an Alternate CD. do md5sum, bur at 4x, check CD for corruption after burn and before install.

---

