---
title: "PCI to USB?  Not Doing As Expected"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2009-11-14
I've a PCI to USB (5 port) card in my machine, and I am running Ubuntu 9.04 as host with VirtualBox and clients of both Windows 2K and XP.  Most things look and act normal, but every time I launch Windows 2K, it sees a new device which it just identifies as PCI, and the driver it has for that is a mismatch.  At the same time, Ubuntu as host doesn't seem to see or recognize the PCI card.  What's odd about that, is that I can understand maybe that it might not recognize the card installed, but it's my understanding that the protected environment provided by VirtualBox, whqt some call a sandbox, is letting evidence of the card's existence slip through to the client.  Seems odd.

I figure there ought to be some sore of an answer for this, only I don't have it.  Ideally, Ubuntu should recognize the card and add this as another USB controller.  Then VirtualBox should let any attached device be passed to the client as the settings direct.  But while we are to the point where Win2K identifies the presence of the card, maybe I should try finding a suitable Windows driver and seeing if it can activate on that side.   Trouble is, I'm not quite sure what the brand or model of the PCI/USB card is.

I thought that by putting this out there, I might pick up some good ides from others, and it would be worth the sharing.  You know, it's been promised that USB 3.0 will come on the scene sooner or later, and the way to add that to existing PCs will probably be via the PCI slots.  USB 3.0 will be quite a bit faster than 2.0, and finally let some speedy drives get to their max when attached by USB.

---

