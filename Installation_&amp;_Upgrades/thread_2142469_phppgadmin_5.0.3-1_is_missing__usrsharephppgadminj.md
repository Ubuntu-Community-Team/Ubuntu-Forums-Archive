---
title: "phppgadmin 5.0.3-1 is missing  /usr/share/phppgadmin/js/ directory"
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by qst on 2013-05-05
Package: phppgadmin
 Version: 5.0.3-1
 Architecture: all
 
I installed phppgadmin and everything seems to work ok. There are however error messages that appear in the logs due to missing javascript files. It seems that the entire **/usr/share/phppgadmin/js/** folder is not found.

I did a [COLOR=#b22222]*dpkg --contents /var/cache/apt/archives/phppgadmin_5.0.3-1_all.deb*[/COLOR] to check and I could not see any references to it, so they are not included in the package

A temporary solution was to copy the files manually from [https://github.com/phppgadmin/phppgadmin/tree/master/js](https://github.com/phppgadmin/phppgadmin/tree/master/js) but it would be nice to have them included in the standard repository.

---

