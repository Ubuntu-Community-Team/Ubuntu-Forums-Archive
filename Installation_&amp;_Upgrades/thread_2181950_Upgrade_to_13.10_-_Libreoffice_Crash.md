---
title: "Upgrade to 13.10 - Libreoffice Crash"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by fromhell.dave on 2013-10-19
upgraded 13.04 to 13.10
after upgrade:
Libreoffice crash with kernel: [ 1469.821496] traps: soffice.bin[4128] general protection ip:7f4c8c2fd970 sp:7fff70510700 error:0 in libmergedlo.so[7f4c89ee8000+3111000]
This occurs anytime a menu is selected in the global menu bar.
When starting any libreoffice application, am presented with the recovery dialog, then starts and loads ok. the instant you select a menu item, crash.
Libreoffice is unusable now.
Also worth noting. the logout, restart and shutdown selections in the system global menu do nothing now.
running 13.10 64 bit, intel motherboard with onboard graphics (intel sandybridge desktop).
prior to upgrade (on 13.04) i was running the intel-linux-graphics. The system was running great.
i do not see any indication of the intel-linux-graphics after the upgrade. maybe some remnants are still there....
any suggestions would be welcome........

---

### Post by bapoumba on 2013-10-19
[https://bugs.freedesktop.org/show_bug.cgi?id=63517](https://bugs.freedesktop.org/show_bug.cgi?id=63517)
That is the only report I found related to your issue, and no workaround.

---

### Post by fromhell.dave on 2013-10-29
thanx for the reply
had to do a fresh install of 13.10 (wasn't too happy about that) which corrected the problem
but then led to other issues such as wireless unable to thaw after suspend, no dropbox in global menubar,
moneydance failure (due to java i think),  lightning calendar in thunderbird failure (had to regress to lightning 2.6.0)
am still trying to track these issues down.
all in all a pretty painful minor release......

---

### Post by bapoumba on 2013-10-29
Hmm, sorry you are having such a bad experience. I have not upgraded yet (no time). Should do that next Sunday.

---

