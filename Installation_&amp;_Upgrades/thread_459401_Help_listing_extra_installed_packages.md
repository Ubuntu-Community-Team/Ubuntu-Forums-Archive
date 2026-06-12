---
title: "Help listing extra installed packages"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by accuser on 2007-05-30
I want to produce a list of the packages that were installed on our server (6.06) after the initial install (hopefully, flagging upgrades and new installations differently). Is this possible using ```
dpkg
``` or another tool? I can't seem to find anything that will help...

Thanks in advance,
Matthew

---

### Post by hoheszeh on 2007-05-31
> **accuser said:**
> I want to produce a list of the packages that were installed on our server (6.06) after the initial install (hopefully, flagging upgrades and new installations differently). Is this possible using ```
dpkg
``` or another tool? I can't seem to find anything that will help...

Thanks in advance,
Matthew

If i understand you correctly you want a "snapshot" of installed software on a system in a text-file which you could hand over to apt to reinstall all these? If so, this might help:

to create the list
```
COLUMNS=200 dpkg-query -W --showformat='${Package}\n' > packages.list
```

to hand the list over to apt-get
```
cat packages.list | xargs apt-get -y install
```

remove the "-y" if you want apt-get to ask you if it should proceed.

---

