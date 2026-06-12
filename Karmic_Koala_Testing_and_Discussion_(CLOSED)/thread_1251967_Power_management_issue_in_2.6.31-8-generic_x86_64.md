---
title: "Power management issue in 2.6.31-8-generic x86_64"
date: 2009-08-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Tibuda on 2009-08-28
Today, the kernel update have fixed the shutdown issue, but now I have another issue with my laptop power management. The power management icon in the notification area always shows that the battery is full and charging, even if the cable is not plugged. When I open the power preferences, I don't have the "using battery" tab! It looks like Ubuntu/Linux thinks this is not a laptop. It was working yesterday, so I think it has something to do with the update that fixed the shutdown issue. Anyone got this too?

```
$ uname -a
Linux danielrmt-laptop 2.6.31-8-generic #28-Ubuntu SMP Thu Aug 27 14:42:57 UTC 2009 x86_64 GNU/Linux
```

Now, I'll reboot to [s]Jaunty[/s] older kernel for my battery life.

EDIT: It is working fine now in the latest kernel after a reboot. No idea what happened.

---

