---
title: "*buntu 10.10 xorg and nvidia problem"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by dk_zero-cool on 2010-10-11
I have already created a post about this problem in launchpad but it might be useful to create one here to in case someone here has a solution.

I installed the new release from scratch using an image I downloaded to day. First problem was that xorg did not star because it could not find the driver. I started it manually and installed hoping an update or the propertary driver would fix it, but it didn't. I then found this small article ([http://rmic.be/ubuntu-maverick-nvidia-x-problem](http://rmic.be/ubuntu-maverick-nvidia-x-problem)) that seemed to have the solution. But it did not work. When I create an xorg file, xorg will not start at all.

The card is a nvidia gf8600m gt

If anyone have a solution it would be nice. I'm currently running 800x600 in resolution

---

### Post by dk_zero-cool on 2010-10-11
The problem is fixed.

Updated the 2.6.35.22 kernel to the 2.6.36.0 from the xorg-edgers repository. This resolved the issue.

---

### Post by mörgæs on 2010-10-11
Good. Please mark the thread 'solved'.

---

### Post by droetker on 2010-10-11
Bug is NOT fixed. see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658258](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658258)

---

### Post by jakell on 2010-10-11
I've gone back to 10.04 because of this issue. In fact, I may just stick with LTS releases for now.

 I moved from ATI cards to Nvidia because of ATI issues, and now Nvdia issues have emerged, I don't really regard this as 'upgrading', I'm seriously considering Debian for more stability.

---

### Post by droetker on 2010-10-11
really. I can't see why cards like nvidia and ati are not fully supported.
If it doesn't work with the new driver, then Ubuntu must wait with the new driver and use the old one until it gets stable.
That's what is called regression.

---

### Post by jakell on 2010-10-11
> **droetker said:**
> really. I can't see why cards like nvidia and ati are not fully supported.
If it doesn't work with the new driver, then Ubuntu must wait with the new driver and use the old one until it gets stable.
That's what is called regression.

The drivers are not the problem, it's the Ubuntu release.

To be fair, the Nvidia drivers are proprietary, so Ubuntu are not duty-bound to support them, but it would be nice if they did.

---

### Post by dk_zero-cool on 2010-10-11
> **jakell said:**
> The drivers are not the problem, it's the Ubuntu release.

To be fair, the Nvidia drivers are proprietary, so Ubuntu are not duty-bound to support them, but it would be nice if they did.

Its not just the closed driver. The open source driver acts out to, so the problem is possibly the xorg version in 10.10

What I don't get its that I manage to get one of them working some times, and then suddenly it just breaks down again.

Well, just got to play around with a live CD for a while and see if the solution merges.

---

