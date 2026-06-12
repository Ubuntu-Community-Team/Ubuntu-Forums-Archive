---
title: "How to downgrade xserver core?"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by cfm34user on 2007-12-27
Ive got a panasonic toughbook which has a Silicon Motion LynxEM video chip, its pretty low spec with a 400mhz P3 and maxed out at 192mb of ram. Ive replaced the HDD with 4gb of flash and am trying to build a minimal system from a CLI install of Gutsy.

Unfortunately the video driver seems to be broken in Gutsy (see [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-siliconmotion/+bug/136853](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-siliconmotion/+bug/136853) ). The fix on that page is to "Purposely downgrade xserver-xorg-core and anything that depend on it, then pining it to that version, while keeping all the rest of the packages to Gutsy versions". I dont know how to go about doing this - could anyone point me in the right direction?

---

