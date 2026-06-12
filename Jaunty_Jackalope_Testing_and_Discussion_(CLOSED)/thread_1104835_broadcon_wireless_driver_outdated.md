---
title: "broadcon wireless driver outdated"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Myxb on 2009-03-24
Hi, all!

My dmesg says this:
[   13.327690] eth1: Broadcom BCM4328 802.11 Wireless Controller 5.10.27.11

I guess it means the driver version to be 5.10.27.11.

Well the Broadcom site has a new driver now: version  	5.10.79.10
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Who is responsible for including the driver into 9.04?

---

### Post by novafluxx on 2009-03-24
Hey the current one works, and I don't see a change log or anything, so why fix what ain't broken!

I use that same driver for my Dell Inspiron 1318, and Ubuntu is the only distro I've tried that includes it...

I'd not mind seeing it updated, but it works as it is (except for me not being able to connect to hidden networks)

---

### Post by Myxb on 2009-03-24
novafluxx,

Yes, it is generally a correct approach. However, a newer driver possibly may give better results. Just compare how wireless connects under Windows (might be NM matter though).

Current driver does not allow use of WICD, probably a bug but developers said problem *might* be the driver not supplying info on signal strength.

Surely I can compile it myself. It is better to have a newer driver, *generally*. However, it is much better to have in an official rep.

Just wondering who is the maintainer for the driver and how to get in touch with him/her.

---

### Post by lithorus on 2009-03-24
> **Myxb said:**
> novafluxx,

Yes, it is generally a correct approach. However, a newer driver possibly may give better results. Just compare how wireless connects under Windows (might be NM matter though).

Current driver does not allow use of WICD, probably a bug but developers said problem *might* be the driver not supplying info on signal strength.

Surely I can compile it myself. It is better to have a newer driver, *generally*. However, it is much better to have in an official rep.

Just wondering who is the maintainer for the driver and how to get in touch with him/her.

I would suggest you first compile it yourself and check if it solves your problem and that it otherwise works fine. Then you can report your results to the already filed bug report :
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/344763](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/344763)

---

