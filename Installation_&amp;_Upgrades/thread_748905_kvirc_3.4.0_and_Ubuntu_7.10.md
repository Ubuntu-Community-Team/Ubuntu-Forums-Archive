---
title: "kvirc 3.4.0 and Ubuntu 7.10"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by Wag on 2008-04-07
I downloaded kvirc from the site. The one titled "Source package (all the platforms)"
I have QT, perl, zlib, and automake all installed.

I extracted the file then in the terminal typed 

sudo su "rootpass"
./configure

everything up and until this point was just fine; no errors.

then 

make install

and got the errors listed below  


 
make[3]: *** [install-tmpDATA] Error 1
make[3]: Leaving directory `/home/me/kvirc-3.4.0/data/protocols'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/me/kvirc-3.4.0/data/protocols'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/me/kvirc-3.4.0/data'
make: *** [install-recursive] Error 1




any help would be great!

---

