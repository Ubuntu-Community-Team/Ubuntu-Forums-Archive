---
title: "package manager error"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by terranz on 2006-09-13
Please help with this I'm lost.  I get this error when trying to update my lists.

```
W: Duplicate sources.list entry http://archive.ubuntu.com dapper-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com dapper-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com dapper-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_binary-i386_Packages)
```

---

### Post by Jussi Kukkonen on 2006-09-13
Well, apt seems to be telling you you have duplicate entries in your sources.list... If you paste the contents of the file here, we'll see.

---

### Post by terranz on 2006-09-16
Sorry I was so late. I had to go to an island and plant trees.

Error

```
W: Duplicate sources.list entry http://nz.archive.ubuntu.com dapper/main Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry http://nz.archive.ubuntu.com dapper/restricted Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://nz.archive.ubuntu.com dapper/universe Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
```

Sources.list
```
deb http://nz.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://packages.freecontrib.org/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb http://nz.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://nz.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nz.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nz.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
#
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
deb http://archive.canonical.com/ubuntu dapper-commercial main
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free

```

---

### Post by terranz on 2006-09-22
:arrow: bump ](*,)

---

### Post by randell6564 on 2006-09-22
> **terranz said:**
> Sorry I was so late. I had to go to an island and plant trees.

GOD MAN! Where can I do that?! I'm SO sorry that you "HAD" to "go" to an island..."! LOL!

Give me an "island" to "GO" to, and I'll tell YOU that Christ has come back and I am in Heaven!

---

### Post by terranz on 2006-09-25
It was a team building thing from work - A big portion of the IT dept went here

[http://www.motuihe.org.nz/](http://www.motuihe.org.nz/)
[http://www.doc.govt.nz/Explore/001~Other-Places/002~Auckland/Motuihe-Recreation-Reserve.asp](http://www.doc.govt.nz/Explore/001~Other-Places/002~Auckland/Motuihe-Recreation-Reserve.asp)

30 minutes ferry from the city.

---

### Post by randell6564 on 2006-09-25
> **terranz said:**
> It was a team building thing from work - A big portion of the IT dept went here

[http://www.motuihe.org.nz/](http://www.motuihe.org.nz/)
[http://www.doc.govt.nz/Explore/001~Other-Places/002~Auckland/Motuihe-Recreation-Reserve.asp](http://www.doc.govt.nz/Explore/001~Other-Places/002~Auckland/Motuihe-Recreation-Reserve.asp)

30 minutes ferry from the city.
CRAP.,NOW I can't even remember what we were discussing!!

---

### Post by randell6564 on 2006-09-25
Here.,Copy mine!


d[B]eb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
[/B]

Save yours first! Then see if mine works, 'Burp'!

---

### Post by terranz on 2006-09-27
thanks, I'll give that a try :)

---

### Post by terranz on 2006-09-29
Thanks I replaced all the us with nz and everything works great :D

---

### Post by randell6564 on 2006-09-30
> **terranz said:**
> Thanks I replaced all the us with nz and everything works great :D
I've seen this before!  Dont understand why folks are having problems with the 'US' mirrors!  I have never had this problem.

---

### Post by terranz on 2006-09-30
Oh no I don't have any problems with US mirrors but NZ mirrors are faster and the traffic is free.

---

### Post by Kateikyoushi on 2006-09-30
> **terranz said:**
> It was a team building thing from work - A big portion of the IT dept went here

[http://www.motuihe.org.nz/](http://www.motuihe.org.nz/)
[http://www.doc.govt.nz/Explore/001~Other-Places/002~Auckland/Motuihe-Recreation-Reserve.asp](http://www.doc.govt.nz/Explore/001~Other-Places/002~Auckland/Motuihe-Recreation-Reserve.asp)


I wish my IT dept would do something like this, by the way been to NZ a month ago.

---

### Post by terranz on 2006-10-01
It was a lot more fun that I thought it would be.

---

