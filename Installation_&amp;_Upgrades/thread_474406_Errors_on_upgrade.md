---
title: "Errors on upgrade"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by badguitarist on 2007-06-15
hi...i tried running sudo apt-get upgrade...and am getting the following error

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  firefox-gnome-support: Depends: firefox (= 1.5.dfsg+1.5.0.12-0ubuntu0.6.06.1) but 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1 is installed
E: Unmet dependencies. Try using -f.


when i tried running  sudo apt-get install -f, this is the error am getting...

Preparing to replace firefox 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1 (using .../firefox_1.5.dfsg+1.5.0.12-0ubuntu0.6.06.1_amd64.deb) ...
Unpacking replacement firefox ...
dpkg: error processing /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.12-0ubuntu0.6.06.1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/mozilla-firefox', which is also in package j2re1.4
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.12-0ubuntu0.6.06.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

can someone please help me rectify this error??...thanks...

---

