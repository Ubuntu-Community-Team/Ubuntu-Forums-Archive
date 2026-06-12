---
title: "Update destroy custom NVIDIA drivers"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by mediajunkie on 2008-07-03
Hi all,

I use version 8.04 / kernel  4.6.24-19 generic
installed the custom Nvidia driver (NVIDIA-Linux-x86-173.14.09-pkg1.run)

I had to add a modline in Xorg.conf to define the native resolution for my 16:9 40" LCD. Everything works fine then at 1360x768. 

However, as soon I run the upgrades available for Ubuntu, the next boot my display drivers are gone (back to the default 640x480 screen)  :(

Then I have to run the installation drivers from Nvidia and add my changes in xorg.conf again (well copy a backup of working xorg.conf) to accommodate the new modline for the 1366x768 resolution. 

once you know, not a huge job but still very annoying. 

Is there a way to prevent this? or is that just because the Nvidia driver is compiling into the kernel that will be overwritten every Linux update? 

thanks in advance for your help and advice.

Media Junkie

---

### Post by avtolle on 2008-07-03
The simple answer to your final question is "yes". As to preventing this, there was a thread on the Forum a bit ago that had a possible solution, and with regret, I didn't bookmark it so you will need to search.

---

### Post by mikewhatever on 2008-07-03
> Is there a way to prevent this? or is that just because the Nvidia driver is compiling into the kernel that will be overwritten every Linux update?

I think you'd have to recompile the driver after every kernel update. It's not that the new kernel overwrites it or the old kernel, you might try using the previous kernel to verify, but that's the solution I'm afraid. Hardy had lots of kernel updates since it's release, way way more then Gutsy. Hopefully they'll slow down.

---

