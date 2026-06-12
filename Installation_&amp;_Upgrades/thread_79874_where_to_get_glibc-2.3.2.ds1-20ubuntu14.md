---
title: "where to get glibc-2.3.2.ds1-20ubuntu14?"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by MblKiTA on 2005-10-21
[PHP]root@nikita:/home/mblkita # apt-get install locales
...
The following packages have unmet dependencies:
  locales: Depends: glibc-2.3.2.ds1-20ubuntu14
E: Broken packages[/PHP]

where to get this glibc-2.3.2.ds1-20ubuntu14 ?

---

### Post by MblKiTA on 2005-10-22
up

---

### Post by Xian on 2005-10-22
Doesn't Ubuntu use the libc6 nomenclature?
Look [Here](http://ftp.acc.umu.se/ubuntu/pool/main/g/glibc/).

---

### Post by MblKiTA on 2005-10-23
[QUOTE=Xian]Doesn't Ubuntu use the libc6 nomenclature?
Look [Here](http://ftp.acc.umu.se/ubuntu/pool/main/g/glibc/).[/QUOTE]
yes, it does and i`ve got libc6 2.3.5-4 installed but still have this problem with glibc... :( :( :(

which package (and where) do i need to download to fix this problem:

> 
root@nikita:/home/mblkita/downloads # dpkg -i locales_2.3.5-1ubuntu12_all.deb
(Reading database ... 58865 files and directories currently installed.)
Preparing to replace locales 2.3.5-1ubuntu12 (using locales_2.3.5-1ubuntu12_all.deb) ...
Unpacking replacement locales ...
dpkg: dependency problems prevent configuration of locales:
 locales depends on glibc-2.3.5-0ubuntu1; however:
  Package glibc-2.3.5-0ubuntu1 is not installed.
dpkg: error processing locales (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 locales



---

### Post by MblKiTA on 2005-10-31
up

---

