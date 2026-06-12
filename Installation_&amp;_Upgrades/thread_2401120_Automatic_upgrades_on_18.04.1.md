---
title: "Automatic upgrades on 18.04.1"
date: 2018-09-13
forum: Installation &amp; Upgrades
---

### Post by penman131 on 2018-09-13
Hi all
Firstly, I apologize if this has been asked before. (but there are over 6000 pages in this section of the forum)
When Ubuntu informs me that there are updates to download and I come across some that I do NOT want installed, I uncheck the box next to them. The next time updates are available, the updater asks me AGAIN if I want the same updates installed. Why does the installer not respect my wishes and ignore those updates the next time ?
A case in point is install of some braille software. I am sorry but my eyes still function, and I do not want any useless software on my (old) computer.
Is there any way around this (a setting somewhere, or is this just the way it is) ?
Sorry for being frank. (that's not my name) ;)

P

---

### Post by Dennis N on 2018-09-13
Probably not the best idea to ignore security updates, but to answer your question:

Unchecking the box by the package only applies to the current upgrades you are doing. If for some reason you want to always ignore upgrading a certain package, you can hold back the package like this using the terminal:
```
sudo apt-mark hold package-name
```
You can revert this with
```
sudo apt-mark unhold package-name
```

---

### Post by penman131 on 2018-09-13
Thanks for the reply. Seeing as I do not classify this as a "security" update; I'll give this a shot.

P

---

### Post by Impavidus on 2018-09-14
When I uncheck some particular update (rarely happens), it's because I don't want to install it yet. Maybe I want to install it tomorrow, so it's best that the update manager proposes the upgrade later again.

You can put the package on hold, in other words pin it at a particular version, but that may later lead to dependency problems. You can pin the package foo at version x, but foo version x may depend on libfoo version x, so this pins libfoo too. Now you want to upgrade package bar to version y, which is later than x, but bar version y depends on libfoo version y. Now you have a problem: pinning foo means that the unrelated package bar got pinned too.

You can also remove software that's useless to you.

---

