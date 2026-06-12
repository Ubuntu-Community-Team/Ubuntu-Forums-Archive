---
title: "can't install ubuntu on new system"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by lime4x4 on 2007-04-04
I've tried installing 6.06,6.10 and feisty.I get to the ubuntu screen with the knight rider lite bar then a black screen and 1 min later my computer locks up.I can load xp just fine thou.
my system consists of the following
p5n32-e sli mainboard with a 680i chipset
dual nvidia pci-e 7600gt vid cards in sli mode
2 gigs of ram
intel core 2 dou
sata dvd drive
usb drive
and 4 320 gig sata2 drives

Any ideas?

---

### Post by lime4x4 on 2007-04-04
got it sorted out.It seems ubuntu doesn't like cing 2 pci-e vid cards installed.First i thought it was cause there were linked (sli). So i removed the connecting bridge and still wouldn't boot.So i removed 1 of the vid cards and ubuntu booted up and installed just fine.Everything was detected also including the nvidia twin lans.So then i shut down the pc and installed the 2nd pci-e vid card in sli mode and ubuntu booted up to the desktop with no hassle or errors

---

### Post by phidia on 2007-04-04
Hey good work! I've been curious about SLI, probably won't go that way but what are the frame rates?  Post the results of glxgears -printfps if you don't mind.

---

