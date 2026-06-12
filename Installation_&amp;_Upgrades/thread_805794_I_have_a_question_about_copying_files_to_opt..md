---
title: "I have a question about copying files to /opt."
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by lichaoir on 2008-05-24
I want to install firefox 2.0, so I downloaded it, and then when I was copying to /opt directory, it raise something like this:

I executed: sudo cp -f firefox /opt
The terminal said: cp: omitting directory `firefox'

Why? And how can I fix it?

Thanks for your discussion and answer!

---

### Post by unutbu on 2008-05-24
```
sudo cp -R firefox /opt
```
-R means: copy directories recursively

without -R, cp will only copy files.

---

