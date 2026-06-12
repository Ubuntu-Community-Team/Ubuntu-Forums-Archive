---
title: "authenticate"
date: 2015-12-31
forum: Installation &amp; Upgrades
---

### Post by mrbill4 on 2015-12-31
When I try to install an app from muon discover, I get an Authenticate window asking for a password, which I simple forgot. Is there anyway around this? I've been told from a friend who installed OS, that I will probably need to reinstall, but I thought I would check here to see if there might be another way. thank for any advice.

---

### Post by tokyobadger on 2016-01-01
[there's a howto at this link](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/) that show's how to reset it

---

### Post by QIII on 2016-01-01
tokyobadger, that is an extremely old article.  Please try not to refer other users to material nearly 8 years old.  It would also be preferable to find a reference closer to home.

Please see [this]("https://help.ubuntu.com/community/LostPassword") for more recent (a couple of years old, but still appropriate) information from the Ubuntu community.  Use the first method.

---

### Post by tokyobadger on 2016-01-01
@QIII: you're absolutely right, we have no idea what release of kubuntu mrbill4 is using and therefore whether we need to consider variables such as upstart vs systemd in the solution

Edit: [mrbill4  appears to be using an older release of kubuntu](http://ubuntuforums.org/showthread.php?t=2307793&p=13413702#post13413702)
[quote="mrbill4"]Okay, the platform version is Kubuntu or KDE 4.13.3[/quote]
which by my reckoning puts the OS [at 14.04](https://en.wikipedia.org/wiki/Kubuntu)

[For 14.04 there appears to be a new way](https://help.ubuntu.com/lts/ubuntu-help/user-forgottenpassword.html) to resolve a lost/forgotten password differing (slightly) from the solutions at the links referenced by QIII and myself - no reference to mount -rw -o remount / nor to init 2 nor again to init=/bin/bash

I tried all 3 solutions (the alternate solution in both links was identical) from the original links with 14.04, 15.10 and 16.04 and none worked 100% as advertised

The official solution for 14.04 [appears to be identical for 15.10](https://help.ubuntu.com/stable/ubuntu-help/user-forgottenpassword.html) and I'd guess for 15.04 by extrapolation.

---

### Post by mrbill4 on 2016-01-02
Thanks for your advice. I attempted several of the solutions listed, and none appear to be workable, at least with my limited understanding of linux and KDE and I'm afraid I will do more damage than good. This is a fresh install and I will not lose anything if I do a reinstall. So no worries! I've learned enough to avoid some of the pitfalls of setting up my desktop and going forward things will run more smoothly. I will leave this thread open for now and update once I have a fresh install. Thanks again, hopefully this will be helpful to someone who has a similar issue.

---

