---
title: "Repository Problems - bzip2?"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by richfeat on 2008-02-14
I have 2 Dapper and 3 Feisty loaded machines, and all are failing to update most of the time. It has been happening for a few months - hard to believe I am trying an update during repo updates EVERY time. Different number of failures each time. On cable broadband connection.
Typical messages:
[http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) Sub-process gzip returned an error code (1)

Dapper sources:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

Anyone know what is going on?

---

### Post by Pumalite on 2008-02-14
Have you tried changing Server?

---

### Post by richfeat on 2008-02-15
I have just tried substituting (from the mirror list)
archive.ubuntu.com
in place of gb.archive.ubuntu.com and security.ubuntu.com
and also tried 
[www.mirrorservice.org/sites/archive.ubuntu.com](www.mirrorservice.org/sites/archive.ubuntu.com)
The mirrors look OK and complete in a browser, but I get (extracts):

Get: 18 [http://www.mirrorservice.org](http://www.mirrorservice.org) dapper-updates/restricted Packages [6356B]                         
Ign [http://www.mirrorservice.org](http://www.mirrorservice.org) dapper-updates/restricted Packages                                     
Errhttp://www.mirrorservice.org dapper/restricted Packages                                              
  416 Unknown [IP: 212.219.56.138 80]

Get: 37 [http://www.mirrorservice.org](http://www.mirrorservice.org) dapper-updates/restricted Packages [6343B]                         
97% [37 Packages gzip 0] [Waiting for headers]                                                231kB/s 0s
gzip: stdin: not in gzip format
Errhttp://www.mirrorservice.org dapper-updates/restricted Packages                                      
  Sub-process gzip returned an error code (1)

Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  416 Unknown [IP: 212.219.56.138 80]

Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)

... and many similar.

---

### Post by zvacet on 2008-02-15
They work for me.In case that your connection is O.K. are you sure that you removed # in front of every line wich start with deb.Even better

```
cat /etc/apt/sources.list
```

---

### Post by zvacet on 2008-02-15
Sorry,I overlooked that you posted source list allready.I tried every line in your source list and they work for me.Did you try to refresh with 


```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by richfeat on 2008-02-16
I was only doing the the update there. The Updates GUI had been bombing out after the "Check".

Now however (after changing the server following your suggestion), even though I still get 4 zip/bzip2 error messages, I can do an upgrade. At least I have a partially up-to-date system.
But I get the feeling this is luck rather than judgement.

I am wondering about your comment "assuming the connection is OK". I am connecting through a server with danguardian running.
I seem to be able to look at the repo servers through a browser OK, but I suppose it would be worth trying with danguardian out of the loop.

---

