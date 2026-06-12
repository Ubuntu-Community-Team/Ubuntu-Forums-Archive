---
title: "Cant boot generic"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by Pnikosis on 2006-12-19
I posted this in the beginner forum, but maybe it's better to post it here  :-k  (sorry for posting this twice)

Hi, I updated my kubuntu installation from Dapper to Edgy. After that, I purged the old kernels (sudo aptitude purge linux-image-2.6.15-26-386...), and updated my Grub. The problem that I have now, is that I can only boot with the 386 kernel (I have an Athlon XP, so I want to boot with the generic one). When I try to boot with the generic kernel, I get an error message saying that it can't find the /lib/modules/2.6.17-10.generic/ folder.

Does anyone knows what could be the problem and how to resolve this? Should I be lazy and stick with the 386 kernel?

Thanks

---

### Post by spd106 on 2006-12-19
Shouldn't be a problem if you stick with 386, AFAIK the generic kernel is only there to make it easier for multi-core systems. If you want to switch back then you should be able to install the generic kernel through Synaptic. 

It's possible that some of the dependencies were upset, missed or removed during the upgrade process. I suggest that you double check that you have a fully updated system using the sticky guide in the install & upgrade forum page.

---

### Post by Pnikosis on 2006-12-19
I will check it, thanks!!

---

