---
title: "Remove framebuffer module"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by juanhm on 2006-02-21
As I stated in another thread, after upgrading to "linux-image-2.6.12-10-k7" X dind´t start due to problems with the nvidia module form "nvidia-glx".

I got to the solution based on removing the conflicting "nvidiafb" module before starting gdm, just by editing the gdm script in /etc/init.d and adding the line "modprobe -r nvidiafb" at the beginnig.

However, I would like to find a cleaner way to solve the problem not by editing the script. ¿Does anybody know why is the nvidiafb module loaded at startup?¿Is it loaded only after upgrading the kernel (as I had no problem before upgrading) or it was loaded always but with a different version compatible with nvidia?¿How can i remove this module (if possible) in a cleaner way?

I also tried removig the "splash" option included in grub.conf for the kernel image, but the module nvidifb was still present and the console became unstable.

---

