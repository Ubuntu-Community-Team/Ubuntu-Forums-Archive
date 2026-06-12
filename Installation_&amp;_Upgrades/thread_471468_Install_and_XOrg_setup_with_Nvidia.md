---
title: "Install and XOrg setup with Nvidia"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by austin.lund on 2007-06-12
I have a clunky install with nvidia GeForce 6150.  

I am unable to get to my screen resolutions using the generated xorg.conf from the install.  So to use the EDID info, I need to run "apt-get reconfigure xserver-xorg" which is ok, but not great.  

Anyway, after doing this and getting my full range of available monitor resolutions, my cursor disappeared.  

So I put an Option "SWCursor" "true" line in the xorg.conf.  

What is going to happen with newer versions.  Isn't there a better way to set the Xorg settings than "{vi | nano | gedit } /etc/X11/xorg.conf"?

Why do I have to set the SWCursor option with the "nv" driver?

---

