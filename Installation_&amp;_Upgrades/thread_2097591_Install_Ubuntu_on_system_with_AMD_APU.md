---
title: "Install Ubuntu on system with AMD APU"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by zalpha314 on 2012-12-23
Hi there,

I have installed Ubuntu on a previous system many times, but the installation does not work on my _new_ system.  

When I insert the installation disc, I see a loading graphic, but after it disappears, my screen remains blank, and does not change.

I have also tried wubi.  The installation succeeds, but when I try to boot, I get the blank screen.

I believe the problem with my system is the AMD Vision APU combined with my Radeon GPU.  I know that Radeon cards do not support Ubuntu as well as Geforce cards, and since my system's GPU and chipset are both Radeon's they cannot display Ubuntu properly.

Does anyone have any ideas how this can be resolved/worked around?

I have included my dxdiag as a zip if anyone wants to see it.  There was a size limit for txt files.

Note that I attempted this several months ago, and am reporting the problem now since I will really be needing Linux on my laptop for my new job.

---

### Post by Bucky Ball on 2012-12-23
Boot to the LiveCD (not Wubi) and at the Try Ubuntu options, hit F6. This will give you a pop-up list of options to run with. Choose 'nomodset' and proceed.

What happened?

---

### Post by zalpha314 on 2012-12-29
Well, like I mentioned, the last time I tried, the screen goes completely blank, so there was no way I could have even seen the "try ubuntu" screen.

But anyway, I gave the latest version of Ubuntu a shot, and it loaded properly.  However, even after installing, I sometimes just get a blank screen after Ubuntu starts to load.  Restarting and trying again works most of the time.  This is something I can live with, but should I submit report a bug for this?

---

### Post by darkod on 2012-12-29
Actually from most threads on the forum, ubuntu works much better with Radeon than Nvidia. In most cases with Nvidia it doesn't even boot correctly, while with Radeon it should boot using the 'radeon' module by default. For 3D and better operation, you should install/activate the 'fglrx' driver. But it works by default with radeon too.

Maybe the combination of two cards confused it (one in the APU and one stand alone). You could have tried installing with only the APU and adding the second card later.

I recently upgraded to AMD A8-5600K and my 12.04 kept working without any problems. But the system was already installed, I just swapped motherboard+APU+memory. It booted right away the first time without needing to modify anything at all.

---

