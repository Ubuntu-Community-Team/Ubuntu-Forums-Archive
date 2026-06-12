---
title: "Cannot install support for compiling some X11 libs on 32bit + 64 bit"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by outofsync on 2012-10-22
Hi,

In Maverick Meerkat (64 bit version) I successfully installed everything I needed for compiling for both 32bit and 64bit targets.

I'm almost there with Precise Pangolin, but there's a place where it fails: The "libxt-dev" and the "libxt-dev:i386" packages are incompatible, so I cannot install both at the same time. The same happens with  "libxp-dev" and "libxp-dev:i386".

These two are the only libs that I cannot install with 32bit + 64bit support. The rest of libs I needed worked fine (maybe there're more libs with this issue, but they don't affect me).

Is there any workaround for this? How can I proceed?

TIA

---

### Post by outofsync on 2012-10-22
After searching a bit, I didn't find anybody talking about this issue, but however I found that it seems to be possible to install packages without uninstalling the other packages they wish to uninstall (I've read this is accomplished with "sudo apt-get download ..." and then "sudo dpkg -i ...").

I guess this would allow me to have both "libxt-dev" and "libxt-dev:i386" installed (and "libxp-dev" and "libxp-dev:i386").

Should I do this, or can it be dangerous in some way?

---

