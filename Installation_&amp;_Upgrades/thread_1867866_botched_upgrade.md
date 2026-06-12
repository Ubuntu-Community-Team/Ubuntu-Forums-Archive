---
title: "botched upgrade"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by isecore on 2011-10-23
*(apologies for the crossposting, in my frustration I somehow missed there were an installation/upgrades section)*

So, how do you redo an upgrade? I had a perfectly running Natty system, I attempted to upgrade to Oneiric. Halfway in it gives me some noise about gnome-dropbox, and with about 6 minutes left the updater simply dies. Now my system is half-functional. It boots, but no sound, and there are numerous glitches in the desktop indicating that some packages are either missing or weren't upgraded properly.

So, how to resolve this?

Each upgrade I grow more and more tired of the increasingly more unstable way of upgrading. Now I need to resolve this, and reinstalling is not an option.

It would also seem that having dropbox installed while attempting to upgrade is VERY DANGEROUS.

---

### Post by zvacet on 2011-10-24
```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

