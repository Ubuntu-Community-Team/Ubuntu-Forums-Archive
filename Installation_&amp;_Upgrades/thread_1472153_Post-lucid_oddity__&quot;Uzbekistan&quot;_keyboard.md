---
title: "Post-lucid oddity : &quot;Uzbekistan&quot; keyboard appears"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by Jethro_uk on 2010-05-04
upgraded from Karmic to Lucid Friday. All seems OK, except I now have a "Uzb" icon in my taskbar. When I click it, it's the keyboard layout settings, which are now set to "Uzbekistan" by default.

When I remove Uzb, to leave just GB, the icon disappears.

Until I next boot up .....

Can anyone suggest a way I can prevent this ?

---

### Post by zvacet on 2010-05-04
```
sudo dpkg-reconfigure console-setup
```

and see if it works.

---

### Post by Jethro_uk on 2010-05-04
> **zvacet said:**
> ```
sudo dpkg-reconfigure console-setup
```

and see if it works.

No joy :-(

---

### Post by zvacet on 2010-05-05
See if [this]("https://help.ubuntu.com/community/LocaleConf") helps.

---

