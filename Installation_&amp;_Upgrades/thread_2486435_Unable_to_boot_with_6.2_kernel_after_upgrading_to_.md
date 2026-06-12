---
title: "Unable to boot with 6.2 kernel after upgrading to 23.04"
date: 2023-04-30
forum: Installation &amp; Upgrades
---

### Post by tL0z on 2023-04-30
Hi all,

I've just upgraded from 22.04 to 23.04. In the initial attempt, I ended up with an half configured 6.2 kernel. After investigating for a bit, I found out that it was due to a displaylink driver, so I removed that and then reinstalled the 6.2 kernel.

Unfortunately, it still doesn't work. When I attempt to boot with kernel 6.2, the boot process gets stuck in the following step:

```
Listening on systemd-rfkill.socket - Load/Save RF Kill Switch Status /dev/rfkill Watch
```

I am able to boot fine with the old 5.15 kernel.

I've had a look around but I can't find a resolution for this.

Can someone help please?

Thank you

---

