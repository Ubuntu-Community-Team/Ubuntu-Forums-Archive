---
title: "silent crashes locked"
date: 2010-02-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dino99 on 2010-02-27
every week i check /var/crash and find there few crashes with root rights: all about linux-image, _usr_sbin, _usr_share. These crashes have not been reported by apport and i can't report them because they are locked.

I find few others too that have not been reported but are not locked: all about _usr_bin, _usr_lib

Dont know how to bypass these locked crashes. My system is a clean install of A1 then daily updated. Am i alone with this problem ?

---

### Post by VMC on 2010-02-27
> **dino99 said:**
> every week i check /var/crash and find there few crashes with root rights: all about linux-image, _usr_sbin, _usr_share. These crashes have not been reported by apport and i can't report them because they are locked.

I find few others too that have not been reported but are not locked: all about _usr_bin, _usr_lib

Dont know how to bypass these locked crashes. My system is a clean install of A1 then daily updated. Am i alone with this problem ?

The only crash in mine is one that should be there, Aptitude.
Also, look at the date. how long ago did these occur?

Use Log viewer and apport.log

Here's how to review them:
gksu nautilus, then open one of the files under Apport and then expand Contents of the report.

---

### Post by dino99 on 2010-02-27
thanks VMC,
they are 2 days back. i'm just wondering and surprised that crashes can be root owned, something strange to me.
anyway, i've changed the rights on these files to be able to report them. Curiously there is a lot crashes not automaticaly reported by apport: so does apport consider these crashes as minor or already known ? but that's seem abnormal.

---

