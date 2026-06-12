---
title: "Can't upgrade 12.04.1 LTS 64bit because of a apport package"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by DocFunfrock on 2013-04-26
I tried 

apt-get autoclean
apt-get clean
apt-get update
 
and got the message

```

The following packages have unmet dependencies:
 apport : Depends: python-apport (>= 2.0.1-0ubuntu17.2) but 2.0.1-0ubuntu17.1 is installed

```

What can I do with this problem?

---

### Post by plucky on 2013-04-26
> **DocFunfrock said:**
> I tried 

apt-get autoclean
apt-get clean
apt-get update
 
and got the message

```

The following packages have unmet dependencies:
 apport : Depends: python-apport (>= 2.0.1-0ubuntu17.2) but 2.0.1-0ubuntu17.1 is installed

```

What can I do with this problem?
 ```
sudo apt-get install -f
```

Do you have the precise-updates repository enabled? It is in the updates tag in Software Sources.

---

### Post by DocFunfrock on 2013-04-26
I've the precise updates enabled. But when I run 

apt-get install -f 


I get

```
Unpacking replacement python-apport ...
dpkg: error processing /var/cache/apt/archives/python-apport_2.0.1-0ubuntu17.2_all.deb (--unpack):
 trying to overwrite '/etc/apport/crashdb.conf.d', which is also in package apport-hooks-medibuntu 2
Errors were encountered while processing:
 /var/cache/apt/archives/python-apport_2.0.1-0ubuntu17.2_all.deb


```

---

