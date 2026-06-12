---
title: "Dual Monitors in Karmic"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sideffects on 2009-10-21
Hi, I've been trying to figure out how to get dual monitors working in Karmic, but I've only found guides that are years old. Can anyone help me with this issue? Thanks!

---

### Post by themusicalduck on 2009-10-21
Which graphics card do you have?

---

### Post by sideffects on 2009-10-21
> **themusicalduck said:**
> Which graphics card do you have?
Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller, according to lspci | grep VGA.

---

### Post by themusicalduck on 2009-10-21
I've only used the program that Nvidia provides with it's drivers, but you might have some luck with System > Preferences > Display.

---

### Post by sideffects on 2009-10-21
> **themusicalduck said:**
> I've only used the program that Nvidia provides with it's drivers, but you might have some luck with System > Preferences > Display.
Yeah I did, and the then everything turns black and all I can see is the cursor, which I am unable to move. 5 minutes later I cut the power. This happened 2 times.

---

### Post by itsbrad212 on 2009-10-21
try going to the display, and ling the two boxes up horizontally

---

### Post by themusicalduck on 2009-10-21
This might be related to your problem: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/422301](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/422301)

It's been confirmed as a bug in Karmic, so you might have to use Jaunty until Karmic is released fully before it'll work. Although at least first make sure you have all the latest updates to check that it hasn't been fixed already.

---

### Post by sideffects on 2009-10-22
> **themusicalduck said:**
> This might be related to your problem: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/422301](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/422301)

It's been confirmed as a bug in Karmic, so you might have to use Jaunty until Karmic is released fully before it'll work. Although at least first make sure you have all the latest updates to check that it hasn't been fixed already.

Yeah, that sounds like the problem. Thanks a ton!

---

### Post by Longinus00 on 2009-10-22
> **sideffects said:**
> Yeah I did, and the then everything turns black and all I can see is the cursor, which I am unable to move. 5 minutes later I cut the power. This happened 2 times.

This is a bug.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/419328](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/419328)

Only current workaround is to disable compiz.

---

### Post by sideffects on 2009-10-22
> **Longinus00 said:**
> This is a bug.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/419328](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/419328)

Only current workaround is to disable compiz.

Perfect, that sounds even more like it. That is exactly my problem. Thanks for bringing this to my attention.

---

