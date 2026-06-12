---
title: "Installed Feisty, but have problems with VMware and Nvidia"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by Pollywoggy on 2007-04-24
I had both VMware and Nvidia working in Edgy, but after I upgraded to Feisty, I could not get VMware to work.  I was also unable to get Nvidia to work due to some missing file in the nvidia-glx package.  I Googled and found that the Nvidia problem is a known issue and not just in Ubuntu.  Apparently the kernel in Feisty is not compatible with VMware 5.x, so I am running a 2.6.17 kernel and I got VMware to work.

Is it possible to compile Nvidia drivers using deb-src from Edgy and use that in Feisty?  Is there a better way to get Nvidia working until the problem with VMware is resolved?  I had to change from Nvidia drivers to "nv" so I could use my Feisty system.

---

