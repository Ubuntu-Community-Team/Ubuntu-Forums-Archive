---
title: "help in DCTC installation plz!!"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by 4uvak91 on 2008-07-24
i'm trying to configurate but I stuck on this.....

...checking for libgcrypt-config... yes
checking gcrypt version... 1.2.4
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking db.h usability... no
checking db.h presence... no
checking for db.h... no
configure: error: BerkeleyDB include required.

i'm noob ubuntu user....so plz help me out!!

---

### Post by Pumalite on 2008-07-24
I hope you have build-essential installed

---

### Post by 4uvak91 on 2008-07-24
i have it already

---

### Post by Pumalite on 2008-07-24
[http://ubuntuforums.org/showthread.php?t=5211](http://ubuntuforums.org/showthread.php?t=5211)

---

### Post by 4uvak91 on 2008-07-24
tyvm dude...i'll tyr this

---

### Post by 4uvak91 on 2008-07-24
well configuration succeeded but at the end of the "make" things soped again...
....user_manage.c:47: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: static declaration of &#8216;hub_user_xtra_info&#8217; follows non-static declaration
user_manage.h:30: error: previous declaration of &#8216;hub_user_xtra_info&#8217; was here
user_manage.c:50: error: static declaration of &#8216;hub_user_uinfo&#8217; follows non-static declaration
user_manage.h:34: error: previous declaration of &#8216;hub_user_uinfo&#8217; was here
make[2]: *** [user_manage.o] error 1
make[2]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/home/ilja91/dctc-0.85.9/src'
make[1]: *** [all-recursive] error 1
make[1]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/home/ilja91/dctc-0.85.9'
make: *** [all] error 2

itranslated some words...i have russian ubuntu

---

### Post by 4uvak91 on 2008-07-25
helloo???

---

