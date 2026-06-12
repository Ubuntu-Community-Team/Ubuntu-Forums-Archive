---
title: "apt-get update not working (404 not found)"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by xander1990 on 2013-01-02
Hi all,

I'm facing a very annoying problem.
I try to **apt-get updat**e and that's what I'm getting:

```
root@mimas:/etc/apt# apt-get update
Ign http://ftp.halifax.rwth-aachen.de precise InRelease
Ign http://ftp.halifax.rwth-aachen.de precise Release.gpg
Ign http://ftp.halifax.rwth-aachen.de precise Release
Ign http://ftp.halifax.rwth-aachen.de precise/main TranslationIndex
Ign http://ftp.halifax.rwth-aachen.de precise/restricted TranslationIndex
Err http://ftp.halifax.rwth-aachen.de precise/main i386 Packages
  404  Not Found
Err http://ftp.halifax.rwth-aachen.de precise/restricted i386 Packages
  404  Not Found
Ign http://ftp.halifax.rwth-aachen.de precise/main Translation-en
Ign http://ftp.halifax.rwth-aachen.de precise/restricted Translation-en
W: Failed to fetch http://ftp.halifax.rwth-aachen.de/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ftp.halifax.rwth-aachen.de/ubuntu/dists/precise/restricted/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```I tried with several repositories, always getting the same error.

My internet connection is perfectly OK.

Finally I ended up with /etc/apt/sources.list like that:

```

# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Beta i386 (20120327)]/ precise main restricted

#deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Beta i386 (20120327)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
#deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise main restricted
deb [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) precise main restricted
#deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise-updates main restricted
#deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

# xand deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib

```

Can someone point me in the right direction? I tried to make a clean and read like 50 posts about the same problem but no solution for me.

Thanks in advance.

---

### Post by dino99 on 2013-01-02
maybe that ftp is down right now, or you does not have rights (proxy rules)
is it your own system ? if so, then test with the main server.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by xander1990 on 2013-01-02
> **dino99 said:**
> maybe that ftp is down right now, or you does not have rights (proxy rules)
is it your own system ? if so, then test with the main server.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

well, I tried with like 10 different servers, the main one included. No difference.
It's my server system and it's connected directly to Internet, I mean, no proxy.

---

### Post by dino99 on 2013-01-02
is your browser able to open the related ftp adresses ?

you can also try with a clean cache:

sudo rm /var/cache/apt/archives/*

---

### Post by xander1990 on 2013-01-02
> **dino99 said:**
> is your browser able to open the related ftp adresses ?

you can also try with a clean cache:

sudo rm /var/cache/apt/archives/*

Well, same result:

```
root@mimas:~# rm -vf /var/cache/apt/archives/*
removed `/var/cache/apt/archives/lock'
rm: cannot remove `/var/cache/apt/archives/partial': Is a directory
root@mimas:~# ls -la /var/cache/apt/archives/
total 32
drwxr-xr-x 3 root root 24576 Jan  2 07:45 .
drwxr-xr-x 3 root root  4096 Jan  2 06:39 ..
drwxr-xr-x 2 root root  4096 Oct 23 14:52 partial
root@mimas:~# rm -rvf /var/cache/apt/archives/*
removed directory: `/var/cache/apt/archives/partial'
root@mimas:~# apt-get update
Ign http://ftp.halifax.rwth-aachen.de precise InRelease
Ign http://ftp.halifax.rwth-aachen.de precise Release.gpg
Ign http://ftp.halifax.rwth-aachen.de precise Release
Ign http://ftp.halifax.rwth-aachen.de precise/main TranslationIndex
Ign http://ftp.halifax.rwth-aachen.de precise/restricted TranslationIndex
Err http://ftp.halifax.rwth-aachen.de precise/main i386 Packages
  404  Not Found
Err http://ftp.halifax.rwth-aachen.de precise/restricted i386 Packages
  404  Not Found
Ign http://ftp.halifax.rwth-aachen.de precise/main Translation-en
Ign http://ftp.halifax.rwth-aachen.de precise/restricted Translation-en
W: Failed to fetch http://ftp.halifax.rwth-aachen.de/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ftp.halifax.rwth-aachen.de/ubuntu/dists/precise/restricted/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I can go with my browser to [http://ftp.halifax.rwth-aachen.de/ubuntu/dists/precise/restricted/binary-i386/Packages](http://ftp.halifax.rwth-aachen.de/ubuntu/dists/precise/restricted/binary-i386/Packages) and obviously I get 404 error.

If I go to [http://ftp.halifax.rwth-aachen.de/ubuntu/dists/precise/restricted/binary-i386/](http://ftp.halifax.rwth-aachen.de/ubuntu/dists/precise/restricted/binary-i386/) I can see Packages.gz file. So actually the file is there only with gz suffix.

Then, I try to wget the file from my server machine:

```
root@mimas:~# wget http://ftp.halifax.rwth-aachen.de/ubuntu/dists/precise/restricted/binary-i386/Packages.gz
--2013-01-02 07:49:31--  http://ftp.halifax.rwth-aachen.de/ubuntu/dists/precise/restricted/binary-i386/Packages.gz
Resolving ftp.halifax.rwth-aachen.de (ftp.halifax.rwth-aachen.de)... 137.226.34.42
Connecting to ftp.halifax.rwth-aachen.de (ftp.halifax.rwth-aachen.de)|137.226.34.42|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-01-02 07:49:31 ERROR 404: Not Found.
```

Exactly the same result, 404. On the other side, the host is resolved correctly, so it's not a DNS problem.

I think I'm going crazy, how is that possible?

---

### Post by xander1990 on 2013-01-02
Well, definitely my wget is not working well. I cannot get any file with it.

I changed the schema to ftp and now it's working perfectly. But I still need my wget.

---

### Post by dino99 on 2013-01-02
well these ftp adresses have not been updated since mid 2012; quite of dead cow ;)

---

### Post by xander1990 on 2013-01-02
OK. Sorry guys, it was a firewall issue.

Thanks.

---

