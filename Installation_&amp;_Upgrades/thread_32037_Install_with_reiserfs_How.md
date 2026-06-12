---
title: "Install with reiserfs? How?"
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by barton on 2005-05-05
I would like to use the reiserfs for my root partition. Is this possible and if so how do I do it from the install disk?

---

### Post by bored2k on 2005-05-05
Yes it is possible.
[[IMG]http://img82.echo.cx/img82/9828/screenshotgparted8ic.th.png[/IMG]](http://img82.echo.cx/my.php?image=screenshotgparted8ic.png)

During the partitioning step, do not select auto. partitioning. 
[[IMG]http://img121.echo.cx/img121/6157/92fa.th.png[/IMG]](http://img121.echo.cx/my.php?image=92fa.png)
Inside the manual section, select your "to become Reiser" partition. After selecting it [and pressing ENTER], you should see a menu indicating the type of partition you wish to create.

---

### Post by Professor X on 2005-05-05
You can install with reiserfs.  You will need to select the option to manually partition during installation.  It should be straightforward from there.

---

### Post by poofyhairguy on 2005-05-05
[QUOTE=barton]I would like to use the reiserfs for my root partition. Is this possible and if so how do I do it from the install disk?[/QUOTE]


Don't do autopartitioning. Tell it no. Then after the no, hit enter on the foot partition it set up. Hit enter on where it says "ext3." An option will come up that will let you use fs.

---

