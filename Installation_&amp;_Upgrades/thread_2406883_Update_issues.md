---
title: "Update issues"
date: 2018-11-27
forum: Installation &amp; Upgrades
---

### Post by 89vivipatata+90willy on 2018-11-27
Hi guys, I was doing an update and Ubuntu just went crazy, I can't understand what's happened I need some help. I can post some photos of desktop and setting panel is not anymore the same and can't connect to wireless. Please help

---

### Post by QIII on 2018-11-27
Hello!

It would certainly be helpful if you would describe your issue in detail and provide whatever information you can so others can help.  He more information you give, the better we can help.

You haven't given us much to work with.

---

### Post by Impavidus on 2018-11-27
That's not a lot to go by. Try to describe exactly what went wrong. A picture may indeed help. Also tell us what version of Ubuntu you're using (16.04, 18.04, ...) and what flavour (regular Ubuntu, Xubuntu, ...). To get a list of recently upgraded packages, try```
grep upgrade /var/log/dpkg.log | grep 2018-11-2
```That will scan the log file for upgraded packages in the past 8 days. As you told us this happened after an update, it may give us a hint. Do you remember anything peculiar about that update? Maybe something about a partial update or some error message.

---

