---
title: "Karmic beta dual monitor"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by P4man on 2009-10-10
Has anyone tried a karmic beta livecd on a dual monitor PC?
It doesn't boot for me, neither the livecd, nor the an installed version if two monitors are connected. I get graphical corruption and xorg hangs. If I disconnect either of the monitors, it works fine (and it also works fine with both monitors after installing binary drivers).

Anyway, i opened a bug for this, but im curious if anyone else is seeing the same?

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/447171](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/447171)

---

### Post by P4man on 2009-10-11
No one else using dual monitor, or no one else having this bug?

---

### Post by nick_stokie on 2009-10-11
I get problems with Karmic beta where the second monitor will only clone (copy) the output of the first rather than being an extended desktop. If I try to force the second monitor through Xorg.conf (as done previously) the system will fail to boot.

I haven't had enough time to problem try to find the problem, so can't add much to the bug at present, sorry.

Nick.

---

