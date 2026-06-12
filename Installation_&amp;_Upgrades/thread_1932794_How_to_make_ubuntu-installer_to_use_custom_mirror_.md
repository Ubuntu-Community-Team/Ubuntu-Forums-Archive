---
title: "How to make ubuntu-installer to use custom mirror with different dist name."
date: 2012-02-28
forum: Installation &amp; Upgrades
---

### Post by kmkswamy on 2012-02-28
Hi,

I have created a new mirror based on packages from oneiric upstream.

Now when doing a pxe boot and giving the url to the custom repository is failing with an error in mirror message.

Error:
it seems like ubuntu-installer is trying yo check as 
[http://xx.xxx.xxx.xx/](http://xx.xxx.xxx.xx/) //dists/oneiric -O | grep .....

here i see that the installer is looking for oneiric directly which i dont have. i have something as //dists/custom-dist

How can i make u-installer to take that into consideration, do i need to tweak the u-installer? if yes where should i do it as i am not able to find the source location where it is written.

Any pointers?

Thx

---

