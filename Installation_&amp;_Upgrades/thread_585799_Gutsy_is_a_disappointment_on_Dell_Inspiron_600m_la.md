---
title: "Gutsy is a disappointment on Dell Inspiron 600m laptop"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by kloudy on 2007-10-21
Gutsy was a real step backward on my laptop over Feisty.

I upgraded 7.04 to 7.10 yesterday and today several times.  HAL failure dialog always opens when I start the system.  I have not yet gotten the ethernet port to work but did finally get wireless to work.  I haven't even tried using my printer yet, since it is networked and I really struggled just to get wireless working so I could check for any fixes.

I am not sure what HAL does.  I have reinstalled it several times using package manager, but can't get it to start.  The network settings tool is very slow.  Sometime takes 2 minutes between OK and being able to get to the next tab.

The right side of the screen seems to extend about 1/2" past the right edge of the screen.  All-in-all I was happy with Feisty.  I wish I wasn't such an early adopter.

Hopefully there will be some fixes downloaded in a month or so.  If someone has an idea in the meantime, please let me know.

Thanks all,
Levi

---

### Post by Lord Landis on 2007-10-21
HAL is the Hardware Abstraction Layer.  Think of it as the OS's master record of your hardware.  If that's failing, then there's either some device that the OS can't recognize or there's some corruption going on.

It's not the sort of thing you can easily re-install, as it's pretty tightly integrated into nearly everything hardware-related.

---

