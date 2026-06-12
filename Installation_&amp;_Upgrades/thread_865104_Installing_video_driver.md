---
title: "Installing video driver"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by willix on 2008-07-20
Hy
I've got a DELL laptop with an ATI Radeon X300 video card.
I installed the driver threw EnvyNG, it seamed to work. Then I noticed the [System] -> [Administration] -> [Hardware Drivers] menu and notice my [ATI accelerated graphics driver] was not enabled. So I enabled it which installed another driver. 

Everything worked good. 

Then my update manager notified me of an update for an fglrx-something library. Once that was done. My driver no longer worked.

I had to reinstall it threw EnvyNG but if I now try to enable the ATi accelerated graphics driver, it screws everything again.

Thus the following question:
1) How can I find the name of the library that screwed everything up? Does synaptic (or update manager) have a history of what was installed and when?
2) Whats the difference between EnvyNG and this enable check box in Hardware drivers?


Thanks
w.

---

### Post by JagDragon on 2008-07-20
The way EnvyNG works is it downloads and builds/installs the latest drivers from nvidia/ati and blacklists the restricted-modules ones. By enabling them, a spanner is thrown in the works.

If you want to update your drivers, use Envy.

The difference is:
Envy: Straight from the ATI/Nvidia website and into your computer, disables the fglrx-restricted-modules driver.
Check Box: Enables the fglrx-restricted-modules driver

---

