---
title: "Will the ati driver work with upgrades from 6.06 to 6.10 to7.04 ?"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by leonid on 2007-12-04
Presently I am forced to use vesa with my radeon 7000 graphic card . As many users have experienced, using ati (radeon) will make the screen freeze . Will upgrading solve the problem? Also presently, moving the windows around will leave a cometlike trail. This is annoying.Does this have anything to do with the fact that I am using vesa. instead of ati? My monitor is A Samsun SyncMaster 997 MB. I would welcome an answer to my questions?

---

### Post by jbt on 2007-12-05
> **leonid said:**
> Presently I am forced to use vesa with my radeon 7000 graphic card . As many users have experienced, using ati (radeon) will make the screen freeze . Will upgrading solve the problem? Also presently, moving the windows around will leave a cometlike trail. This is annoying.Does this have anything to do with the fact that I am using vesa. instead of ati? My monitor is A Samsun SyncMaster 997 MB. I would welcome an answer to my questions?

Hi,

I have a similar system (radeon 7000 AGP and SyncMaster 920N)  running Gutsy 7.10.
I did a new install rather than an upgrade, and a single screen radeon works fine with the ati driver.

The only issues I had were because I'm running with 2 screens

The ati drivers have had a major overhaul to add xrandr support, so the xorg.conf settings have changed a lot (for dual screen configs). This may cause you a few niggles if you upgrade from an older version.

JohnT

---

### Post by leonid on 2007-12-05
Thank you John T. This is quite positive.  Do you have an idea if the cometlike trails  are related to the "ati -radeon -7000 agp card"  problem? I am looking forward to a better Video system  including Skype videeo.
Leonid.

---

### Post by jbt on 2007-12-05
> **leonid said:**
> Thank you John T. This is quite positive.  Do you have an idea if the cometlike trails  are related to the "ati -radeon -7000 agp card"  problem? I am looking forward to a better Video system  including Skype videeo.
Leonid.

I think the comet tails are just because of the poor performance of your video driver.
I don't get any comet trails.

I don't use skype, but I can watch videos OK, so I expect you will be OK.

---

