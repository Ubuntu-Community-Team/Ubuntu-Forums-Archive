---
title: "Why need for blocking RST devices from installing latest Ubuntu?"
date: 2022-04-04
forum: Installation &amp; Upgrades
---

### Post by alvincarter717 on 2022-04-04
I have Intel RST on my laptop. Ubuntu 20.04+ versions show RST error on ISO setup. But why?

Why Ubuntu 18.04 is allowed with RST but, 20.04+ not? The workaround is to install Ubuntu 18.04 and then upgrade one by one to 20.04 and then 21.10. And it works perfectly. If it works, then why did you block it in the newer setup?

I have used Arch, Endevous, Manjaro, Fedora, and PopOS non of the distro shows that error.  Everything just works. Ubuntu is known for stability and working on a lot of devices. I'm only getting this problem with Ubuntu only.

Can't the community do something about this?

---

### Post by guiverc on 2022-04-04
Your issue is a kernel issue, I don't know if it's been reported (*it cannot be fixed, or even looked at until reported*) and thus if any workarounds exists (*they're usually found on bug reports*)... however you've tagged your system as Lubuntu.

Please note Lubuntu 18.04 LTS was the end of the road with regards upgrades.

In later [release notes]("https://lubuntu.me/focal-2-released/") you'll find messages like 

> ***Note***, due to the extensive changes required  for the shift in desktop environments, the Lubuntu team does not support  upgrading from 18.04 or below to any greater release. Doing so will  result in a broken system. If you are on 18.04 or below and would like  to upgrade, please do a fresh install.

ie. LXDE details get left on your system that reduce the *polish* and *operation* of LXQt which later releases use, thus the recommendation of re-installing when using Lubuntu (`lubuntu-desktop`).

Those notices stopped being published when Lubuntu 18.04 LTS reached EOL (2021-April) thus weren't included in the* focal-3* or *focal-4* release notes, but it still applies.

The base Ubuntu system will upgrade correctly; the issues you'll have are with the desktop, and they vary depending on what applications you have installed. The issues are usually minor (*menu items that do nothing*) but maybe more significant.. I'm using a system that was *release-upgraded* from older LXDE releases and it was a *royal pain* getting this box working right, but I've also had boxes that were *simple*, but be aware that Lubuntu/LXDE systems that are *release-upgraded* (to Lubuntu/LXQt) are not *supported *and will have issues.

FYI:  The documentation that existed (created during the *cosmic* cycle) no longer exists I believe, though *bionic *to *focal* can be less troublesome than the earlier upgrade.

---

