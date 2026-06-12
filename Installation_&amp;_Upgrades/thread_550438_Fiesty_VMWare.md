---
title: "Fiesty VMWare"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by steveneddy on 2007-09-13
Maybe I'm beating a dead horse here - but I recently tried to DL and install the new VMWare server from the repos and it still won't launch. It tries, but it never launches.

I totally uninstalled all of the references to vmware on the machine, and it installs, but still won't run.

I wonder what I'm doing wrong?

---

### Post by Pumalite on 2007-09-13
I'm not sure is the answer, but you might want to try:
Code:

rm -f /bin/sh 
ln -s /bin/bash /bin/sh

and try again.

---

### Post by steveneddy on 2007-09-13
> **Pumalite said:**
> I'm not sure is the answer, but you might want to try:
Code:

rm -f /bin/sh 
ln -s /bin/bash /bin/sh

and try again.

What does this do?

please

:)

---

### Post by Pumalite on 2007-09-13
[http://www.howtoforge.com/forums/showthread.php?t=11088](http://www.howtoforge.com/forums/showthread.php?t=11088)

---

### Post by steveneddy on 2007-09-13
cool - worked

---

### Post by Pumalite on 2007-09-13
No problema.

---

### Post by steveneddy on 2007-09-14
so - um - what actually does this do?

I'm too lazy to search google.

---

### Post by Pumalite on 2007-09-14
Beats me; I researched it just for you. But I'm also lazy.

---

### Post by steveneddy on 2007-09-16
Well then, I thank you very much.

---

### Post by Pumalite on 2007-09-16
You are most welcomed. Any time.

---

