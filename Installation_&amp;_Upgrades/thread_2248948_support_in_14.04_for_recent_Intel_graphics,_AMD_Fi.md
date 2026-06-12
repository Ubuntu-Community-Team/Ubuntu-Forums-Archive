---
title: "support in 14.04 for recent Intel graphics, AMD FirePro M5100?"
date: 2014-10-18
forum: Installation &amp; Upgrades
---

### Post by joe-murray on 2014-10-18
I bought a Dell M4800 laptop with Intel Core i7-4940MX(Quad Core [Extreme]("member:Extreme") 3.10GHz, 4.0GHz Turbo, 8MB 57W, w/HD Graphics 4600) and AMD FirePro M5100 w/2GB GDDR5 preinstalled with Ubuntu 12.04. I'm having someone try to upgrade it to 14.04, but it fails due to a graphics not supported error. Does 14.04 should support both the built-in Intel graphics and the AMD graphics card?

---

### Post by ajgreeny on 2014-10-18
I'm pretty sure the Intel graphics are fully supported, but I wonder if this is a hybrid graphics setup, that in Windows would switch from Intel to AMD when needed.

Hybrid graphics using intel/nvidia are getting better support now with bumblebee but as far as I'm aware at the moment there is no similar way of dealing with intel/AMD graphics.

Other forum users may know more than me, so wait for other comments, and hopefully something that may help you more directly.

---

### Post by johnathanamber on 2014-12-29
I know that back in the early days of Intel/Nvidia combinations, we could disable the discrete graphics adapter and leave the Intel one running. I am wondering if we can do the same here.

I am considering installing Ubuntu 14.10 on my Dell Precision M6800 Mobile Workstation. There are REH drivers available here:
[http://downloads.dell.com/FOLDER02253072M/1/fglrx64_p_i_c-12.104.2-1.x86_64.rpm.tar.gz](http://downloads.dell.com/FOLDER02253072M/1/fglrx64_p_i_c-12.104.2-1.x86_64.rpm.tar.gz)

I wonder if anyone more knowledgeable would be able to part this out to get drivers working for the AMD FirePro family for Ubuntu and other variants.

---

