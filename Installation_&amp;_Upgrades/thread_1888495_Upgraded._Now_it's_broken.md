---
title: "Upgraded. Now it's broken"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by gavofyork on 2011-11-29
Hi,

I'm on a Macbook Pro 5,3. I was using Ubuntu 11.04, and I recently upgraded to 11.10.

It now fails before it gets to the GUI, the final messages on the console being:

* Stopping Failsafe Boot Delay [ OK ]
* Starting LightDM Display Manager [fail]
mountall: Disconnected from Plymouth
[ ... ] b43-phy0 ERROR: Cannot request IRQ-0
[ ... ] b43-phy0 ERROR: Cannot request IRQ-0

The keyboard cannot be used to scroll or enter any text on the console.

I tried booting in the recovery mode - it gets to the curses UI, but the USB obviously isn't working since neither the internal keyboard nor an external USB keyboard function at all. Altering the GRUB command line to bypass everything and drop to a shell (using the boot option init=/bin/bash) reveals a shell with, again, no USB I/O, so my investigation doesn't get very far.

Ideas?

---

