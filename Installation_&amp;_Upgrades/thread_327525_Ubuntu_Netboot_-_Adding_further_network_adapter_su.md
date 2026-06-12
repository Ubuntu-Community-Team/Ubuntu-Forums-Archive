---
title: "Ubuntu Netboot - Adding further network adapter support"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by iamwu on 2006-12-29
We want to install Ubuntu onto the IBM x3550 which requires the bnx2 drivers.  These drivers are neither available in the 6.06 LTS or 6.10 netboot images.  The kernel used for these netboot images are:

- for 6.06 LTS is the 2.6.15-13-386 kernel and 
- for 6.10 is the 2.6.17-10-386 kernel.

Hence, I am looking for a way of including the bnx2 kernel module in the netboot initrd.gz.  I would expect that this module would either:

 - be built already and available through some other package which I have not yet found

or

- possible to build using the 2.6.15 kernel source using a specific kernel configuration file which I also have not yet found.

I would dearly appreciate any direction on this matter.

Many thanks in advance to whomever can shine light on this.

---

### Post by iamwu on 2006-12-29
I've done some further investigation and come up with the following link which I am currently investigating....:

[https://answers.launchpad.net/distros/ubuntu/+ticket/1969](https://answers.launchpad.net/distros/ubuntu/+ticket/1969)

- Will

---

