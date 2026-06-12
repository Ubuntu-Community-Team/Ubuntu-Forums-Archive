---
title: "Problems with atheros and intel 4500"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Ub1476 on 2008-10-02
Just installed Intrepid beta. I'm welcomed by a 1024x768 screen, so I go and open the Screen Resolution app to fix it. The app think I have 3 screens, every one is mirroring each other. So I set those two others (non-existing) to off, and set my screen to 1280x800. It sets the correct resolution, but the area which was "extended" gets lots of ugly artifacts. Mostly black with a few colors here and there.

Second is wireless. Atheros is supposed to have released free drivers for .27, and it seems right. Hardware Drivers tells me that the drivers are in use and is tested by the Ubuntu devs. Networkmanager does however not detect any signals.

My laptop is a Thinkpad X200, with Intel Centrino 2 P8400, Intel GMA X4500 and an atheros wireless card. Does anyone experience the same problems?

---

### Post by danbuter on 2008-10-02
PLEASE file a bug report. The main reason I'm not using Hardy on my laptop is because Atheros and Hardy do not mix.

---

### Post by plun on 2008-10-02
Master bug and a bunch of duplicates

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259157](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259157)

Also discussed within this forum. So please search this forum

A new kernel is coming, unclear when.

Wicd seems to be one solution.

---

### Post by Ub1476 on 2008-10-03
Replied to already filled bugs now. Will the new kernel fix the atheros problem? I didn't see a fix commited..

[Intel 4500 bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/273899")

---

### Post by plun on 2008-10-03
> **Ub1476 said:**
> Replied to already filled bugs now. Will the new kernel fix the atheros problem? I didn't see a fix commited..

[Intel 4500 bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/273899")

I don't know and the changelog is a bit unclear

> ath9k: Fix IRQ nobody cared issue with ath9k


Maybe also this
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274748](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274748)

Hope for the best...:)

---

