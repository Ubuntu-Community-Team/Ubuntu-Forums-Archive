---
title: "Loading Ubuntu queery"
date: 2005-11-05
forum: Installation &amp; Upgrades
---

### Post by AllanP on 2005-11-05
I had Breezy on the system sharing a 160GB disk with Windows XP. I had a problem with Windows. Tried using Acronis True Image for a restore. Everything was corrupt. Then I realized that MBR was changed by Grub. What a mess. Got out of it by formatting and recreating C: and loading image. Now I want to reload Ubuntu Breezy. Is there a way of doing it where I don't mess with MBR and still load Grub? On a floppy? I have a second 120GB disk so space isn't the problem. Actually I think I'll put it on the second disk next time. I also have another old 40GB disk I could connect for breezy. Just looking for some good advice from you whiz's out there.:confused: 

Thanks, Allan

---

### Post by aysiu on 2005-11-05
So you want Windows to be on the MBR? If so, why? And, if so... it's not easy to do a dual-boot, then. This may help:

[http://www.littlewhitedog.com/content-52.html](http://www.littlewhitedog.com/content-52.html)

If you want Ubuntu's Grub to be on the MBR, just put it there during the install process, and it'll add Windows to the boot menu.

---

