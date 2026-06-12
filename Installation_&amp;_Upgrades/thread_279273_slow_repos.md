---
title: "slow repos"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by TSOL on 2006-10-17
i or we have got a problem about repos. the tr. repos are really really slow. we have got 1024kb adsl but we're downloading updates like 5kb/s or may be 11kb/s.

```
deb http://tr.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://tr.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://tr.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://tr.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb http://tr.archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://tr.archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://tr.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://tr.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
```

and this is the sources.list that we're using. is this a result from our sources.list or is this a general problem?

---

### Post by Kateikyoushi on 2006-10-17
You can choose another mirror from [here]("https://wiki.ubuntu.com/Archive") you should be able to find a faster one.

---

### Post by TSOL on 2006-10-17
ok thanks but when i choose one how can i edit the sources.list?
like;

deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

deb [http://sommerville.uvt.nl/ubuntu/](http://sommerville.uvt.nl/ubuntu/) dapper main restricted universe multiverse

any language problems?

---

### Post by Kateikyoushi on 2006-10-17
Yes, it should look like that, but create a backup first just in case.
There shouldn't be any language problems the mirrors contain identical data, you can download all the avaible language packages from each.

---

### Post by TSOL on 2006-10-17
thank you very much :-D

---

