---
title: "Boot problem"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by chris0108 on 2011-01-10
Really strange problem, i have ubuntu 10.10 installed on a laptop and a desktop pc, the desktop boots fine every time no problem.
The laptop is very starnge, sometimes it boots straight away and another time it just boots to a black screen and nothing happens at all, or the screen goes black and the hard drive light just stays on. I have noticed its got worse since the last update, as an example today iv ended up booting into kernel 2.6.35-22 instead of 2.6.35-24 because 15 (yes 15) attemps to to boot into the latest kernel and black screen every time! On the old kernel it went straight in first time (this can be hit and miss too)

Has anyone else had anything the same?
Laptop is fairly old, its a samsung v20, intel pentium 4 processor, 512mb of ram and 250gig hard drive.

---

### Post by presence1960 on 2011-01-10
Well if the older kernel boots and the newer one does not you can try removing the newer kernel and then reinstalling it. I would boot into the older kernel, open Synaptic Package Manager and Mark For Complete Removal :

linux-image-2.6.35-24 & linux-headers-2.6.35-24

Mark them for Complete Removal whch will uninstall and remove them from cache in case the download was corrupted. Click Apply. Then try installing them again.

---

### Post by chris0108 on 2011-01-11
Thank you for that, i removed the headers etc done a reboot into the 22 kernels and all is fine, done another reboot into the 24 kernels and low and behold it has booted straight into it no problem! 

Thank you :D

---

### Post by presence1960 on 2011-01-11
You are welcome enjoy!

---

