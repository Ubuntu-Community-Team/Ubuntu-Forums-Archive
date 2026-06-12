---
title: "Help installing Wine and AIM"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Brain_of_J on 2008-10-18
I'm attempting to install AIM (as well as Wine) in 8.10
I tried following the directions for installing AIM as found on this page [link]("http://www.aim.com/get_aim/linux/latest_linux.adp#tgz2")
It turns out that the directory found in /usr/local/bin/aim was never created...
So I got the bright idea to try to install Wine to get around all of this.
I tried to use the Add/Remove Application utility and it failed...but directed me to Synaptic. I tried Synaptic and I received this error when trying to install the Wine packages...
[I]wine:
  Depends: libasound2 (>1.0.17) but 1.0.15-3ubuntu4 is to be installed[/I]

Ideas?

---

### Post by cl0ckwork on 2008-10-18
why not use pidgin?

---

### Post by perlluver on 2008-10-18
That package is outdated, it is trying to use older libraries, and I am pretty certain the AIM will not run in Wine.  You can either use Pidgin, or Kopete, both can be found in Add/Remove Programs.  Also Intrepid 8.10, is still beta, so some programs might not yet work right.

---

### Post by Brain_of_J on 2008-10-18
Ah.
Thanks.
Pidgin works just fine.

---

### Post by bapoumba on 2008-10-19
Moved to Intrepid Ibex.

---

