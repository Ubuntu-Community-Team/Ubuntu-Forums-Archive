---
title: "Boot an ISO contained in a LUKS container"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by Kip Ingram on 2012-07-09
Hi.  I routinely use a system that I boot to RAM.  I built it, and occasionally tune it, by booting the system from a portable hard drive, making any new changes I want, using Remastersys to create an ISO backup, and burning that to a USB stick.

I've applied some hacks I found elsewhere on the web to make the toram option work properly at boot time.  So once I boot the USB stick I then eject and remove it, and the whole shebang runs from RAM.

I use GitHub for persistent storage; whenever I feel like it I just git commit / git push and my changes are preserved.  On reboot I git pull.

I have this thing darn near perfect.  My only remaining desire is to encrypt the USB stick, so that if I lost it it my sensitive information would be secure (my iso is pre-logged into my Gmail, my Facebook, etc., and there is some initial content of the git repository on there too).

I think I need to attack this by putting the squashfs file into a LUKS container, or something like that, and then using a loopback to get that container used at the appropriate point.

I have found some instructions for this online and I will be trying that, but I thought I'd see if anyone else had any experience in this area.

Thanks!
Kip

---

### Post by Kip Ingram on 2012-07-09
I should add that I don't necessarily have to have the whole ISO in the LUKS container.  I only have to have encryption on filesystem.squashfs.

Thanks!
Kip

---

