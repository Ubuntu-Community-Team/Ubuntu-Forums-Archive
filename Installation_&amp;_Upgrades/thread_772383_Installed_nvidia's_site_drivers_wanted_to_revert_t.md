---
title: "Installed nvidia's site drivers wanted to revert to restricted"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by vexorian on 2008-04-28
Before I upgrade I wanted to get rid of nvidia's site's driver, it really did not help me or improve performance or anything, it was a huge mistake to install it and the restricted driver was good enough.

So, I did "nvidia-install --uninstall" or a similar command line to get rid of it, the next thing I know is that x.org did not work anymore, I used links2 to find information and changed the driver in xorg.conf from "nvidia" to "nv"

So, now X works and nvidia's site's driver was uninstalled, the *only* problem is that I got no 3d acceleration. I tried re installing nvidia-glx-new which was the old driver I used, I also removed nvidia nv nvidia-new from the restricted manager exceptions file. How do I enable 3d acceleration again?

Edit: fixed.

If anyone is interested, here's what I did:
- I used synaptic to reinstal my kernel version's restrict modules package.
- I also used sudo nvidia-xconfig

I am not sure which of those things fixed the problem, it could also be that both were necessary.

---

