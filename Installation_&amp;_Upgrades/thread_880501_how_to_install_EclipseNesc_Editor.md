---
title: "how to install Eclipse/Nesc Editor ?"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by psundar on 2008-08-05
Hi,


How to install eclipse along with nesc plugin ?
If its performance is very slow, can anyone point to any other good nesc editor installable?  

Thanks,
psundar

---

### Post by tinny on 2008-08-05
> **psundar said:**
> Hi,


How to install eclipse along with nesc plugin ?
If its performance is very slow, can anyone point to any other good nesc editor installable?  

Thanks,
psundar

Ive never used nesc, but I have used Eclipse alot on Ubuntu.

It is available in the Ubuntu repositories.

1. Enable "universe" and "multiverse" repository.
2. Install Sun Java 6 JDK (optional but I would REALLY recommend it!)

```

sudo apt-get clean
sudo apt-get update
sudo apt-get sun-java6*

```

3. Install Eclipse...

```

sudo apt-get clean
sudo apt-get update
sudo apt-get install eclipse

```

EDIT: Here is a guide to setting up an [Eclipse nesc plug-in]("http://www.dcg.ethz.ch/~rschuler/installation.htm").

---

### Post by psundar on 2008-08-07
thanks.. I was able to install eclipse and then the nesc plug-in is available at
[http://nxtmote.sf.net/nescdtupdate](http://nxtmote.sf.net/nescdtupdate)

psundar
p.s
For those who wants to install python too, it can be found at
[http://pydev.sourceforge.net/updates/](http://pydev.sourceforge.net/updates/)

---

