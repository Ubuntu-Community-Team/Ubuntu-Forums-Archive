---
title: "failing to install new packages"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by mmistroni on 2010-07-15
Hello,
  while upgrading packages in my ubuntu 10.4 i m receiving following exception
```

Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (113: No route to host)
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_GB.bz2  Unable to connect to za.archive.ubuntu.com:http:
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_GB.bz2  Unable to connect to za.archive.ubuntu.com:http:
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to za.archive.ubuntu.com:http:
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz  Unable to connect to za.archive.ubuntu.com:http:
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz  Unable to connect to za.archive.ubuntu.com:http:
Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz  Unable to connect to za.archive.ubuntu.com:http:
Some index files failed to download, they have been ignored, or old ones used instead.

```

anyone could help? shall i just remove the  za.archive.ubuntu.com from my repositories?

w/kindest regards
 marco

---

### Post by tommcd on 2010-07-15
Is it working now for you? I can get to that mirror:
[http://za.archive.ubuntu.com/ubuntu/dists/lucid/](http://za.archive.ubuntu.com/ubuntu/dists/lucid/)
Try loading that link in firefox.
Are you behind a proxy or something?
Sometimes mirrors may go down temporarily. You can always try later, or try another mirror.
Write back if you need more help.

---

### Post by mmistroni on 2010-07-15
Hello
  thanks for reply
no icannot load the link even from firefox

i m in UK....... could that be the reason?

regards
 marco

---

### Post by tommcd on 2010-07-15
> **mmistroni said:**
> 
no icannot load the link even from firefox
i m in UK....... could that be the reason?

**Are you behind a proxy????????**

If not, try choosing another mirror. Go to: system administration > software sources, and choose a different mirror.
Then run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
and see if you can get any updates that may be available.

If there are no other mirrors available when you go to: system > administration > software sources, then do this:
First, back up your sources.list:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
Then run:
```
gksudo gedit /etc/apt/sources.list
```
Then simply remove the **za.** before each mirror. Don't forget the *dot* "." after *za*.
This will put you on the main server. 
See if you can connect to it in firefox first:
[http://archive.ubuntu.com/ubuntu/dists/lucid/](http://archive.ubuntu.com/ubuntu/dists/lucid/)
Then run:
 ```

sudo apt-get update
sudo apt-get dist-upgrade

```
and see if you can get the updates.

---

### Post by mmistroni on 2010-07-15
Hello,
 t hanks looks it's working fine.. i m updating from main server...

regards
 marco

---

### Post by srikanth40 on 2011-01-05
Even I have the same problem. I am unable to connect to repositories.

I am behind a proxy. ([http://proxy.nitk.ac.in:9001/proxy.pac](http://proxy.nitk.ac.in:9001/proxy.pac))

I tried updating 
    1. /etc/apt/apt.conf [Acquire:: Proxy...]
    2. /etc/bash.bashrc [export http_proxy=http://proxy.nitk.ac.in:9001/proxy.pac]

Contents of my "sources.list" file

#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse



What should I do to connect to repositories from behind a proxy.


Thanks,
Srikanth

---

### Post by nilsw1 on 2011-01-05
The instruction to change mirror helped me solve a similar problem.  While staying in France the upgrade to 10.04..1 could not fetch 18 files  from se.archive.ubuntu.com/... even though I could get to the addresses  i Firefox. Changing to a mirror in France and
sudo apt-get update
sudo apt-get dist-upgrade
and re-doing the upgrade solved the problem (only the 18 missing files were fetched). Thanks!

---

