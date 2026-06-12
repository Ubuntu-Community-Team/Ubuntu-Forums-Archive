---
title: "New Updates: bug against the 'update-manager' ??"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by Ms.Kai on 2008-02-29
As of late last night I can not retrieve updates or install any new software.

I am receiving the following error message consistently....

Now what do I do?  Or will this problem go away?  


A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Read error - read (5 input/output error),E:The package lists or status file could not be parsed or opened.'

I am on Ubuntu 7.04

- Ms.  Kai

---

### Post by taurus on 2008-02-29
If you have an update-manager window open, close it first.  Then, open a terminal and run these two commands and see what happens.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Ms.Kai on 2008-02-29
Hiya Taurus,

Thanks for your post.

I tried the sudo apt-get update and it looks like everything updated.

The update icon in the upper right corner has now gone away.

Thanks!

Ms.Kai:popcorn:

---

