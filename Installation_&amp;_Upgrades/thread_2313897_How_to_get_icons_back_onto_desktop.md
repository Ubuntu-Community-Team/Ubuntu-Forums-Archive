---
title: "How to get icons back onto desktop"
date: 2016-02-16
forum: Installation &amp; Upgrades
---

### Post by TeaLady on 2016-02-16
Am new to Ubuntu forums.  Have an old Toshiba computer with Ubuntu on it.  Somehow lost the menu list with all my icons on it.  How can I get them back?

---

### Post by mörgæs on 2016-02-17
Hi, welcome to the fora.
Which Toshiba and which version of Ubuntu?

---

### Post by TeaLady on 2016-02-17
It's a Satellite A210 and Ubuntu is 14.04

---

### Post by grahammechanical on 2016-02-17
There are 3 commands that might help. Run them one at a time.

```
dconf reset -f /org/compiz/
setsid unity
unity --reset-icons
```

Regards

---

### Post by shane_faulkinbury2 on 2016-02-17
If you want icons on your desktop for your programs I simply go into Files/Computer and just select the magnifying glass and put in the program name and copy/paste to my desktop!  :D

---

