---
title: "edgy upgrade failure - failed to fetch"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by billh1241 on 2006-10-27
upgrade does not work get error;

failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/) Sources.gz Sub-process gzip returned an error code (1)

Please help if  you can.  thanks

---

### Post by Andrew1234 on 2006-10-27
I had the same problem I think its because so many people are downloading at once, keep retrying and it will download all the new files.

---

### Post by Nightingale on 2006-10-27
Same problem here, but I get this message:
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-amd64/Packages.bz2) &#1055;&#1086;&#1088;&#1086;&#1078;&#1076;&#1105;&#1085;&#1085;&#1099;&#1081; &#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089; bzip2 &#1074;&#1077;&#1088;&#1085;&#1091;&#1083; &#1082;&#1086;&#1076; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080; (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz) &#1055;&#1086;&#1088;&#1086;&#1078;&#1076;&#1105;&#1085;&#1085;&#1099;&#1081; &#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089; gzip &#1074;&#1077;&#1088;&#1085;&#1091;&#1083; &#1082;&#1086;&#1076; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080; (1)

---

### Post by BackInTimeMan on 2006-10-27
> **billh1241 said:**
> upgrade does not work get error;

failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/) Sources.gz Sub-process gzip returned an error code (1)

Please help if  you can.  thanks

Not sure which method you're using to update but you have "Dapper" in your URL, it shopuld be "Edgy".

---

### Post by raul_ on 2006-11-20
> **BackInTimeMan said:**
> Not sure which method you're using to update but you have "Dapper" in your URL, it shopuld be "Edgy".

Not using the update manager...i'm getting that error too. any solutions, or should i just keep trying?

---

### Post by raul_ on 2006-11-20
turns out i had a problem with my repo's list. I copied/pasted a new one, and now it's working. Just in case, i used the psychocats page list

---

### Post by BackInTimeMan on 2006-11-21
> **raul_ said:**
> turns out i had a problem with my repo's list. I copied/pasted a new one, and now it's working. Just in case, i used the psychocats page list

Glad you got it sorted  :)

---

