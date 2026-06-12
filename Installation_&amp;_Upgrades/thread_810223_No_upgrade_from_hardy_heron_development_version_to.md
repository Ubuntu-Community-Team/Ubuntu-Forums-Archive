---
title: "No upgrade from hardy heron development version to 8.04LTS?"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by grayFalcon on 2008-05-28
Hello everybody!

I couldn't wait for 8.04, so I installed the development version a two moths back or so. Now this worked quite fine, but when 8.04 was finally released, the updates stopped coming for me. I tried a few things from the forums, none worked, but maybe this might be a hint that somebody might understand?

> 
> gksu do-release-upgrade
Checking for a new ubuntu release
current dist not found in meta-release file
No new release found


So... any ideas what I could do to get to 8.04 LTS?

Thanks a lot in advance,
-grayFalcon

---

### Post by nzadLithium on 2008-05-28
cat /etc/apt/sources.list
post output here please.

---

### Post by grayFalcon on 2008-05-28
Pretty much the standard stuff...

> 
> cat /etc/apt/sources.list | grep -v "#" | grep -v -e "^$"
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb [http://de.packages.medibuntu.org/](http://de.packages.medibuntu.org/) hardy free non-free


---

### Post by nzadLithium on 2008-05-29
try adding

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates main restricted multiverse universe

and 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted multiverse universe

and if you want to
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe

---

