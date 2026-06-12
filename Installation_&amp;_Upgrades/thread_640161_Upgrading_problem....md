---
title: "Upgrading problem..."
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by hansyje on 2007-12-13
I was trying to upgrade to last Ubntu using: sudo apt-get update && sudo apt-get upgrade
I received this message and i have no idea what to do: E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


Could you guys please help me. Thanks!

I have kubuntu feisty and i want to upgrade to Gutsy

---

### Post by rsambuca on 2007-12-13
You have another package manager open.  Close it.

---

### Post by chippy99 on 2007-12-13
These are the instructions for upgrading [http://www.ubuntugeek.com/upgrade-ubuntu-704-feisty-fawn-to-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/upgrade-ubuntu-704-feisty-fawn-to-ubuntu-710-gutsy-gibbon.html)

Do not do it how you are trying to or you will break your sytem.

---

### Post by rsambuca on 2007-12-13
> **chippy99 said:**
> These are the instructions for upgrading [http://www.ubuntugeek.com/upgrade-ubuntu-704-feisty-fawn-to-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/upgrade-ubuntu-704-feisty-fawn-to-ubuntu-710-gutsy-gibbon.html)

Do not do it how you are trying to or you will break your sytem.

What are you talking about?  An update followed by an upgrade has nothing to do with changing versions of Ubuntu.  It updates the sources and then upgrades any packages in the repositories.

This should be done prior to upgrading to Gutsy.

---

### Post by chippy99 on 2007-12-13
I read this bit at the end of the post "I have kubuntu feisty and i want to upgrade to Gutsy" and presumed he/she was upgrading by changing his sources.
Which is what a friend of mine did last week and trashed his installation.

---

### Post by hansyje on 2007-12-14
Thanks both of you! 
I followed the link that Chippy suggested and it worked really fine.

---

