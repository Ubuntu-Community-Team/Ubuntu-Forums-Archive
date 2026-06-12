---
title: "Nvidia driver - screen corruption"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ivze on 2010-04-02
I have Nvidia GT220 video card with 1Gib of (video card) memory. I have been trying to run it with Nvidia binary drivers on x86_64 system since the beginning of March until now (Lucid beta + all fresh updates). My problem is that after some minutes of usage screen gets corrupted. There is a bug report at launchpad: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/532111](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/532111). It has some pictures.

Does anyone have anything to say about this:)?

---

### Post by nhasian on 2010-04-02
using the nvidia restricted drivers with linux kernel 2.6.33 i do get a little video corruption only on the login screen.  I have not experienced any video corruption after logging in though.

---

### Post by ivze on 2010-04-02
The default kernel for Lucid would be 2.6.32, so I didn't try other kernels. Also, I didn't try 32 bit version. The bug is definitely reproduceable: corruption always happens after 3-10 minutes of using. To make sure that I am not dealing with some hardware issues, I have tested the card with windows XP on a separate machine for some days. There were no such problems.

---

### Post by cyberkilla on 2010-04-02
Might be worth checking whether the Powermizer level changes in NVidia Settings at the same time the artefacts appear.

Looks like a long shot though, as the typical Powermizer-related artefacts I've seen are usually much more chaotic.

---

### Post by ivze on 2010-04-03
cyberkilla, great thanks for you idea!

Now after logging in I switch PowerMizer mode from "Adaptive" to "Maximum performance" and all works great! 3 hours of testing, no artefacts.

With this I can wait until new drivers are released. This is a suitable work-around for me.

---

