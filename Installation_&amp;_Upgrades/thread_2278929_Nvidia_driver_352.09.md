---
title: "Nvidia driver 352.09"
date: 2015-05-19
forum: Installation &amp; Upgrades
---

### Post by odror on 2015-05-19
Hi 

I am looking for a ppa for nvidia version 352.09. The linux driver was release on 5/18 on the nvidia site. It is already the default for Archlinux. Does anyone knows when this ppa will be available for ubuntu. It is labeled as beta on the nvidia site.

I need this specific version because my lxc container is running arch with the 352.09 version. I am not able to downgrade it to the 349.16. I need to match both versions so that the nvidia driver will work in the container.

---

### Post by dino99 on 2015-05-20
not yet published on launchpad ppa (xorg-edgers, mamarley)

---

### Post by JMB74 on 2015-05-20
Now here.

[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

---

### Post by dino99 on 2015-05-20
finally landed in vivid archive  

> nvidia-graphics-drivers-352 (352.09-100ubuntu100~ppa0~vivid0) vivid; urgency=medium

  * New upstream release.

 -- Michael Marley <email address hidden>  Wed, 20 May 2015 05:27:47 -0400

---

