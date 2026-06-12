---
title: "System corrupted by upgrade to 14.04"
date: 2014-09-02
forum: Installation &amp; Upgrades
---

### Post by resmith2 on 2014-09-02
I have Xubuntu on a Windows 7 computer running as a Wubi install. I don't know what version I was at but it just offered and then tried to do an upgrade to 14.04. The upgrade downloaded everything and began intalling. At some point it popped up something saying that xscreensaver or xlock???? were running and would need to be halted. I killed xscreensaver at the terminal, didn't see the other running. It then continued on but eventually died with some error messages about something wasn't there or installed or whatever and something else was != 0. In short, the upgrade failed. But the terrible thing is, now my system will not boot.  I think there should be a big fat huge warning when you get offered the chance to do a huge major upgrade of this nature  - CAUTION: it may destroy your system! If you aren't really in need of  this upgrade DON"T DO IT!

---

### Post by fantab on 2014-09-02
WUBI installs are not supported any more.
Save all your important work... backup your data, preferably away from HDD. You can use Xubuntu install DVD/USB, if you have any problems from Windows.
[Uninstall WUBI]("https://wiki.ubuntu.com/WubiGuide#Uninstallation").

Install Xubuntu on its own separate partition and separate from Windows.

---

