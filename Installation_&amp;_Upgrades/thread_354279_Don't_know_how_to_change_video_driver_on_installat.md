---
title: "Don't know how to change video driver on installation"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by Billtg on 2007-02-05
I've been trying for a few days now to get 6.10 LiveCD to boot, but whenever I do I either get an error from X saying it can't configure my video card or something to that extent. After researching the forums a bit I found out I need to change one of the parameters in xorg.conf to "radeon" or "vesa" but I can't figure out how to get to this so I can change it. I've already tried replacing "quiet - splash" with "break = bottom" in the boot parameters, and then I try typing in "chroot /root nano etc/x11/xorg.conf" but it tells me nano doesn't exist. If someone can tell me how to go about this it would be much appreciated.
Currently trying with 6.10 AMD64-bit LiveCD, and I'm fairly certain this setting is the problem as I've seen some other people having the same problem.

Thanks

---

### Post by barefoot on 2007-02-05
What video card do you have?

I would recomennd just getting the alternative installer if you are having problems (my lcd backlight flickers or something in the live cd so i have to use alternative.)

---

