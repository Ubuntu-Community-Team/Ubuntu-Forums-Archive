---
title: "Sorry, Ubuntu 15.10 has experienced an internal error."
date: 2016-07-03
forum: Installation &amp; Upgrades
---

### Post by UserJB on 2016-07-03
Sorry, Ubuntu 15.10 has experienced an internal error.

That is the error message whenever I log into the Ubuntu PC I just installed.  I'd paste the text of the error here, but the window that displays the message does not cut-and-past.

So, what do I do?

It tells me to upgrade a list of packages which is 1000 characters long.  But I can't cut and paste the list into a window?  What do the Ubuntu developers expect me to do?  Type every package into the command line?  And, why do I have to upgrade packages if I just did a fresh install?  (yes, I already did apt-get update).

---

### Post by &amp;KyT$0P# on 2016-07-03
> why do I have to upgrade packages if I just did a fresh install?
Because the packages distributed on the CD image are not necessarily the latest packages

> (yes, I already did apt-get update)
apt-get update doesn't upgrade the packages, it just downloads the current list(s) of packages.  In order to upgrade the packages, also run apt-get dist-upgrade

---

### Post by Impavidus on 2016-07-04
The packages in the live disk were the lastest versions when the live disk was released, which was last October. You have about 9 months of updates waiting. The atp-get update command made the package manager aware of the updates, now the command **sudo apt-get dist-upgrade** should be able to install them.

Note though that 15.10 is almost end-of-live. Better not spend too much time on it, as you'll have to upgrade before the end of the month. In fact, better not spend any time on it, but do a fresh installation of 16.04 LTS right away.

---

