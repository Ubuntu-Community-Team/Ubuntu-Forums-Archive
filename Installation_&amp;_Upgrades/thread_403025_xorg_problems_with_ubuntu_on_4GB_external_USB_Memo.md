---
title: "xorg problems with ubuntu on 4GB external USB Memory Stick"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by phibuntu on 2007-04-06
Hello all

I finally managed to install an edgy on an external 4GByte USB memeory stick.
Everything works fine, except, when I plug the stick to a **different** hardware.
This is clear, because the installation of ubuntu checks for the graphics card (and other hardware) and configures the system for exactly this hardware. Thats what it did on my stick either.

So, when I plug the stick to a different hardware, linux boots well, but is not able to start the X-Server (I mentioned above why).

Question:
- Is there a generic xorg.conf, which can be run on most hardware?
Or
- Is there a script which can be loaded at boot time, to setup the xorg.conf file automated?

Every hint is wellcome.

---

### Post by phibuntu on 2007-05-03
I found a simle workaround:

simple delete the /etx/X11/xorg.conf

Now, the System tries itself to create something like a "good" X-Server.

Disatvantage:
 - Screen manipulations (moving, resizing, ...) are slow
 - Flickering occures
 - The resolution is default to 1600x1200 pixel. This can not be changed and some
   screens do not allow this. That means: On some PCs I am not able to boot my USB-Ubuntu.

Ideas? Hints?

---

