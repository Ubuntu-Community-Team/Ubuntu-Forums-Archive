---
title: "x201 black screen on bootup with 10.04 RC"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by xnstz on 2010-04-27
Pretty much what the title says.. a few more details:

- I installed 10.04 using the alternative install so I've been doing all this in safe mode
- I installed a newer kernel (2.6.33) and still black screen
- I tried to install an updated Intel xorg driver, but I kept getting dependency errors (xorg, x11, something else)

Can someone help me?  I read another thread on this forum from a user who is using the same platform (Intel HM55), and I got stuck at the last point (can't get Intel xorg driver to install).

---

### Post by xnstz on 2010-04-28
Anyone?

---

### Post by Agnaramasi on 2010-04-28
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569)
The suggestion in #8 worked for me with 10.04 RC on my X201.

---

### Post by xnstz on 2010-04-28
Wow that fixed it!  Thanks!

---

### Post by pIII on 2010-05-21
> **xnstz said:**
> Wow that fixed it!  Thanks!

yea, is sort of a "fix" cause we still don't have full support.

now, im wondering if any of the kernels of this PPA will do better on our particular video card:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D)

has anyone tried with a recent kernel from there?

---

