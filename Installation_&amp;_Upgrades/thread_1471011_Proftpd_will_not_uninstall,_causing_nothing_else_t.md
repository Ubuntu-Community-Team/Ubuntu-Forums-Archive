---
title: "Proftpd will not uninstall, causing nothing else to install"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by stevo81989 on 2010-05-03
So I have searched around the internet and no one has a usable answer. Hoping someone can help me. I am trying to uninstall proftp because it wont let me install anything else. It keeps erroring out with the following status:


Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  proftpd-basic
0 upgraded, 0 newly installed, 1 to remove and 40 not upgraded.
1 not fully installed or removed.
After this operation, 1798kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 59291 files and directories currently installed.)
Removing proftpd-basic ...
/var/lib/dpkg/info/proftpd-basic.postrm: 8: update-inetd: not found
dpkg: error processing proftpd-basic (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 proftpd-basic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas??

---

### Post by wojox on 2010-05-03
Try reinstalling it:

```
sudo aptitude --reinstall install proftpd-basic
```

---

### Post by stevo81989 on 2010-05-03
Wow! I cant believe after all of the research that it was that easy! Thanks so much! Also just so you know the aptitude wouldnt register so I tried:

```
 sudo apt-get --reinstall install proftpd-basic

```

Just for future reference. Thanks for all your help!

---

### Post by wojox on 2010-05-03
Your welcome.

---

