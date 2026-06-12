---
title: "apport-qt, ubuntu-bug don't work"
date: 2009-09-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pedrogfrancisco on 2009-09-05
I do
```
$ ubuntu-bug -p linux
```
It collects info.
Then launches no browser. Stays forever running until I kill him. It's annoying me...

Can anyone help me fixing the problem?

If not, with which package shall I fill a bug report? apport-qt or ubuntu-bug ?

---

### Post by tghe-retford on 2009-09-05
> **pedrogfrancisco said:**
> If not, with which package shall I fill a bug report? apport-qt or ubuntu-bug ?
I'm not able to launch a browser to report any bugs either. This is on an fully up to date system. I would personally report the bug under the apport package (if no-one does it, it might have to wait for a good few hours, its long past my bedtime!).

---

### Post by 23meg on 2009-09-06
[QUOTE=pedrogfrancisco]If not, with which package shall I fill a bug report? apport-qt or ubuntu-bug ?[/QUOTE]

Just "apport".

---

### Post by tghe-retford on 2009-09-06
Someone has already reported this bug, seems to have been going on and off since Alpha 3:

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/405378](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/405378)

---

### Post by pedrogfrancisco on 2009-09-06
Marked "This bug affects me too" on the bug report, suggest you all do the same.

---

### Post by pedrogfrancisco on 2009-09-13
[Apply this patch to make it work as intended.]("https://bugs.launchpad.net/ubuntu/+source/apport/+bug/405378/comments/11")

---

