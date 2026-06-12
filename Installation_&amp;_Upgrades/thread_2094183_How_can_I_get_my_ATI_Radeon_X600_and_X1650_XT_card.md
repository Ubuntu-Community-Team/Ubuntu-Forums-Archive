---
title: "How can I get my ATI Radeon X600 and X1650 XT card work on Ubuntu 9.04 and 12.04?"
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by towenyu on 2012-12-13
Hi,

  I'v been struggling for many days on getting my ATI Radeon X600 and X1650 XT card work on Ubuntu 9.04 and 12.04.
  I have two powerpc based board/system, one installed  Ubuntu 9.04, another with Ubuntu 12.04.
  
  Both system installed Xserver-xorg-video-ati, they are latest updated for their corresponding system. However, 

both system can not get those cards to work. Not even fall back to fbdev.

  When doing Xorg -configure, I noticed there's two related driver listed: ati, radeon.  With the default 

"radeon" as card driver ( means a line {Driver "radeon"} in the xorg.conf ), running Xorg fail. In the fail log, 

the driver listed a huge list of supported cards -- my two cards included --, but at last says " (EE) No device 

detected".
  I tried to use "ati" as card driver, but fail logs tells "No drivers available".

  Much appreciation if anyone can let me know what should I do. Or how can I roll back to an older driver?

Thanks in advance,
Wenyu

---

