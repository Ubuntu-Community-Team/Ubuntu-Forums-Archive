---
title: "Just making sure the upgrade works"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by vinitlee on 2007-04-20
I just want to be certain that an upgrade from Edgy to Feisty will work. Please, if anyone has gone trough it, I'd just like to have your comments on it. I've had bad experiences upgrading in the past. (also, by which method did you upgrade?)

---

### Post by pzearfoss on 2007-04-20
I was running compiz before and now I can't get the gl desktop to work.  Seems to create all sorts of problems with window borders now.  

I plan to try a fresh install and see if I have better luck with that.

---

### Post by elmerfud on 2007-04-20
I'd wait a couple days.   I had issues with rebooting, wireless and Xserver.

I have Xserver running, but not dual monitors.  Wireless works now, but I had to do a few manual ifups/downs and /etc/init.d/networking stops and starts.

---

### Post by Leebo on 2007-04-20
I had to reinstall my nvidia drives as i have to do with every kernek change but everything worked flawless for me..even beryl works..maybe i'm a lucky one?

Leebo

---

### Post by vinitlee on 2007-04-20
Erg. Doesn't sound very shiny. Hopefully, when I eventually update, I will only need to reinstall graphics drives and such!

Thanks for the feedback!

---

### Post by astronic on 2007-04-20
> **vinitlee said:**
> I just want to be certain that an upgrade from Edgy to Feisty will work. Please, if anyone has gone trough it, I'd just like to have your comments on it. I've had bad experiences upgrading in the past. (also, by which method did you upgrade?)

One major key to success is: Don't use non-Ubuntu (i. e. third party) packages and especially don't use third-party install/config tools like automatix or envy.

For example some people would just do everything to get Beryl working in Edgy, even though Beryl is not even part of Edgy and Edgy is not ready for Beryl. They therefore have to bypass the Ubuntu package management to install for example NVidia drivers not deemed stable for Edgy and also have to add third-party repositories from which many exciting packages get installed.

Now during the update process the Ubuntu update-manager of course has not that much of a clue about all the non-Ubuntu mess floating around and of course has not means to update it. Additionally Ubuntu of course doesn't QA the update process for arbitrary non-Ubuntu packages. So if your system is in such a non-well-defined state, things are far more likely to break during update. Also this is why I think most people having trouble with their update to Feisty on the forums have to blame themselves and not Ubuntu for their updates going wrong.

This doesn't change the fact that quite a few real bugs are around, so better wait a few more weeks until trying to update anyhow.

HTH,
Stefan

---

