---
title: "STEAM INSTALLATION ERROR | Unbuntu 14.04"
date: 2015-10-19
forum: Installation &amp; Upgrades
---

### Post by joshnorman2467 on 2015-10-19
Hello,

I am new to linux and no nothing about anything :)
I tried to install steam on Ubuntu 14.04 and it kept giving me errors...

This is what the Terminal looked like...
------------------------------------------------------------------------

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.5)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
----------------------------------------------------------------------------------------------------------------------------------------------------

Then I pressed enter and it said this

You are missing the following 32-bit libraries, and Steam may not run:
libGL.so.1
---------------------------------------------------------------------------------------------------


Please help!!!:o

---

### Post by joshnorman2467 on 2015-10-20
I fixed it! You just type this into the Terminal

[COLOR=#111111][FONT=Consolas]sudo apt-get install libc6:i386 libgl1-mesa-dri-lts-vivid:i386 libgl1-mesa-glx-lts-vivid:i386[/FONT][/COLOR]

---

