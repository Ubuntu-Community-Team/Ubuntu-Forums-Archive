---
title: "[solved] sudo do-release-upgrade"
date: 2018-05-04
forum: Installation &amp; Upgrades
---

### Post by zeedo65 on 2018-05-04
Hi

I can not see the ubuntu 18.04 upgrade after sending the command in terminal (see below). I need the new version because the 17.10 support will be lost soon and I need a stable release to do my projects. So, I am in hurry to install 18.04. So, the question is that do you have any news about the date that this upgrade will be available? And, if I upgrade to 18.04 using the developer version, does it need a full release-upgrade to the latest version or it just comes in the form of an update.

The main thing is that for my case, installation of the drivers will take lots of time, so, if I do all of these things on 17.10, I need to do all again on 18.04 as well and that is annoying. 
[COLOR=#000000][I]sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found.



[/I]
[/COLOR]

---

### Post by PaulW2U on 2018-05-04
> **zeedo65 said:**
> sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found.
Upgrades have now been enabled but in the "Software & Updates" application you will need to be notified "For any new version". If you are set to be notified "For long term support versions" then I think you won't be notified of the upgrade until 18.04.1 is released in July.

Make sure you are fully updated before starting the upgrade and then follow the prompts but look out for any error messages. You will end up with a fully updated installation of 18.04 but any PPAs that you have will be disabled and may need editing before re-enabling if 18.04 versions don't yet exist.

Just so as you know, an upgrade from Xubuntu 16.04 ddidn't work for me a couple of days ago. :(

---

### Post by zeedo65 on 2018-05-04
Hi

Awesome, thanks. you are right. The problem was that I put it on Long term support versions. It was my idea to keep the 18.04 for long term, so, I just enabled it for LTS versions.

---

### Post by kansasnoob on 2018-05-05
> **PaulW2U said:**
> Upgrades have now been enabled but in the "Software & Updates" application you will need to be notified "For any new version". If you are set to be notified "For long term support versions" then I think you won't be notified of the upgrade until 18.04.1 is released in July.

Make sure you are fully updated before starting the upgrade and then follow the prompts but look out for any error messages. You will end up with a fully updated installation of 18.04 but any PPAs that you have will be disabled and may need editing before re-enabling if 18.04 versions don't yet exist.

Just so as you know, an upgrade from Xubuntu 16.04 ddidn't work for me a couple of days ago. :(

If you're running Xenial and set Software & Updates to notify of "any new version" it will offer the upgrade to Artful which is only supported for another 3 months.

---

