---
title: "Is it safe to install 12.10 with Nvidia?"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by gilgongo on 2013-02-16
A couple of months ago, I merrily installed (from scratch, not an update) Quantal 12.10 64bit after having run 12.04.2 LTS just fine with my GeForce GTX 550Ti.

Big mistake. Nothing ran properly and it was all hellish.

Have the Nvidia bugs been squashed since then? If I installed it now (with nomodeset?) will it all be OK and I can run Unity 3D and stuff?

I know I should just find out for myself, but it was such as screaming pain in the foreskin last time that I thought I'd just see if anyone else has been there first.

---

### Post by grahammechanical on 2013-02-16
I always install without installing third party software. That way I do not get the Nvidia driver but Nouveau. At the moment Additional Drivers (it is a tab in Software Sources) is offering (on 13.04)

Nvidia-310 (proprietary, tested)
Nvidia-310-updates (proprietary)
Nvidia-304-updates (proprietary)
Nouveau (open source)
Nvidia-304 (proprietary)
Nvidia-experimental-304 (proprietary)
Nvidia-experimental-310 (proprietary)

On my GT 220 Nouveau works fine and so does Nvidia-310 (proprietary, tested). I have not experimented with the others. As you say, it can be a pain in the ...

Regards.

---

### Post by gilgongo on 2013-02-16
OK thanks. When I installed 12.10, it went with the Nouveau drivers but they didn't run in 3D, so I didn't get things like the HUD, for example, and the system dies every time it went to sleep. 

When you say "on 13.04" - do you mean Raring? Does Nouveau work OK in that release?

---

