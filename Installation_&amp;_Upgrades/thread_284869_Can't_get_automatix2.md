---
title: "Can't get automatix2"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by riddlermarc on 2006-10-26
For some reason when I try to install automatix2, it comes up with:

"E: Couldn't find package automatix2"

My sources.list:

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

Any ideas, please? I'm using 6.06 AMD64 and I know it worked on a different install yesterday :confused:

---

### Post by taurus on 2006-10-26
Why don't you head over to [http://www.getautomatix.com/](http://www.getautomatix.com/) and download it yourself!  ;)

---

### Post by riddlermarc on 2006-10-26
> **taurus said:**
> Why don't you head over to [http://www.getautomatix.com/](http://www.getautomatix.com/) and download it yourself!  ;)That's the thing, I followed the install instructions from the site but no joy :confused:

---

### Post by taurus on 2006-10-26
Did you remember to run the update first after you modified your /etc/apt/sources.list?

```
sudo aptitude update
```

---

### Post by riddlermarc on 2006-10-26
Yep, I followed the installation guide to the letter but no joy.. it has me stumped! Now when I run a refresh in Synaptic I get failures:

[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Bad header line [IP: 195.248.90.23 80]
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Bad header line [IP: 195.248.90.23 80]
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) Got a single header line over 360 chars [IP: 195.248.90.23 80]
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz)
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz)
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-amd64/Packages.gz)
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.gz)
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-amd64/Packages.gz)
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-amd64/Packages.gz)

Can I change these so they *don't* point to a gb server and if so, tho which server?

Thanks :)

---

### Post by taurus on 2006-10-26
Yes, edit your /etc/apt/sources.list and remove the gb!  Then, don't forget to run the update again...

---

### Post by riddlermarc on 2006-10-26
> **taurus said:**
> Yes, edit your /etc/apt/sources.list and remove the gb!  Then, don't forget to run the update again...Thanks, that fixed the errors but I still don't get automatix2.. is there anywhere I can actually download it from, rather than using apt-get?

Go easy on me, I'm a looooong time RH/Fedora user so that transition to Ubuntu is taking a little working on!

---

