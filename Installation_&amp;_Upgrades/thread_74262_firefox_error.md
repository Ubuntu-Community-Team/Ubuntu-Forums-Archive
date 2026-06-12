---
title: "firefox error"
date: 2005-10-11
forum: Installation &amp; Upgrades
---

### Post by leteci on 2005-10-11
Try to install firefox with synaptic!

Error message: 
E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox

Need help!

---

### Post by WildTangent on 2005-10-11
Ubuntu already comes with firefox. if its updates you want, they come whenever the ubuntu version is available (unfortunately, this is usually after mozilla releases and update)

-Wild

---

### Post by wylfing on 2005-10-11
I wonder if you're trying to "force" installation of the mozilla-firefox dummy package. As already pointed out, Ubuntu comes pre-installed with Firefox. You don't need to install it. Just choose Applications > Internet > Firefox.

---

### Post by dJeez on 2005-10-12
Nah, I just ran into the same problem. I did an apt-get upgrade and apparently the new packages (for firefox 1.0.7) cannot be installed, giving the error message mentioned above (same goes for mozilla-firefox-gnome-support btw).

---

### Post by openback on 2005-10-22
I'm having the same exact problem. And ever since I tried to upgrade firefox, it's been broken. It runs, but no window ever opens and it takes up 100% CPU. I can't uninstall the package either, since it complains about a conflict. Is there anyway to just force the upgrade maybe?

---

