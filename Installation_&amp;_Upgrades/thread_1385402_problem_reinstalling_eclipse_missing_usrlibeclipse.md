---
title: "problem reinstalling eclipse: missing /usr/lib/eclipse"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by noahlt on 2010-01-19
After uninstalling Eclipse, I deleted /usr/lib/eclipse.  When I reinstalled Eclipse, apt-get did not reinstall /usr/lib/eclipse.

In short:

```
$ sudo apt-get remove eclipse
...
$ sudo rm -rf /usr/lib/eclipse
$ rm -rf ~/.eclipse
$ rm -rf ~/workspace
$ sudo apt-get install eclipse
...
$ eclipse
/usr/bin/eclipse: 7: /usr/lib/eclipse/eclipse: not found

```

How do I get my /usr/lib/eclipse back?

---

### Post by noahlt on 2010-01-19
Solved it -- the other eclipse packages weren't getting removed, so I ran this:

```
$ sudo apt-get remove eclipse
...
$ sudo apt-get autoremove
...
$ sudo apt-get install eclipse
...
```

and now eclipse works.

---

