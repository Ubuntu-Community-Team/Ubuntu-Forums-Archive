---
title: "after upgrade xfce panel is empty"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by Georges on 2006-06-29
it's not really acceptable that my nice xfce panel is reduced to nothing after upgrading to dapper. Anyone else experienced this behaviour?
The internal structure of the panel's XML file has changed.
From a serious distribution I would expect an automatic migration tool which would convert the file. But no, "it's just not working (tm)"

Perhaps such a tool exists but it did not run because this was originally an ubuntu-desktop and not xubuntu-desktop?

Georges

---

### Post by aysiu on 2006-06-29
If you had the *xubuntu-desktop* metapackage installed before you upgraded, the upgrade *should* have gone smoothly.

---

### Post by Georges on 2006-06-29
hmm,

that could be my problem. Is there some way to get this update to convert the file manually or is that far too well hidden in the install scripts?

Georges

---

### Post by aysiu on 2006-06-29
I don't know. You could try this and see if it works: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

---

