---
title: "Envy and Hardy Upgrade"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by ph1 on 2008-04-28
So, being a little too excited to upgrade, I just went ahead and moved from 7.10 to 8.04 without uninstalling Alberto Milone's envy script first (which I know he specifically reminds you to do).  

Now Ubuntu starts in low-graphics mode, and it doesn't properly detect my screen resolution.  I've managed to use the legacy drivers (nvidia-glx) to fix the resolution, but I can't seem to enable desktop effects using them (and life without viewport switcher and wobbly windows makes me sad).  

If I try to reconfigure xorg, using dpkg or using the nvidia utility nvidia-xorgconf, it seems to work, and then when I reboot it's back to where I started, asking me to select between two ridiculously low screen resolutions.  Also, the driver sometimes appears under the Hardware Drivers section, marked as Not in Use, and sometimes does not appear for me to even enable, when by my resolution it clearly is.  

I've tried removing the drivers with envy and reinstalling, same with envyng, removing envyng and nvidia-glx-new reinstalling, and adding lines to xorg.conf.  

Does anyone have any advice on how to avoid a complete reinstall and somehow get the new nvidia driver working and detected again?  

Many thanks in advance.

---

