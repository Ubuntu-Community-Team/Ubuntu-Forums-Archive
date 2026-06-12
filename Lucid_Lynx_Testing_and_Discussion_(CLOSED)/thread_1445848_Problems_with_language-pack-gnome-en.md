---
title: "Problems with language-pack-gnome-en"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by stardustdk on 2010-04-03
Hey.

I was trying to upgrade, both using GUI and aptitude safe-upgrade.

With aptitude, I tried to install, reinstall and remove ```
language-pack-gnome-en
``` because is supposed to be a package with problems.

Whatever i tried, inkluding > dpkg --configure -a etc., nothing worked :(.

Now I can't upgrade packages because of language-pack-gnome-en

Any idea besides reinstall the beta1?

Best regards

Stardustdk

---

### Post by dino99 on 2010-04-03
if you can use synaptic, searcf for language and select theses you need/want but english might be installed because its widly used.

look at broken package, dependencies if you have

sudo apt-get autoremove
sudo apt-get install -f

be sure there is no error into sources.list ( no ppa, no third party, only lucid) and using main server (never heard about en packages trouble)

sudo apt-get update

---

### Post by stardustdk on 2010-04-03
I didn't help...

Hrmm ... :(

Best regards

---

### Post by stardustdk on 2010-04-04
Did make a fresh install of Beta1 (I386), and updated. All is working now.

---

