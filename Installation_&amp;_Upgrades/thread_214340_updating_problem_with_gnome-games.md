---
title: "updating problem with gnome-games"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by marko83 on 2006-07-12
sudo dpkg --configure -a
Setting up gnome-games-data (2.14.2-0ubuntu1) ...
/usr/share/gconf/schemas/glines.schemas:2017: parser error : Specification mandate value for attribute gry
        <short.Punktacja gry</short>
                            ^
/usr/share/gconf/schemas/glines.schemas:2017: parser error : attributes construct error
        <short.Punktacja gry</short>
                            ^
/usr/share/gconf/schemas/glines.schemas:2017: parser error : Couldn't find end of Start Tag short.Punktacja line 2017
        <short.Punktacja gry</short>
                            ^
/usr/share/gconf/schemas/glines.schemas:2017: parser error : Opening and ending tag mismatch: locale line 2016 and short
        <short.Punktacja gry</short>
                                    ^
/usr/share/gconf/schemas/glines.schemas:2019: parser error : Opening and ending tag mismatch: schema line 1800 and locale
      </locale>
               ^
/usr/share/gconf/schemas/glines.schemas:2110: parser error : Opening and ending tag mismatch: schemalist line 3 and schema
      </schema>
               ^
/usr/share/gconf/schemas/glines.schemas:2716: parser error : Opening and ending tag mismatch: gconfschemafile line 1 and schemalist
  </schemalist>
               ^
/usr/share/gconf/schemas/glines.schemas:2718: parser error : Extra content at the end of the document
</gconfschemafile>
^
dpkg: error processing gnome-games-data (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-games:
 gnome-games depends on gnome-games-data (= 1:2.14.2-0ubuntu1); however:
  Package gnome-games-data is not configured yet.
dpkg: error processing gnome-games (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-games-data
 gnome-games



I got this problem after I installed ubuntu linux 6.06 and updated it with 131 files or smth and I got this problem with gnome-games when I was updating new ubuntu 6.06. I dont know what it means cause im a new user in linux. Can someone help me?

---

### Post by marko83 on 2006-07-12
E: gnome-games-data: subprocess post-installation script returned error exit status 1
E: gnome-games: dependency problems - leaving unconfigured


I got this message too when trying to re-install gnome-games-data

---

### Post by marko83 on 2006-07-13
Am I the only one with this problem which occurred during updating the ubuntu 6.06?

---

