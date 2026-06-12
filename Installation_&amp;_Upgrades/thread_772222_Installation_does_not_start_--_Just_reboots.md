---
title: "Installation does not start -- Just reboots"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by k.pekka on 2008-04-28
So I did a upgrade with apt from 7.10 to 8.04 (64 bit). Everything went okay until I rebooted and was about to boot into 8.04. It boots into Busybox (?). Same with recovery mode. This is with 2.6.24-16-generic. I can boot into 8.04 with 2.6.22-14-generic but there the graphics are screwed.

So I thought I'd just download the .iso (8.04 64 bit), and do a clean install. But the install does not start after i've pressed "Install ubuntu". It loads the kernel. Shows the ubuntu-logo for about a half a second and then just reboots.

I've searched for others with same problems but I have not really found any help.

My system:
AMD 64 bit x2 +6000
NVIDIA GeForce 8600 GT
250 GB SATA drive
2 GB RAM

Any ideas?

---

### Post by k.pekka on 2008-05-06
So i've installed 7.10 now. I had the same problems with 7.10 before but now I read somewhere I should add "pci=nomsi" to the install options.  And that way I got the install to start. BUT this does not work for 8.04. So still stuck.

I can probably do an upgrade from 7.10 to 8.04 when i'm done with the upgrades for 7.10 (upgrading right now) - but that's what I did before and nothing seemed to go right then, so what I want to do is to get the install-cd to work so I can do a clean install.

And BTW I tried the Debian netinstall CD (4.0 R3) and same there as with 7.10. It works with pci=nomsi.

So if someone just wants to explain what "pci=nomsi" does - that would be good reading too. I'm not what one would call an expert at these kind of things :)

---

### Post by k.pekka on 2008-11-03
Hi, back with the same problem again. And this time I tried with Fedora 8. Fedora 8 Live, CDs, DVD,s USB.. same everywhere.

Oh and I still have the same system:
AMD 64 bit x2 +6000
NVIDIA GeForce 8600 GT
250 GB SATA drive
2 GB RAM

---

