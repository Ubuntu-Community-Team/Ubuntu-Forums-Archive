---
title: "27 March: PYTHON IS BORKED"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by macogw on 2009-03-27
A bad Python upload went through and is causing a bunch of crashing applications.

The problem is corrected in version 2.6.1-1ubuntu5.1. Note that since Update Manager is one of the affected programs, users affected by this bug will need to upgrade using apt-get in a terminal: $ sudo apt-get update && sudo apt-get dist-upgrade

It will, however, take time before this package reaches your mirror.  You can check what version your mirror is currently offering with ```
apt-cache policy python2.6 python2.6-minimal
```

---

### Post by binbash on 2009-03-27
too late for me : )

---

### Post by taavikko on 2009-03-27
Python packages are been reverted in main repo.
So they are un-upgadable (<<-- Is that a word? )

wgrant stated while ago, thut this takes few hours to clear/fix

---

### Post by macogw on 2009-03-27
> **taavikko said:**
> Python packages are been reverted in main repo.
So they are un-upgadable (<<-- Is that a word? )

wgrant stated while ago, thut this takes few hours to clear/fix

You can force downgrade to the old working version if you still have it with:
```
sudo dpkg -i --force-downgrade <thing>.deb
```
replace the deb's name

---

