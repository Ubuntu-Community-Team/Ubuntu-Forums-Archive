---
title: "Sources.list is corrupt!"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by suyash01 on 2010-10-11
Hi,
I am getting this error when I run update manager or Software centre:
---------------------------
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'src' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-maverick.list'
--------------------------
Please guide me as to how to fix this issue.

---

### Post by ibuclaw on 2010-10-11
I suppose if you are going to insert ppas into your software sources list, then you get what you ask for. ;)

```
sudo rm /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-maverick.list
```
Is there any reason why you want the mozilla-daily builds?

---

### Post by suyash01 on 2010-10-11
Hi,
thanks that worked. But I tried removing that entry from Software sources and it didn't work.
And I wanted to install mozilla daily ppa to get firefox 4. It worked fine in 10.04.
Thank again.
-Suyash

---

