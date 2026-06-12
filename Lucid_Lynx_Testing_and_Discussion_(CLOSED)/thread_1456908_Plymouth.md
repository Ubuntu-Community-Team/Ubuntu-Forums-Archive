---
title: "Plymouth???"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by purgatori on 2010-04-17
I have been experiencing frequent Xorg/xserver crashes, as reported in [this bug](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/564570). I have noticed that after X goes down, there is a brief period of time where an error message about mountall and plymouth having failed some command or some nonsense like that. The two events seem to be related, so I figure that maybe one solution would be to remove plymouth. When I look at the description in aptitude, it certainly doesn't _sound_ all that essential, but when I attempt to remove it, it wants to take just about everything with it! So my question is, why have (I'm assuming) the Ubuntu devs made so many critical pieces of software dependent on such a non-essential application? And is there any way I can banish it without taking half my system with it?

EDIT: Used a hacked version of mountall to change the dependency status of plymouth so I could remove it. After doing so, xorg crashing problem persisted, thus ruling out plymouth as the cause. Still, I think that plymouth should be changed to an optional package, since Ubuntu **clearly** works fine without it.

---

### Post by Yellow Pasque on 2010-04-17
Out of curiosity, what video driver are you using? I'm using the open-source radeon/ati drivers, which spit out errors when X crashed. I found that removing plymouth fixed it.

---

### Post by purgatori on 2010-04-18
> **Temüjin said:**
> Out of curiosity, what video driver are you using? I'm using the open-source radeon/ati drivers, which spit out errors when X crashed. I found that removing plymouth fixed it.

I'm using the xserver-xorg-video-intel driver for my 82845g embedded graphics device.

---

