---
title: "Installing 10.04 Server on a working 10.04 Workstation?"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by jdholman on 2010-05-21
Hi There:

I have a 64 bit Dell laptop happily running 10.04 32-bit and Windows 7 booting with GRUB.  I want to also install Lucid server on a spare 20GB empty partition and I would like to have Lucid server available in the GRUB menu along with Lucid 10.04 and Windows 7.

I don't want to blow away what I already have working and last time I booted from the server CD to try to install it (9.10), it didn't look as easy as when I installed workstation.

Will an install of Lucid server gracefully and safely allow itself to be put on a spare partition and install itself in GRUB or so I need to do this manually?  If I lose my Lucid workstation install, I am in trouble.

Thoughts?

Jim

---

### Post by darkod on 2010-05-21
While I have never tried it, it should allow you to install where ever you choose. Only don't install grub2, not from the server, because you're already running grub2. After the server is installed you will just need to boot your desktop version and do:

sudo update-grub

The thing you will have to be slightly careful about is that the server has a text based installer, unlike the desktop version (which you probably noticed :) )
But as long as you pay attention, it should be fine.

---

### Post by jdholman on 2010-05-21
Thanks.

I saw that installer.  It game me pause for sure after the very nice looking and easy to understand graphical installed of Lucid workstation.

I may just try to install server and skip grub.  Presumably when I reboot, Server won't be in the Grub menu, but this could be added by the sudo update grub command you mention.

Sound ok?

---

### Post by darkod on 2010-05-21
> **jdholman said:**
> 

I may just try to install server and skip grub.  Presumably when I reboot, Server won't be in the Grub menu, but this could be added by the sudo update grub command you mention.


Yes, that was the point. For any linux install you don't need it to install grub if you already have one. Just keep using the grub you are used to. OK, in this case they would be the same, grub2, but why mess with it...

---

