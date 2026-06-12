---
title: "Need nvidia binary for TNT2 on Lucid 10.04"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by nicefinger on 2010-04-23
As standard it now comes with Nouveau. But there must be a bug, my monitor freezes after a while. Need the binary driver that is NOT in the Jockey-gtk anymore .. (71.** something).

Second solution is to activate driver nv. Is there a simple way to do that?
(maybe just deinstall Nouveau .. hmmm)

---

### Post by nicefinger on 2010-04-25
Yep, erase nouveau solved that. The result was nv with 800x600 res.
I had to copy a xorg.conf from elsewere. Puppy succeded where Lubuntu did not. Now I have 1280x1024 :)

Thank God for Puppy ... It has saved me many times.

---

### Post by nicefinger on 2010-04-30
Nobody can help me?

---

### Post by MoLE on 2010-05-06
Unfortunately, I can confirm the same freezing issue with the TNT2 on Lucid.  Happens with both the liveCD and an in-place upgrade from 8.04.4

I was able to disable Kernel Mode Setting (KMS) using this [wiki page instructions]("https://wiki.ubuntu.com/X/KernelModeSetting"), which forced xorg to use the nv driver.

I'm stuck with the nv driver now at 1024x768, and I don't seem to be able to use change the resolution either.

---

### Post by nicefinger on 2010-05-11
There must be some way to install the proprietary nvidia, don't you think?
Lubuntu is made for old computers. It works fine with my P3. Somebody must know how to do it.

---

### Post by MoLE on 2010-06-04
I have posted a bug with a workaround for the majority of the video issues with the TNT2.

Unfortunately 3D acceleration isn't one of them but it sorts out the video screen resolution problems.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/577314](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/577314)

If this affects you, please mark it as such.  The bug has been confirmed.

---

