---
title: "Quake Wars crashes (sig11)"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-09-23
A few weeks ago Quake Wars stopped working for longer than five minutes.

The only thing I've noticed is if I run from a terminal, in amongst all the bot chat (playing a local game) near the end, there's some thread warning, a bit more chatter and then a seg fault.

```
WARNING: Thread 'FireThreadFake_sdScriptEntity_gameplay_strogg_shield_generator_trigger_78': idPhysics_RigidBody::SetClipModel: unbalanced inertia tensor for entity 'idProjectile_RigidBody_projectile_scud_86' type 'idProjectile_RigidBody'
Dev4r, Outpost: Hold That Vehicle!
Dev4r, Outpost: You lead, I'll follow!
Segmentation fault
```

The thread fault varies and sometimes it doesn't even happen; sometimes it just plonks out with a code "11" fault.

This is new under karmic... So no idea if it's me, the hardware, karmic or just plain bad luck. That's why I'm asking here. Anybody else having issues?

I'm running an i7 920, nvidia 8800gts on 185.18.36 drivers (twinview'd), 64bit 2.6.31 kernel (has been like this since at least -5).

---

