---
title: "seed file not working"
date: 2016-02-15
forum: Installation &amp; Upgrades
---

### Post by darius-lewandowski on 2016-02-15
Hello
I am trying to install ubuntu with preseed file. 
I have 
d-i mirror/udeb/components multiselect main, restricted
d-i pkgsel/include string bcmwl-kernel-source cheese dkms fakeroot libfakeroot

but bcmwl-kernel wont install anyway. 

any ideas why?

-------
I've also tried in-target apt-get install bcmwl-kernel-source. 
Nothing happened

---

