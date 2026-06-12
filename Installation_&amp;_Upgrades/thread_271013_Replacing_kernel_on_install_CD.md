---
title: "Replacing kernel on install CD"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by rowol on 2006-10-04
Hi,

I have a Shuttle SS30G2 which has an onboard RAID controller (Sis966L, i.e. 1184) that is not supported by the kernel included with Ubuntu 6.06.1.  I believe this controller is supported in the 2.6.18 kernel as well as some of the later 2.6.17 kernels.    

Would it be feasible to make a new install CD from Ubuntu's ISO where I replace the included kernel w/ a new 2.6.18 kernel that I build from source.... or would this totally break the installation?      If it might work, what other parts of the install CD would I also need to change (i.e. modules, etc) and what would be the procedure for doing this?

Thanks,
Ross

---

### Post by orb9220 on 2006-10-04
Edgy is 2.6.17-10 at the moment. 2.6.18 will be in edgy+1 in feb 2007.

If I was forced to give an answer it would be yes it would break dapper. 

Why don't you just download edgy and give it a try. Just had 108 updates so they are working fast and furious for stable release on the 26th. 

But appears pretty stable now on my system. Have nvidia new beta drivers with beryl running pretty smooth on this older system. 

Hope someone with an exact answer to the kernel breaking dapper or not will post here.

---

### Post by rowol on 2006-10-04
Orb9220,

I've been using Linux for a while, but I'm fairly new to Ubuntu and did not realize a Beta of the next release (Edgy Eft) was available.   Thanks for pointing that out, I will give it a try!

I did try the Knoppix live CD last night, which has a 2.17 kernel on it, but I'm not sure which subversion...   it didn't recognize the controller either, so I might actually have to use 2.18 or patch 2.17 to get it to work.

It would be useful to know how to replace the kernel on a dist CD though, as I see the problem happening more and more in the future, and that's a somewhat easy fix for ppl that have the capability to build a custom kernel and edit ISOs....   easy if it doesn't break a lot of other stuff anyway.

If Edgy doesn't work (and I can't find anything else with a 2.18 kernel), I'm guessing my other option is to make my own "roll your own distro" based off Debian and install enough stuff to get apt-get to work.... not really the way I was hoping to go.

Ross

---

### Post by rowol on 2006-10-05
Orb9220,

Thanks for the suggestion... but using Edgy Eft didn't solve the problem.    That kernel worked better in that it actually supports the onboard ethernet controller, but it still doesn't have the updated driver that supports to newer onboard RAID controller.

Any other suggestions for an easy way to get things working?   (I originally posted this question in one of the h/w forums trying to figure out if patching the driver and trying to modprobe it during the install was feasible, but didn't get any replies.)

Thanks,
Ross

---

### Post by rowol on 2006-10-23
I got this to work by remastering some drivers on the install CD.   

See post [http://www.ubuntuforums.org/showthread.php?p=1651238](http://www.ubuntuforums.org/showthread.php?p=1651238)

---

