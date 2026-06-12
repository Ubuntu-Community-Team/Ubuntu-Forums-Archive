---
title: "Last night upgrade killed my laptop"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by joplass on 2007-03-20
I upgraded 18 stuff last night and now Ubuntu does not boot.  Even my elive on the other partition is gone.  The line that shows start up of Ubuntu stops about half way.  Can't even get to recovery mode.

---

### Post by bapoumba on 2007-03-20
Can you boot from a liveCD ?

---

### Post by joplass on 2007-03-20
Well something strange here, when the Ubuntu bar got stuck I popped in the Edgy CD and hop it went.  I was able to go back to my installation with a message Volume need to upgrade.  So I said yes and the system installed a few software but at the end I was left with this message:

Failed to fetch [http://malteo.homelinux.net/dists/edgy-malteo/Release.gpg](http://malteo.homelinux.net/dists/edgy-malteo/Release.gpg) Could not connect to malteo.homelinux.net:80 (84.220.159.237). - connect (111 Connection refused)
Failed to fetch [http://malteo.homelinux.net/dists/edgy-malteo/all/i18n/Translation-en_US.bz2](http://malteo.homelinux.net/dists/edgy-malteo/all/i18n/Translation-en_US.bz2) Could not connect to malteo.homelinux.net:80 (84.220.159.237). - connect (111 Connection refused)


For now I am up and running, don't what the CD did though.

Very funny I am told there are 10 software to upgrade but only Auomatix2, Froswire, and amsn are listed.  Let's see where these upgrades will take me.

---

### Post by bapoumba on 2007-03-20
I cannot get to the repos you get an error from. Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by joplass on 2007-03-20
> **bapoumba said:**
> I cannot get to the repos you get an error from. Please post your sources.list:
```
cat /etc/apt/sources.list
```

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
#AUTOMATIX REPOS END

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

# Treviño's Beryl-SVN Ubuntu Repository
 # GPG key: 81836EBF
##deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy beryl-svn

## Murine
deb [http://malteo.homelinux.net](http://malteo.homelinux.net) edgy-malteo all
deb-src [http://malteo.homelinux.net](http://malteo.homelinux.net) edgy-malteo all

---

### Post by halw on 2007-03-20
Looks like you need to comment out the last two lines in your sources.list. Also you have a reference to a dapper repo. I would comment that out as well

---

### Post by bapoumba on 2007-03-20
Please open your file with nano (a small text editor):
```
sudo nano -B /etc/apt/sources.list
```
and comment (add a # at the beginning) the two following lines: 
> **joplass said:**
> 
deb [http://malteo.homelinux.net](http://malteo.homelinux.net) edgy-malteo all
deb-src [http://malteo.homelinux.net](http://malteo.homelinux.net) edgy-malteo all

and remove:
> **joplass said:**
> 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

Save the file (CTRL-O, same name) and exit nano (CTRL-X). Run:
```
sudo aptitude update
```

---

