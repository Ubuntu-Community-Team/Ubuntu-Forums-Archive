---
title: "update a program"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by dmsn on 2007-02-28
Hey i want to update lftp with apt-get but it doesn't work so good.


dmsn@laptop:~$ lftp -v
LFTP | Version 3.5.0 | Copyright (c) 1996-2006 Alexander V. Lukyanov

LFTP is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
There is absolutely no warranty for LFTP.  See COPYING for details.

Send bug reports and questions to <lftp@uniyar.ac.ru>.

Libraries used: Readline 5.1, GnuTLS 1.4.0, zlib 1.2.3
dmsn@laptop:~$ 

I know there is a newer version than this... i know i can install it manuell but i want to know how to update
programs/tools with apt-get :D

Thanks for help.

---

### Post by taurus on 2007-02-28
If the latest version is not in the repos, then you have to upgrade (install) it by hand then.

---

### Post by dmsn on 2007-02-28
Oki thanks.
Another question how can i list all programs i installed with apt-get?

---

### Post by zvacet on 2007-02-28
All programs you installed with apt-get or synaptic are in var/cache/apt/archives

---

