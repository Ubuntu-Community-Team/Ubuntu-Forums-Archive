---
title: "gparted and automatic mounting"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by Lary Grant on 2007-08-07
There seems to be a bad interaction between gparted and the automatic mounting feature in Ubuntu.  Several times I've noticed that in the middle of the gparted process, the automounting happens and it messes up the rest of the commands that gparted is trying to do, in particular growing the filesystem.  Is there any way to report this as a bug?

---

### Post by merlinus on 2007-08-07
Are you using gparted live cd?

-merlin

---

### Post by Lary Grant on 2007-08-07
No... this has happened in both Feisty Live CD and installed Feisty.

---

### Post by merlinus on 2007-08-07
Both use an older version of gparted.  The latest is on the live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

It also has new features in terms of partition re-sizing and moving.  For example, it can re-size partitions from either end, whereas the older version could only do that from the right.

It is also why folks like Pumalite and me usually recommend using the live cd version to set up partitions before installing ubuntu.

Unless, of course, one is saddled with vista.

-merlin

---

### Post by Lary Grant on 2007-08-08
OK, but this is a tricky issue.  It is not an issue that can be fixed in gparted itself.  It is actually an interaction between gparted and the auto-mounting process.  Gparted needs to be able to disable the auto-mounting temporarily.

---

### Post by dabl on 2007-08-08
If you boot the GParted Live CD, there's no Ubuntu present.   Only GParted and your hardware.  :)

---

