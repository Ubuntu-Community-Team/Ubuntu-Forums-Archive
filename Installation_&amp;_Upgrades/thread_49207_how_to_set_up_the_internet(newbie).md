---
title: "how to set up the internet(newbie)"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by porsher_puddles on 2005-07-15
hi there i just installed ubuntu on an old computer its a celeron 667 on an old hp motherboard with 196mb ram. i was amazed how smoothly the install went, all seems well i have sound etc, i just get one fail message on boot, it says ROR temp fail in name resolution, i do not know what this means or if it is a problem?
My main trouble is i have no idea how to set up the internet, i have an internal modem for dial up (dodo). i am used to setting up windows but i can't work this out, would be greatfull if someone could talk me through it.
ty

---

### Post by varunus on 2005-07-15
Well, you can set up your modem from System->Administration->Networking if you're lucky...unless you have a "winmodem," in which case you'll need to get special drivers.  What modem do you have?

---

### Post by porsher_puddles on 2005-07-15
ok in devices it lists my modem as a sm56 pci modem, i do not know how to query the modem to check if it is functioning correctly, help with this would be appreciated.

how do you find system-administration-networking i can't seem to find it, along the top of the screen i have applications- computer-etc, where do i find them?

---

### Post by varunus on 2005-07-15
Applications and Computer?  It sounds like you're using Ubuntu Warty, not Ubuntu Hoary...I think for Warty its in Applications->System Tools->Administration, or maybe Applications->Preferences->System Administration or something like that.  I think you can get to it by opening a terminal and typing:
```
gksudo gnome-network-properties
``` 

You may want to post this over in the Warty forum if you're using Warty, or upgrade to Hoary (better support for hardware, bugfixes, etc).

---

