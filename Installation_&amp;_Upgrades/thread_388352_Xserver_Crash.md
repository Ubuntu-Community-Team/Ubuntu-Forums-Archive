---
title: "Xserver Crash"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by SOG420 on 2007-03-19
The message I get upon booting is "Failed to start the X server(....) Then something about Failed to load Nvidia module. I have installed and uninstalled ther appropriate driver for my nvidia 5200fx twice and both times the X server crashed. Tried reverting back to a previous release and nothing different happened. ANy advice would be apreciated.
Edgy

---

### Post by zvacet on 2007-03-19
[CODEsudo dpkg-reconfigure xserver-xorg][/CODE]
Instead of nvidia try with nv

---

### Post by r4ik on 2007-03-19
sudo dpkg-reconfigure xserver-xorg

replace as suggested.

When you have a visial get you're drivers here,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by SOG420 on 2007-03-19
Thanks for your help guys I got it working again.

---

