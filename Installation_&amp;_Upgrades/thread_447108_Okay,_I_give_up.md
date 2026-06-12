---
title: "Okay, I give up"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by SixStringSW on 2007-05-17
I have an old AMD K6/550 box with an ATI Mach 64 graphics card and Linksys LNE-TX100 network card, 40gb HDD, 384mb RAM.  Thought it might make a decent file server for my home network (3 PCs and a Mac).

Apparently Linux doesn't know what to do with this system.  I've tried:

Ubuntu server: installed fine (but couldn't find the NIC) but keeps rebooting during GRUB load.  I tried re-partitioning manually, but to no avail.

Xubuntu: locks up during install, saying it can't load a screen.

Kubuntu: Goes into some graphics mode during install, despite having told me it couldn't start Gnome.  Screen is locked in text, CPU seems to think it's in graphics, can't do anything.

Debian:  Installed fine (except for not finding the NIC), gets past GRUB, says it's "loading Kernel," goes away on vacation and doesn't even write.

Windows sucks, but it doesn't suck this bad.

---

### Post by IgnorantGuru on 2007-05-17
Have you tried the alternate install CD for Kubuntu/Ubuntu?  That would be my next step.

---

### Post by starcraft.man on 2007-05-17
> **IgnorantGuru said:**
> Have you tried the alternate install CD for Kubuntu/Ubuntu?  That would be my next step.

I concur with ignorant, try the alternate CD of Ubuntu. However, with your low specs you may even want to go for alternate Xubuntu... 384 mb of ram is really low today >.>. Ubuntu's bare minimum spec is 256.

As for Ubuntu sucking, I'm afraid thats not the case... it merely seems to me you've had bad luck in your early efforts to get linux working and now blame the software when you lose patience. Anyway, do as you like, were about choice and your free to choose to stay with MS.

---

### Post by scrooge_74 on 2007-05-17
> **SixStringSW said:**
> I have an old AMD K6/550 box with an ATI Mach 64 graphics card and Linksys LNE-TX100 network card, 40gb HDD, 384mb RAM.  Thought it might make a decent file server for my home network (3 PCs and a Mac).

Apparently Linux doesn't know what to do with this system.  I've tried:

Ubuntu server: installed fine (but couldn't find the NIC) but keeps rebooting during GRUB load.  I tried re-partitioning manually, but to no avail.

Xubuntu: locks up during install, saying it can't load a screen.

Kubuntu: Goes into some graphics mode during install, despite having told me it couldn't start Gnome.  Screen is locked in text, CPU seems to think it's in graphics, can't do anything.

Debian:  Installed fine (except for not finding the NIC), gets past GRUB, says it's "loading Kernel," goes away on vacation and doesn't even write.

Windows sucks, but it doesn't suck this bad.

Does it loads from the Live CD?

If all fails you could try either Knopix to see if it boots ok or use either DSL or Puppy linux to at least get it to work and go from there.

---

### Post by jerrylamos on 2007-05-17
For whatever reason, my K6 was pretty slow.  Too slow.  "The Official Ubuntu Book" mentions an alternate kernel for K7, but not K6.  I've got a 1 GHZ Pentium which is nice and fast and crisp with Ubuntu, and was fine at 384 MB, is now at 512 MB which was a cheap add.  This is a 1.2 GHZ Celeron and is great for testing Ubuntu Alpha's and Beta's.

Cheers, Jerry

---

