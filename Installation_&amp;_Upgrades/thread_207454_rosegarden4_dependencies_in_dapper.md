---
title: "rosegarden4 dependencies in dapper"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by blizzrdof77 on 2006-07-01
hi everyone. i tried adding this repository to my sourcest.list so i could install rosegarden4 on dapper drake...

deb [http://ubuntu.lnix.net/dapper/](http://ubuntu.lnix.net/dapper/) ./

after doing so, i tried installing rosegarden4 and this was my error message...

```
alex@alex-laptop:/etc/apt$ sudo apt-get install rosegarden4
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  rosegarden4: Depends: libjack0.100.0-0 (>= 0.100.0) but it is not installable
               Depends: liblo0 (>= 0.22) but it is not installable
               Depends: liblrdf0 but it is not installable
               Depends: jackd but it is not installable
E: Broken packages
```

---

### Post by John.Michael.Kane on 2006-07-02
The source.list posted will give you rosegarden

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

##deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

```
[[IMG]http://img276.imageshack.us/img276/6452/screenshot8jw.th.png[/IMG]](http://img276.imageshack.us/my.php?image=screenshot8jw.png)

---

