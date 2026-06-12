---
title: "Anyone know when we'll be able to install the nvidia driver from synaptic?"
date: 2009-12-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-12-21
Without it wanting to remove ubuntu-desktop and the whole of xorg?

---

### Post by autocrosser on 2009-12-21
Well---I'm using the 195.22 driver without any problems....[http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) lucid main   Installed without drama...works very well.

---

### Post by philinux on 2009-12-21
> **autocrosser said:**
> Well---I'm using the 195.22 driver without any problems....[http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) lucid main   Installed without drama...works very well.


Thanks Dean,
Cheers for that. I'm trying to stick with testing "as is". I assume the nvidia driver just needs rebuilding but it's taking an age to come through.

If it dont come through soon I'll be off to the ppa. :P

---

### Post by autark on 2009-12-21
I find these kinds of issues highly disruptive to the testing process, and should be avoided at all cost. I know the release is still far away, but every lost day is nevertheless a day that could have been used in some meaningful way instead of having maybe hundreds of potential testers either not testing or trying to work around the problem.

---

### Post by gnomeuser on 2009-12-21
> **philinux said:**
> Thanks Dean,
Cheers for that. I'm trying to stick with testing "as is". I assume the nvidia driver just needs rebuilding but it's taking an age to come through.

If it dont come through soon I'll be off to the ppa. :P

Actually the driver released as stable by nvidia isn't compatible with the xorg version shipped in Lucid. 

You'll have to use the beta driver in the ppa for now or the nouveau driver (no 3d nor vdpau support yet though).

---

### Post by hikaricore on 2009-12-21
> **gnomeuser said:**
> Actually the driver released as stable by nvidia isn't compatible with the xorg version shipped in Lucid. 

You'll have to use the beta driver in the ppa for now or the nouveau driver (no 3d nor vdpau support yet though).

Where do you get your info?
I've just tested 3 different versions of the driver including the stable and the beta with lucid's version of xorg and it works flawlessly on all of them.
Once kdm started funny but I just relaunched it and i was golden.

---

### Post by gnomeuser on 2009-12-21
> **hikaricore said:**
> Where do you get your info?
I've just tested 3 different versions of the driver including the stable and the beta with lucid's version of xorg and it works flawlessly on all of them.
Once kdm started funny but I just relaunched it and i was golden.

I apologize, I must have mixed up notes on the latest xserver release candidate and Lucid. Lucid does not carry the 1.8 RC releases which are incompatible with the current nvidia drivers (if I recall correctly even the beta drivers won't work due to API changes).

To make up for my mixup I found the correct bugreport tracking this issue and I nominated it for Lucid in the hope that it will get addressed.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/494166](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/494166)

the OP can subscribe to that and be notified when a fix is made available.

---

### Post by philinux on 2009-12-22
Yep I found that bug report late yesterday and subscribed.

---

### Post by philinux on 2010-01-12
Yeah, fixed.

Well done to the guys.

I just had to copy my xorg.conf from karmic to set up visual effects. Sys>admin>Hardware drivers not fixed as yet.

---

