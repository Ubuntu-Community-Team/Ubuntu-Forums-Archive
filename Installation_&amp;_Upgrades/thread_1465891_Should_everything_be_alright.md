---
title: "Should everything be alright?"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by blah... on 2010-04-29
Today I was upgrading from Karmic to Lucid, and about 15 minutes before all the files have been installed, my battery dies (it was connected to a faulty charger). So when I start it up, it says to do a partial install. So I do it, and it says that no upgrade is necessary, but I can't shake off the feeling that something might be wrong since the original upgrade went wrong... ideas?

---

### Post by jjcv on 2010-04-30
It does not sound good if it died before the upgrade was finished.   The last step is usually installing the latest kernel in grub.    What kernel is it booting.

From a terminal you can always try

sudo aptitude safe-upgrade
sudo aptitude full-upgrade

---

### Post by blah... on 2010-04-30
> **jjcv said:**
> It does not sound good if it died before the upgrade was finished.   The last step is usually installing the latest kernel in grub.    What kernel is it booting.

From a terminal you can always try

sudo aptitude safe-upgrade
sudo aptitude full-upgrade
2.6.32-21-generic is the one I'm booting with right now, and I tried both, nothing happened. My indicators on the panel have turned to white squares though =P

---

