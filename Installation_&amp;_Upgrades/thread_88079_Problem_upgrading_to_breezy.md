---
title: "Problem upgrading to breezy"
date: 2005-11-09
forum: Installation &amp; Upgrades
---

### Post by eoinmonty on 2005-11-09
Im new to linux and would be very grateful if anybody could help me.
Im trying to upgrade to breezy from hoary however i keep getting this error

The following packages have unmet dependencies:
  abiword-common: Depends: abiword but it is not installed or
                           abiword-gnome but it is not installed
E: Unmet dependencies. Try using -f.

I attempted to use synaptic to fix abiword-common which it sais is broken however it failed.

thanks in advance

---

### Post by frodon on 2005-11-09
did you follow these step to perform your breezy upgrade ? : [https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28breezy%29](https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28breezy%29)

---

### Post by eoinmonty on 2005-11-09
Yes i followed the apt-get instructions

---

### Post by frodon on 2005-11-09
You should use the synaptic way, it will allow you to solve some conflicts during upgrade that you couldn't solve using the apt-get way.
If you still have this problem, i advice you to remove all the abiword packages or to re-install it before the upgrade.

---

### Post by eoinmonty on 2005-11-09
I attempted to use synaptic however it will not allow me untill the abiword-common package is fixed.However it is unable to either Fix or remove it. I get an error saying failed to apply all changes.

---

### Post by eyebrowman92 on 2005-11-09
i had a problem similar to this when i first was upgrading. luckily i was new to linux and i upgraded to breezy the day i installed hoary. that stinks man.

---

