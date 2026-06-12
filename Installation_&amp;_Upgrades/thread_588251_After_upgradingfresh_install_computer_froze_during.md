---
title: "After upgrading/fresh install computer froze during loading hardware drivers."
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by vitya on 2007-10-23
Hi,

I am trying to install Gutsy.
I started with a fresh install(dual boot with XP), but I couldn't boot into the live CD, it would always freeze during the time when you get that weird picture. So I thought maybe my cd was bad, so I downloaded another one, but it did the same thing. 
So I decided to install Feisty and then try to upgrade to Gutsy. Everything was normal during upgrade, but then I had to restart and it froze while booting. I pressed Ctrl+Alt+F1 and I saw that it was stuck at "intel_rng: unable to load LWH" or something like that. I search online for that and I saw people saying to add that module to blacklist file. But I couldn't boot into ubuntu so I couldn't do that. Then I decided to start and unplug some of my hardware. When I unpluged my wireless card (Zyxel G-302 v3) - everything worked perfect. So I went and added intel_rng to the blacklist file. Now it freezes during "loading hardware drivers".

Does anybody know how to fix this.

Thanks.

---

