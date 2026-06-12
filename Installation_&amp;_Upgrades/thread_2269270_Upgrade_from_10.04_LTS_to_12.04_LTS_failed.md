---
title: "Upgrade from 10.04 LTS to 12.04 LTS failed"
date: 2015-03-14
forum: Installation &amp; Upgrades
---

### Post by anrikun on 2015-03-14
I tried to upgrade from 10.04 LTS to 12.04 LTS and it failed with messages below.
What should I do?
 ```
Des erreurs ont été rencontrées pendant l'exécution :
 dbus
 accountsservice
 language-selector-common
Error in function:

 Une erreur fatale est survenue
 Veuillez signaler ce problÃ¨me comme un bogue et y inclure les
fichiers /var/log/dist-upgrade/main.log et
/var/log/dist-upgrade/apt.log. La mise a niveau a Ã©chouÃ©.
Votre fichier souce.list original a Ã©tÃ© enregistrÃ© dans
/etc/apt/sources.list.distUpgrade.

 SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
 Impossible d'installer les mises Ã  niveau
 Erreur pendant la soumission
'E:Couldn't configure pre-depend multiarch-support for
libapt-pkg4.12, probably a dependency cycle.'
Restauration du systÃ¨me dans son Ã©tat d'origine
 Restauration du systÃ¨me dans son Ã©tat d'origine


```





cat /etc/apt/sources.list shows:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb ftp://mirror.ovh.net/mirrors/ftp.ubuntu.com/ubuntu/ precise main restricted
deb-src ftp://mirror.ovh.net/mirrors/ftp.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb ftp://mirror.ovh.net/mirrors/ftp.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src ftp://mirror.ovh.net/mirrors/ftp.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb ftp://mirror.ovh.net/mirrors/ftp.ubuntu.com/ubuntu/ precise universe
deb-src ftp://mirror.ovh.net/mirrors/ftp.ubuntu.com/ubuntu/ precise universe
deb ftp://mirror.ovh.net/mirrors/ftp.ubuntu.com/ubuntu/ precise-updates universe
deb-src ftp://mirror.ovh.net/mirrors/ftp.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb ftp://mirror.ovh.net/mirrors/ftp.ubuntu.com/ubuntu/ precise multiverse
deb-src ftp://mirror.ovh.net/mirrors/ftp.ubuntu.com/ubuntu/ precise multiverse
deb ftp://mirror.ovh.net/mirrors/ftp.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src ftp://mirror.ovh.net/mirrors/ftp.ubuntu.com/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb ftp://mirror.ovh.net/mirrors/ftp.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src ftp://mirror.ovh.net/mirrors/ftp.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
deb http://software.virtualmin.com/gpl/ubuntu/ virtualmin-lucid main
deb http://software.virtualmin.com/gpl/ubuntu/ virtualmin-universal main

```

---

### Post by Moofus on 2015-03-14
i would just back up all files somewhere and do a fresh install.  in my desktop, i have a 320gb drive for files and a 128gb ssd for the os, so its easy to do fresh installs.  
btw, why not just install 14.04 LTS?

---

### Post by gifford on 2015-03-14
Yes, do a fresh install of 14.04.2

---

### Post by flaymond on 2015-03-14
Do fresh install is better, upgrading will conflicting your saved files in some cases.

---

### Post by anrikun on 2015-03-15
Doing a fresh install is not an option for me: it's a remote production server.
Everything seems to work as expected.
I just had to change some conf files for some services to restart.
System reports that currently installed release is 12.04 so I guess upgrade was somewhat done.

But I need to know what is left to be upgraded.
If I could get a log of a fully successful upgrade to compare with mine, it would help.

---

### Post by anrikun on 2015-03-15
Everything is ok!
For people who might need help, here's what I did to complete the upgrade:


 - replaced in /etc/apt/sources.list: deb [http://software.virtualmin.com/gpl/ubuntu/](http://software.virtualmin.com/gpl/ubuntu/) virtualmin-lucid main by deb [http://software.virtualmin.com/gpl/ubuntu/](http://software.virtualmin.com/gpl/ubuntu/) virtualmin-precise main
- ran:
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo dpkg --configure -a
sudo apt-get -f install
apt-get install bind9 spamassassin spamc procmail libnet-ssleay-perl  libpg-perl libdbd-pg-perl libdbd-mysql-perl quota iptables openssl  python mailman subversion ruby irb rdoc ri mysql-server mysql-client  mysql-common postgresql postgresql-client awstats webalizer  dovecot-common dovecot-imapd dovecot-pop3d proftpd webmin usermin  webmin-virtual-server libcrypt-ssleay-perl webmin-virtual-server-theme  webmin-virtualmin-dav webmin-virtualmin-svn webmin-virtualmin-awstats  webmin-virtualmin-mailman webmin-virtualmin-htpasswd clamav-base  clamav-daemon clamav clamav-data clamav-freshclam clamav-docs  clamav-testfiles libapache2-mod-fcgid scponly apache2 apache2-doc  libapache2-svn libsasl2-2 libsasl2-modules sasl2-bin  usermin-virtual-server-theme procmail-wrapper php-pear php5 php5-cgi  webmin-security-updates libgd2-xpm
sudo apt-get autoremove
(Some of these commands are duplicate of each other but you never know)


 I then rebooted the system with no problem!

---

