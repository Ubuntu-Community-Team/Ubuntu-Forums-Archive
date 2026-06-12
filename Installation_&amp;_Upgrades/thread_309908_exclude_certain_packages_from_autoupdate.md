---
title: "exclude certain packages from autoupdate?"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by gruadp on 2006-11-30
Due to a bug in cyrus-2.2 ([https://launchpad.net/distros/ubuntu/+source/cyrus-imapd-2.2/+bug/67111](https://launchpad.net/distros/ubuntu/+source/cyrus-imapd-2.2/+bug/67111)) I had to rebuild and reinstall this packages by my own.

Now the update-manager always wants to update this packages, which is quite annoying and I'm quite sure one day I'll accidentely upgrade this packages and reintroduce the bug in my system and make my users kill me :)

The funny thing is that update-managers wants to update a package with the very same package again. (see attached screenshot)

any idea how to get aroung this?

thnx
peter

---

### Post by an.echte.trilingue on 2006-11-30
Use [apt-pinning]("http://http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin").

Take care

-mat

---

### Post by CheckItOut on 2008-02-13
Or use wajig:

Install wajig with:
apt-get install wajig

Then exclude the package with:
wajig hold <package>

Good Luck

---

