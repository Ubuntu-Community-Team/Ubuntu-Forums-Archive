---
title: "Tips for Smooth Upgrade?"
date: 2014-12-29
forum: Installation &amp; Upgrades
---

### Post by pfthizzz on 2014-12-29
I'm running Kubuntu 13.10, and I figure it's past time to upgrade to 14.04.

Any tips for ensuring a smooth upgrade process? Things to check, set, etc?

Aside from backing up important data, any tips for quickly recovering from a problem should things go south? 

Are there any settings that I'm certain to lose, that I should record before kicking off the upgrade? Known issues with popular apps (e.g. Dropbox, e.g. Firefox)?
Is there a pre-upgrade check and/or compatibility test I can run?

Thanks!

---

### Post by nerdtron on 2014-12-29
Note sure about test compatibility programs before upgrade, but I just Run the LIVE CD and see if my hardware still works, wifi, lan, video etc.

Next I just backup my files. The important one (Or I just move them to another partition or hard drive).

Then I just install the new OS wiping the old OS out.

---

### Post by MAFoElffen on 2014-12-29
+1...

but additionally, take a peek at your software sources and ensure your are not pointed to any PPA's before you start your upgrade. That *will* cause problems.

---

### Post by buzzingrobot on 2014-12-29
Return the system to its default post-install state, or as close as you can get.  That includes removing PPA's from the sources list and, especially if PPA packages have replaced system packages, like a video driver, backing that software out.

---

### Post by ian-weisser on 2014-12-29
1) Back up your data before upgrading.
You should be backing up your data anyway. Bad stuff happens unpredictably.

2) Buzzingrobot is right: If you installed non-Ubuntu software, uninstall it before the upgrade.
You -the user- have no way to tell if non-Ubuntu software will break an upgrade due to a file conflict or a version conflict.
Example: if you installed a PPA to get the latest version of Shotwell,  uninstall Shotwell (and it's PPA-provided dependencies) before upgrading. Reinstall Shotwell after the  upgrade is complete.

3) If the installer offers you a 'partial upgrade', refuse it. The offer of a partial upgrade means you didn't complete step #2.

4) If the system is critical to you, test before upgrade. Nerdtron's recommendation of testing hardware from a Live media is excellent.

---

