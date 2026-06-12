---
title: "Minecraft running slowly?"
date: 2012-07-02
forum: Installation &amp; Upgrades
---

### Post by Morgannah on 2012-07-02
Hello all!

I recently installed ubuntu 10.10 and installed the Linux version of Minecraft and I noticed it runs very sluggishly, as opposed to it running perfectly in Windows. I even gave it more RAM. (-Xmx2048M -Xms1024M)

Any help?

---

### Post by efflandt on 2012-07-03
You might give some clue what video card and driver you are using.  If not sure, post the output of **sudo lspci -v** related to your video card/chip.

I have generally found minecraft to run faster in Ubuntu than in Win7.  Although, that is most apparent when testing it on AMD C-50 1 GHz 2 core 2 GB tablet PC w/ATI HD graphics 32-bit Win7 Pro vs. 64-bit Ubuntu 11.10 (openjdk-6-jre) where it is actually playable in Linux and not so much in Windows.

I did have something strange happen on my desktop. It has generally been running 150-250 fps and I thought 12w26a snapshot  was running slightly faster.  But suddenly Sunday in 64-bit 11.10 it was running 25-30 fps (smoothly with no lag) even in different worlds or when game restarted, and my video card was more than 20 degrees C cooler than normal.  I copied .minecraft dir over to 12.04, booted that, and that was back up to normal speed.  I booted back into 11.10 and then that ran normal speed.  So I don't know why minecraft was temporarily running about 10% of its normal speed even though gpu and a core of cpu were full speed (but gpu much cooler).

It ran full speed in 64-bit 10.10 too, but I recently replaced that with 12.04.

---

