---
title: "Package held back after dist-upgrade"
date: 2014-12-18
forum: Installation &amp; Upgrades
---

### Post by paulathomas on 2014-12-18
Linux version: xubuntu 14.10 (also happened on 14.04)

first I did:

 sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libdevhelp-3-2
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.

Then, noticing the held back package I did:


sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libdevhelp-3-2
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade


What is happening? Why is this package not coming down?

---

### Post by sudodus on 2014-12-18
Because some package that it needs is still missing (there is probably an older version of that package, but the kept-back package waits for a newer version, that should arrive in the near future).

---

### Post by Bucky Ball on 2014-12-18
Welcome. Presuming you did:

```
sudo apt-get update
sudo apt-get upgrade
```

... prior to:
```

sudo apt-get dist-upgrade
```

? Might be a silly question, but thought I'd ask. ;)

---

### Post by paulathomas on 2014-12-18
Sudodus: Thanks - I'll just wait.

Bucky Ball: In computing there is no such thing as a stupid question,  but yes I did.

---

### Post by Bucky Ball on 2014-12-18
> **paulathomas said:**
> 

Bucky Ball: In computing there is no such thing as a stupid question,  but yes I did.

+1. ;)

---

### Post by vasa1 on 2014-12-18
Paula, could you please post the output from
`apt-cache policy libdevhelp-3-2` between code tags?

On my system, Lubuntu 14.04, I see```
08:14 AM ~ $ apt-cache policy libdevhelp-3-2
libdevhelp-3-2:
  Installed: (none)
  Candidate: 3.8.2-2ubuntu1
  Version table:
     3.8.2-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
08:14 AM ~ $
```

---

### Post by paulathomas on 2014-12-19
Output from apt-cache policy:

```

libdevhelp-3-2:
  Installed: 3.8.2-2ubuntu1
  Candidate: 3.12.1-1
  Version table:
     3.12.1-1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages
 *** 3.8.2-2ubuntu1 0
        100 /var/lib/dpkg/status


```

---

