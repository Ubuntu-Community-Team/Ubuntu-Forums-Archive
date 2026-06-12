---
title: "Installing the latest coreutils"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by tieTYT on 2007-04-05
The latest coreutils has a new option for the sort command called -R/--random-sort that would be very useful for me.  But when I use synaptic/apt-cache to search for coreutils it says I already have the latest.  This is not true.  If you look at the coreutils website you'll see that they're up to 6.9 but ubuntu only has 5.9.  

How can I upgrade my coreutils (or at least get this -R option)?  I'm on ubuntu edgy and I don't know much about linux or package management.

---

### Post by tieTYT on 2007-04-05
In the mean time, the -R option can be duplicated with this command:

perl -MList::Util=shuffle -ne 'push @foo,$_; END { print shuffle @foo}'

---

