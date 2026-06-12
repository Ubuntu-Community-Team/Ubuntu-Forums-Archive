---
title: "Update from Beta to LTS"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Grobbendonk on 2010-04-30
Apologies for asking such a daft question, I seem to be incapable of constructing a useful search phrase for this one...

What's the procedure for updating from Lucid Beta 2 to Lucid LTS?

Is it just "apt-get upgrade"?  Or would I be better off with a clean install?  

Assuming the machine has been used, software added via apt from standard repos, but not really tinkered with heavily.

---

### Post by Aearenda on 2010-04-30
```
sudo apt-get dist-upgrade
```This is the way I did it.

A clean install is only needed if you have serious problems already. Take a backup first!

---

### Post by Grobbendonk on 2010-04-30
Just what i needed to know!  Thank you.  I'd managed to miss that everywhere.

Backups are a part of my life, after a salutory lesson 20 years ago...

---

