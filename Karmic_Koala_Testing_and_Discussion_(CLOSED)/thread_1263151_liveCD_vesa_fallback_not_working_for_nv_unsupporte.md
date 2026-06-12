---
title: "liveCD: vesa fallback not working for nv unsupported nvidia cards"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by victorb on 2009-09-10
Using 09/09/09 liveCD or alpha5 with a nvidia 9400M in a dell laptop, X fails to start as the video card is not supported by nv and the vesa fallback is not working; I end up on a tty login prompt.

Excerpt from Xorg log:
   [...]
   (II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
   [....]
   (WW) NV: Ignoring unsupported device 0x10de0866 (C79 [GeForce 9400M G]) at 02@00:00:0

A few people already reported this in the xserver-xorg-video-nv package ([#422463]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/422463"), [#413439]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/413439")), but I think the main problem is not that NV doesn't support some video cards, but that there is no fallback and the user ends up on a text prompt. Sounds like a major showstopper for any new user. 
Anybody knows which package I should report this bug under in launchpad? It's not really nv specific, nor usplash, nor gdm.. any idea?

Note: Starting the liveCD in safe graphics mode works fine.

---

### Post by MacUntu on 2009-09-10
> **victorb said:**
> Note: Starting the liveCD in safe graphics mode works fine.

Did you test that with the Alpha 5 Live CD or a newer one? I'm asking because that didn't work for me with the Alpha 5 Live CD: [https://bugs.launchpad.net/ubuntu/+source/caspar/+bug/423969](https://bugs.launchpad.net/ubuntu/+source/caspar/+bug/423969)

---

### Post by victorb on 2009-09-10
I should have said using vesa instead of starting in safe graphics mode. Since I am using a USB drive to run the liveCD, I do not have access to the safe graphics mode option from the CD. What I did is create a minimalistic xorg.conf from the command line to use the vesa drivers, which allowed me to start X.

My point is: is any dev aware that if nv doesn't support your nvidia card, the liveCD shoots you out to a text console instead of falling back to vesa?

---

### Post by MacUntu on 2009-09-11
Maybe this bug is related (at the end the question was why the fallback to vesa failed): [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/385658](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/385658)

> Bryce Harrington wrote on 2009-07-30: 


Second is the issue that if a card is not supported by -nv, the xserver should not attempt to boot -nv, but rather use -vesa. I've filed this issue upstream as [https://bugs.freedesktop.org/show_bug.cgi?id=23045](https://bugs.freedesktop.org/show_bug.cgi?id=23045) - sub to this one if you wish; it's probably the more likely bug to get solved in time for karmic.

---

### Post by victorb on 2009-09-11
Yup that's a good one. I commented and subscribed on this bug. 
Thanks for the heads up!

---

