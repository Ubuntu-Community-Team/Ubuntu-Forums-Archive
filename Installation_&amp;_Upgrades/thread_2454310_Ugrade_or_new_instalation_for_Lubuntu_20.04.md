---
title: "Ugrade or new instalation for Lubuntu 20.04?"
date: 2020-11-26
forum: Installation &amp; Upgrades
---

### Post by brunozero on 2020-11-26
Hello Ubuntu community,

I have a computer running Lubuntu 18,04 and I would like to upgrade to Lubuntu 20.04. However, I read somewhere that upgrading from a LXDE to a LXQt desktop is not advisable because doing so could result in a broken system.
I this information true? Should I do a fresh installation instead of simple upgrade? Note that every time I install upgrades in my computer I receive a message from Ubuntu telling that Lubuntu 20,04 is available and that I should do an UPGRADE (not a fresh installation. This is a little bit confusing. I want to be sure that if I proceed with the upgrade I won't have a broken system as a result.

Thank you very much for any information you can give me.

Bruno B. Zero

---

### Post by CelticWarrior on 2020-11-26
Yes, it's true.
If you want Lubuntu 20.04 do a clean install.

You can (probably should) open Software & Updates > Updates and change the bottom setting to "never".

---

### Post by tea for one on 2020-11-26
> Note, due to the extensive changes required for the shift in desktop environments, the Lubuntu team does not support upgrading from 18.04 or below to any greater release. Doing so will result in a broken system. If you are on 18.04 or below and would like to upgrade, please do a fresh install.

This extract was taken from [https://lubuntu.me/focal-1-released/](https://lubuntu.me/focal-1-released/)

---

### Post by GhX6GZMB on 2020-11-26
Fresh installation.
The leap from LXDE to LXQt is too great for an update.
Be careful where you get the installation .ISO image from. lubuntu.me is the official site, lubuntu.net is a cybersquatter.

Current LTS is 20.04.1 and works wonderfully.

---

### Post by guiverc on 2020-11-26
@tea for one has already provided the official Lubuntu response. Great responses from others too!

Your base Ubuntu system will see the upgrade (18.04 to 20.04.1) so will offer it, but due to change of desktop, problems are possible, thus the Lubuntu stance of *unsupported*.  

Note: The problems you'll have may vary on what packages you've added to your system, and what changes you've made. A clean re-install will ensure the best experience of the new LXQt desktop, but you can always use an *unclean* re-install too (ie. using "*Manual Partitioning*", selecting your existing partition(s) and ensuring you don't format; it'll erase system directories (only) and install; it then tries to reinstall your additional packages, where some unwanted LXDE crud could be re-installed if you've caused packages to be set to *manually installed* due to prior commands, but it's worked in the testing I performed)

I've seen numerous reports of people upgrading and not having any issues so they claim (though given it's only in support venues that I see these upgrade reports, no issues maybe a *slight* stretch), but the number leads me to believe it's possible, and at least a number report few issues.

If it was me, and you've made the decision to clean install for the *best* experience, you could always backup, then try the *release-upgrade* first, and if you don't like the problems, do the clean install then (or my suggested *unclean* re-install)

I made the move from 18.04 to 18.10; and yes I had problems. This system is that upgrade, and it's now on *hirsute* (*I upgrade every six months, and am on the development cycle*, *but was slow to upgrade during the cosmic cycle due change of DE*).

 There are reasons why clean install are recommended and upgraded systems *unsupported*.  Problems may not be severe, just minor annoyances that will lessen the experience.

---

