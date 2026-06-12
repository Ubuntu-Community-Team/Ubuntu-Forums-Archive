---
title: "Migrating from Mint to Ubuntu without reinstalling"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by MonoAM on 2011-07-15
Hello,

Is it possible to migrate from Linux Mint 11 to Ubuntu 11.04 without reinstalling the whole system, i.e. as if it was an upgrade from a previous version from Ubuntu. I would like to avoid having to reinstall and reconfigure all the applications I installed in Mint. 

Thanks,
MonoAM

---

### Post by Perfect Storm on 2011-07-17
Do you have separated /home partition?

---

### Post by XubuRoxMySox on 2011-07-17
I think it's possible (if you have the Ubuntu-based Mint rather than the Debian Edition) just by removing the Mint repositories from your sources list (do this in Synaptic). No more updates from Mint sources. Then while you're there in Synaptic, you can remove whatever Minty stuff you don't like, and re-install whatever software that Mint has messed with (like Firefox, for example, to which they added that frustrating Mint Search feature). Include Synaptic and Update Manager in stuff to re-install, since Mint's changes affect them too. The MintUpdater should prob'ly be removed since it may not determine "Levels" of stuff to update with the Mint repos removed. 

A separate /home partition, if you have one, would simplify this process and help you avoid future problems with upgrades.

Hope this helps,
Robin

---

