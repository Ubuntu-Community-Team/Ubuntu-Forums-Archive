---
title: "licq + icqnd (gtk gui) - crashes in Feisty"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by vicnov on 2007-04-28
Hi,
after upgrading from Edgy to Feisty, licq does not work with icqnd plugin (but works with qt-gui). I tried to build both licq and icqnd from sources, but it does not help.

Has somebody succeeded with licq + icqnd in Feisty?

---

### Post by dwbmb on 2007-07-15
this plugin is unable to load existing user settings from owner.Licq and if you take u look to the error log after trying to create a new account , it says that you have to fill in Password manually. Do that. After doing that, trying add account again, it deletes the Password field and in error log is a new log that you have to fill in a Password. Even with chmod 600. i dont understand it, maybe bug.

---

### Post by Andrew Yuspin on 2007-08-12
Try this [http://rapidshare.com/files/48576107/licq-icqnd-plugin-0.2BETA-all.deb.html](http://rapidshare.com/files/48576107/licq-icqnd-plugin-0.2BETA-all.deb.html)

---

### Post by vicnov on 2007-08-12
Andrew Yuspin,
please give some comments about what it is in this link ;)

---

### Post by Andrew Yuspin on 2007-08-13
This is the ".deb", what I built for my Feisty from source ([http://icqnd.sourceforge.net/news.html](http://icqnd.sourceforge.net/news.html),  0.2BETA). It`s work for me.

---

### Post by vicnov on 2007-08-13
> **Andrew Yuspin said:**
> This is the ".deb", what I built for my Feisty from source ([http://icqnd.sourceforge.net/news.html](http://icqnd.sourceforge.net/news.html),  0.2BETA). It`s work for me.

I will try it, thanks !

---

### Post by vicnov on 2007-08-27
**Andrew Yuspin**,
thanks, it works! I do not understand why it did not work when I built from sources...

---

