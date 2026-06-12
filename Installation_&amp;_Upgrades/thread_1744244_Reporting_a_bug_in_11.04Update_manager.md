---
title: "Reporting a bug in 11.04/Update manager"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by xic816 on 2011-04-30
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

---

### Post by sikander3786 on 2011-04-30
Not much of a bug I guess. All you need to do is to refresh your repository index.

Applications > Accessories > Terminal:

```
sudo apt-get update
```

Then try update manager again.

---

### Post by xic816 on 2011-04-30
> **sikander3786 said:**
> Not much of a bug I guess. All you need to do is to refresh your repository index.

Applications > Accessories > Terminal:

```
sudo apt-get update
```Then try update manager again.

nop, dosnt work.
I had this problem before aswell; 

[http://ubuntuforums.org/showthread.php?t=1741726](http://ubuntuforums.org/showthread.php?t=1741726)

and now it's back... -_-

---

