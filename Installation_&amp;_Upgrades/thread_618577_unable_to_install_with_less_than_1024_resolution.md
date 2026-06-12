---
title: "unable to install with less than 1024 resolution?"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2007-11-20
I'm trying to install 7.10 (from LiveCD) onto a computer with an integrated Geforce MX video card.  Unfortunately, the default video driver only allows 640 or 800 resolutions, and I can't see the "Install" wizard buttons at 800x600?!

The workaround I came up with:
1. opened System > Administration > Restricted Drivers Manager
2. enabled the proprietary Nvidia driver
3. instead of rebooting (which wouldn't work with LiveCD?) I pressed CTRL-ALT-BACKSPACE to reload X.
4. The new driver immediately took effect and defaulted to 1024 resolution!

Larger issue:
Should the install wizard be usable at lower resolutions???

---

