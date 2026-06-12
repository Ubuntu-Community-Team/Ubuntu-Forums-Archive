---
title: "Ubuntu accesses router asap, BUT XP can't..."
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by UnCola on 2007-08-13
Hi I struggled through the hal.dll hell to get a dual boot set up...  and at once Ubuntu detects my router and connects to the net, even from the desktop CD without installing it.  Great stuff.

But for some reason XP (freshly reinstalled with updates SP2 etc) will not access the router, even if I type in its IP address. It will access the net via USB modem, though.

I realise this is a Ubuntu forum and this may be just an XP issue, but I am just wondering if anyone is aware of some aspect of Ubuntu install which could cause this?  Does the router have an issue with same machine accessing it with different OS?

Thanks for any comments.

PS I don't really like the idea of resetting router to factory settings, time consuming, been there and done that, but I'll do it if I have to.

---

### Post by 1/0 on 2007-08-13
Just a long shot but it sounds like an DHCP release issue. If the same MAC tries to get an IP, cheaper routers might have a problem with that. Have you tried static IP:s instead? 

What happens if you restart the router and maybe leave it for an hour with the computer off. Then try to access from XP and see if its that.

---

### Post by UnCola on 2007-08-14
Hi thanks for the suggestion, I did try it but no joy.  Reset to factory settings and installed router's drivers to XP from router's CD.  XP then accesses the router ok via wireless but not ethernet, Ubuntu still fine accessing router via ethernet.

Looking around on the net this seems to be a recurring XP prob: a fresh install having trouble accessing router and esp via ethernet, but not a Linux specific problem.

---

