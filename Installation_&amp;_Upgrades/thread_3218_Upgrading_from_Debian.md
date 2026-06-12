---
title: "Upgrading from Debian?"
date: 2004-11-04
forum: Installation &amp; Upgrades
---

### Post by mattruby on 2004-11-04
I have Debian 3.0r/GNOME2.6.1/kernel2.4.20/Evolution1.4.6 . I want to upgrade to Ubuntu 4.10 , without deleting my Evolution email. I'd prefer to retain my currently installed packages, though I'd like to reinstall/upgrade them to the Ubuntu package versions. I can download/burn an install CD, or preferably just Internet install. Where are the upgrade instructions? And when it fails, where are the rollback instructions, so I can start over clean for another attempt? TIA - this process is the gateway for many current Debian users to swell the ranks of Ubuntu users.

---

### Post by im_ka on 2004-11-04
do a forum search on that, i think it's been discussed.

afaik (don't sue me if you screw up smthg :)), if you replace your sources.list with an ubuntu one, and do dist-upgrade, it should work.

```

deb http://archive.ubuntu.com/ubuntu/ warty main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ warty universe 
# deb-src http://archive.ubuntu.com/ubuntu/ warty universe 

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted 

##
## Various Multimedia Helper Apps Mplayer, Real, etc.. ##
deb ftp://ftp.nerim.net/debian-marillat/ unstable main

#java:#
deb http://jrfonseca.dyndns.org/debian ./ 

```

---

