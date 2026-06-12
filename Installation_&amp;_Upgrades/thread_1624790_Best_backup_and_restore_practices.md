---
title: "Best backup and restore practices"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by toolmania1 on 2010-11-18
What are some of the best back up practices?

For example, I recently messed up Ubuntu by doing something stupid.  I had to reinstall Ubuntu.  It did not take long, but I would like to have a backup of some sort that I could easily restore.  Things like Norton Ghost for Windows are nice since you can ghost a working installation and then be back up and running in a few minutes in this situation.

I have read about Clonezilla, but never used it.

Any ideas?

Also, is there some type of system restore in Ubuntu?

---

### Post by jpl888 on 2010-11-18
Store /home on a separate partition. If you need to reinstall saves borking the whole thing.

I use rsnapshot to backup. It's basically a cmd line version of Time Machine. Read something about Back In Time on here yesterday, seems to be a reasonable GUI way of doing it in Ubuntu.

---

### Post by azertyh on 2010-11-18
hello,
see the doc [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
see also in tutorials and tips forum, there are many howto backup and restore.

---

### Post by Frogs Hair on 2010-11-18
I use Back in Time as well , It backs up the home folder in one package , which is great for the six month release cycle.

---

