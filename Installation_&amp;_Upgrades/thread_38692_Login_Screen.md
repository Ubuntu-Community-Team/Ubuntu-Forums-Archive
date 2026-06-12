---
title: "Login Screen"
date: 2005-06-01
forum: Installation &amp; Upgrades
---

### Post by Dasch on 2005-06-01
After a new install the login screen is blurred,unreadable. The login sound works and the install went ok. I checked the iso image with md5sum before, ok. My system is Asus K8v Deluxe,AMD64 3000+,ATI Radeon 9200. Thank you in advance for any help.

---

### Post by mingus on 2005-06-01
That's the mobo, not the system.  Is this a laptop?

When you boot, try adding this argument to the kernel line:
vga=normal
this will put you into 800x600 or lower resolution, and disable the framebuffer.  If this works, you can then work on getting your X-server configuration corrected.

---

### Post by mingus on 2005-06-01
Oops, sorry.  Of course this isn't a laptop.  I engaged fingers before brain.

Still, try the kernel argument.

Since you've got an Athlon64 and are using a different kernel, you might want to post on that sub-forum.

--mingus

---

### Post by Dasch on 2005-06-01
Thx for your reply. Am I pressing "e" at boot, then add this line? Please excuse my newbieness. Thank you.

Ok, I added vga=normal to the kernel /boot line. Still no difference.

---

### Post by mingus on 2005-06-01
Your problem sounds like it is in either the X-server or how the hardware is interacting with the kernel.  Try a post on the 64 forum, or maybe the IRC channel.

---

### Post by Dasch on 2005-06-01
I not trying to install the 64 bit version of Ubuntu.

---

### Post by mingus on 2005-06-01
You should also research the driver for your specific ATI card.  Some drivers are in the kernel, others not.  I seem to remember that there is also more than 1 driver available for newer ATI cards.

If you have the correct driver, then the issue will probably be in either the X-server configuration, or with hardware compatibility or detection.

---

