---
title: "upgrade ubuntu installed inside windows"
date: 2012-03-21
forum: Installation &amp; Upgrades
---

### Post by kaleem11 on 2012-03-21
[SIZE=3]can i upgrade ubuntu installed inside windows? i so, how? for example, i install ubuntu 11.04 inside windows and now i want to upgrade to 11.10. how can i? and i want to save installed softwares in ubuntu as well.
[/SIZE]

---

### Post by MG&amp;TL on 2012-03-21
You can; as with any form of installation-however, it's not always a good idea, and you might have some problems. If you do experience problems, backup your data, then remove wubi and get wubi for the 11.10 release instead.

Here's how:

-backup important data

-open update manager

-click 'settings' and set it to notify you of new ubuntu releases, not just LTS.

-install the update as you would any other.

-any software which conflicts with the update will be removed, but otherwise your software will still be there.
Have a nice day.

---

### Post by darkod on 2012-03-21
You can try, but success is not guaranteed. Wubi was never developed to be used as long term install so upgrades don't always work.

You could do it in a same way like a stand alone system. If you get asked to upgrade to a newer version just say Yes.

There is no need to save the installed software in any way during an upgrade, all software should remain installed because you are only upgrading, not doing a clean install.

If you plan to continue using ubuntu I suggest you start making plans to stop using wubi and make a proper dual boot.

---

### Post by kaleem11 on 2012-03-22
[SIZE=3]thank u both. 
[/SIZE]

---

