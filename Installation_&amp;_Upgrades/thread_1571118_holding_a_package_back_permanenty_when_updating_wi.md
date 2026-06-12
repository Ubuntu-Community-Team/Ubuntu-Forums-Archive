---
title: "holding a package back permanenty when updating with update-manager"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2010-09-09
ok  the new version of soundkonverter in maverick seems to me lame beyond belief so i want to hang on to the soundkonverter.3.8  version which was on lucid so i have installed it


MY QUESTION IS is there a way to never have update manager trying to update it

unclicking it every time i want to do my weekly update with update manager could be a massive pain in the rear


how would i go about that?

---

### Post by slakkie on 2010-09-09
man apt_preferences

---

### Post by lechien73 on 2010-09-09
Yes, you can exclude certain packages from being updated.

Go to **System > Administration > Synaptic Package Manager**. Find the package you wish to exclude from updates, and click on it. From the **Package** menu, select **Lock Version**.

---

### Post by shantiq on 2010-09-09
> **lechien73 said:**
> Yes, you can exclude certain packages from being updated.

Go to **System > Administration > Synaptic Package Manager**. Find the package you wish to exclude from updates, and click on it. From the **Package** menu, select **Lock Version**.


superb thank you   sorted:KS

---

### Post by VcDeveloper on 2010-09-09
I'm locking the version for the PHP5.2.10 before updating to 10.04 but it still updating to 5.3.2.  I need the 5.2.10 for my Drupal 6.19.  I only selected the ones I need, do I have to select all of them to keep it from updating?

---

