---
title: "Newbie upgrade error"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by awang on 2008-05-12
In attempting a distribution upgrade, running a partial upgrade, in preparig the upgrade, I get the following error message.

Can't install 'ubuntu-desktop'

It was impossible to install a required package. Please report this as a bug. 



I'm a relatively new user.

Awang

---

### Post by Pumalite on 2008-05-12
Give more details and post your entire outputs.

---

### Post by awang on 2008-05-15
On bootup, Update Manager reports that there are 614 updates.
I get a popup that says, "Not all updates can be installed", "Run a partial upgrade, to install as may updates as possible."
I click "Partial Update" button, and get a popup that says, "Can't install 'ubuntu-desktop'", "It was impossible to install a required package. Please report this as a bug."
I click "OK" button, and get a popup that says, "Could not calculate the upgrade"

Albert

---

### Post by Pumalite on 2008-05-15
You are talking about 'updates' and upgrade' here. What was it?

---

### Post by awang on 2008-05-16
References to updates and upgrades are as quoted from the messages and dialog boxes.

---

### Post by awang on 2008-05-16
What is the best way to present screenshots?

---

### Post by Sef on 2008-05-16
> What is the best way to present screenshots? 

Use a digital camera and download the pics to an os that works or the Live CD and attach the photos.

---

### Post by awang on 2008-05-18
How do I submit a bug report?

Albert

---

### Post by _sluimers_ on 2008-05-31
Not 100% sure, as I haven't done it before, I beleive Ubuntu bugs are reported at launchpad
[https://bugs.launchpad.net/](https://bugs.launchpad.net/) -> report a bug

If I'm correct, this bug has already been reported, though his problem was that ubuntu-studio and after uninstalling it worked.
I have the same problem as you and am currently reinstalling ubuntu-desktop through aptitude.. I'll let you know if this fixes it for me.

---

### Post by Kevbert on 2008-05-31
You may want to run:
```
sudo apt-get install -f
```
This will repair any partially installed packages.  Then run
```
sudo apt-get update
sudo apt get dist-upgrade
```
This will upgrade, from say, Gutsy 7.10 to Hardy 8.04.
If you still get problems you may need to change servers.

---

### Post by awang on 2008-05-31
Thanks for the suggestions.
I think I solved most of my problems by upgrading directly to Hardy 8.04.

---

