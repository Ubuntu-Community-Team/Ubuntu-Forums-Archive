---
title: "Help me, I can't install 10.10"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by Zegerv on 2010-11-07
Hello,


My Ubuntu 10.04 doesn't find the update to 10.10, how do I fix/find this? 
Also, i'm a complete beginner, so don't make it to hard.


Hope to hear something,
Zegerv

---

### Post by geoffmcc on 2010-11-07
To upgrade from Ubuntu 10.04 LTS on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '10.10' is available. Click Upgrade and follow the on-screen instructions.

But before you do that make sure your current release is up to date.

If no updates found - then do above

---

### Post by P4man on 2010-11-07
The above is correct, but to "make it easier" and explain why you may not see the upgrade, go to system > administration > update manager. Click "settings" > updates > release upgrade.

I suspect you have it set to Long Term Support releases only. 10.10 is not a LTS version (10.04 is). Change it to "normal releases" and update manager will prompt you to upgrade to 10.10.

---

### Post by Zegerv on 2010-11-07
Thanks, i've just noticed it. Stupid mistake, but still, thanks a lot.

---

