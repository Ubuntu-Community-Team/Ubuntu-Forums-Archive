---
title: "cant install anything"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by cgm12mgc on 2008-02-26
i go to add/remove and try to select something to install and each time it just comes up and says refresh..  when i do download something it refuses to install, just closes each time,    this has happend on this laptop, (toshiba satellite a135) my desktop and my ps3, with my desktop a simple re-install fixed the issue, however it doesnt seem to help here, i know someone out there has had and fixed this problem.


any help would be great,

Thanks,
Charlie

---

### Post by taurus on 2008-02-26
Sounds like you don't have any repo enable in /etc/apt/sources.list.  While you still have Add/Remove running, click Preferences -> Ubuntu Software and make sure there is a check mark in front of all the lines except the last one, Source code, and the Cdrom in the window below.  Close it and click Refresh.  Now, see if you can install anything this time.

---

