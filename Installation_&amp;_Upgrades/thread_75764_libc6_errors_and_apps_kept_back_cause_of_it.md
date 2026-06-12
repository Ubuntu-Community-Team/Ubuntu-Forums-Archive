---
title: "libc6 errors and apps kept back cause of it"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by Liz on 2005-10-14
is anyone else having problems with some upgrades?

i upgraded via sudo apt-get dist-upgrade on monday. 
all is well, except, i no cant use or upgrade a few apps that i use. 

ie. 
mozilla-thunderbird:
  Depends: libc6 (>=2.3.4-1) but 2.3.2.ds1-20ubuntu14 is to be installed
 Depends: libcairo2 (>=1.0.2) but it is not installable
  Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
  Depends: libgcc1 (>=1:4.0.1) but 1:4.0.0-7ubuntu6~5.04ubp1 is to be installed
  Depends: libglib2.0-0 (>=2.8.0) but 2.6.3-1 is to be installed
  Depends: libgtk2.0-0 (>=2.8.0) but 2.6.4-0ubuntu4 is to be installed
  Depends: libpango1.0-0 (>=1.10.1) but 1.8.1-0ubuntu2 is to be installed
 Depends: libstdc++6 (>=4.0.1) but it is not installable


i get similar errors of dependencies with numlock, nethack, open office, tuxracer...and they all have in common a problem with the libc6 depend. 

anyone else have this problem???

---

### Post by wezzer-foo on 2005-10-14
I had same kind of problem and the only solution was to remove all packages that were part of the problem and then reinstall them from breezy repository / breezy cd. CD was a lot of quicker because all repositories were kind of slow... :)

//EDIT There might be a lot easier way to solve this, because it took almost 4 hours to me to upgrade breezy because I had to first remove all kinds of packages and then install newer version etc.

---

### Post by Liz on 2005-10-15
well after 12hours of downloads, and rebooting to do upgrades...im fully installed and no more errors...

i got an email last night to say it had broken repositories..hence the errors.

---

