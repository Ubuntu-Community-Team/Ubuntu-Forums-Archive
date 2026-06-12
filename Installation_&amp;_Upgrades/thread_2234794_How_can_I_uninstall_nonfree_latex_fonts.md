---
title: "How can I uninstall nonfree latex fonts?"
date: 2014-07-17
forum: Installation &amp; Upgrades
---

### Post by coverup1128 on 2014-07-17
I would like to uninstall the classico font for texlive, which I installed using getnonfreefonts-sys on my Ububtu 14.04 laptop.  Can somebody please guide me through the uninstall procedure?

Thanks

---

### Post by ajgreeny on 2014-07-17
How exactly did you install them, and where are they now sitting in your system?

---

### Post by coverup1128 on 2014-07-18
I installed the font using these commands (not necessarily in this order)

[B]$ sudo getnonfreefonts-sys classico --verbose
$ sudo update-updmap
$ sudo updmap-sys
$ texhash
[/B]
It looks like the first command installed bunch of files in /usr/local/share/texmf, but I am not certain whether that was all it did.

---

### Post by coverup1128 on 2014-07-21
Anyone?

---

