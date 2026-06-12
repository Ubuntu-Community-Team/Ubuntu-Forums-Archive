---
title: "The installation wouldn't proceed (with any distro with the latest kernel)"
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by Julita on 2010-04-20
Hello everyone! I have a laptop Asus eeepc 1001ha with Intel chipset. Any kernel after 9.04 wouldn't load. The tweak with parameters in a boot line (e.g., nomodeset) wouldn't help. Not a single distro would work, except the earlier versions, which is weird because the laptop was launched at the end of 2009. Thank God I haven't removed my Windows partition. By the way, I am the only one with such problems with this particular laptop which is weird; the hardware is OK. I can't figure out what is wrong. I have just tried Lucid Lynx, and, just like previous times, the installation wouldn't go further than the logo (after I press "install") Alternate CDs wouldn't load as well. Suse, Fedora wouldn't load as well. Checked with different USB flashes, using different programs. Any help would be greatly appreciated. Now I am thinking about switching again to BSD, but there might be some hardware compatibility issues.

I don't want to use 9.04 since there are some performance issues. "nomodeset" worked for me for Xubuntu 9.10, but the overall performance was also very poor, and I had to download the early release because of the kernel.

Another issue is my videocard's driver (intel); I checked: when I decided to try the later versions, the screen would freeze; I had to roll back to the previous ones.

---

### Post by dabl on 2010-04-20
If you are the only EeePC 1001 owner having this problem, then it is apparently some issue with your hardware.  Have you run a diagnostic test on your hard drive and/or memory?

---

### Post by Julita on 2010-04-20
> **dabl said:**
> If you are the only EeePC 1001 owner having this problem, then it is apparently some issue with your hardware.  Have you run a diagnostic test on your hard drive and/or memory?

Windows works like a clock, so there is no need for it. Besides, earlier kernel versions work, albeit not very smoothly.

---

### Post by dabl on 2010-04-20
I don't know the 1001 model, but I have an EeePC 4G/701, which runs sidux Xfce very well -- I think the kernel is a 2.6.30 or 2.6.31 (I'm away from it at the moment).  The idea that a new modern kernel won't run on that PC does not sound right -- maybe it is just a video framebuffer issue or something like that?

Have you tried it with a boot option like vga=785?

Also, I would think the UNR version would be a good choice, if you don't mind the appearance of it, as per this: [http://www.linux-netbook.com/video/installing-ubuntu-netbook-remix-on-asus-eee-pc-1001ha](http://www.linux-netbook.com/video/installing-ubuntu-netbook-remix-on-asus-eee-pc-1001ha)


Here's some information, if you haven't seen it already:  [http://forum.eeeuser.com/viewtopic.php?id=81183](http://forum.eeeuser.com/viewtopic.php?id=81183)

---

### Post by Julita on 2010-04-21
Thanks, but I was using both desktop and UNR. By the way, 9.04 UNR runs flawlessly, and I have used it since I have bought the laptop until now. I know it sounds weird, but the problem (now I am sure of it) lies in the updated driver for my videocard, and I have heard a lot of people complaining about Intel's poor graphic performance with the latest versions of driver.

---

