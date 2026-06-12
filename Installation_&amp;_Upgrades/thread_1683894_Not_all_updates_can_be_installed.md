---
title: "Not all updates can be installed"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by Bit Banger on 2011-02-08
I'm running Ubuntu 10.04, and I had some trouble with an old Drupal installation, so I ran the script below in an effort to revert PHP back to version 5.2.  The script below didn't work for me, and now Update Manager gives me the message "Not all updates can be installed", presumably because the script changed the repository for some of the software from lucid to karmic.  How do I get it back?
Thanks.

Script which "broke" Update Manager:

> #!/bin/bash
# by Ruben Barkow (rubo77) [http://www.entikey.z11.de/](http://www.entikey.z11.de/)

# Originally Posted by Bachstelze [http://ubuntuforums.org/showthread.php?p=9080474#post9080474](http://ubuntuforums.org/showthread.php?p=9080474#post9080474)
# OK, here's how to do the Apt magic to get PHP packages from the karmic repositories:

echo "Am I root?  "
if [ "$(whoami &2>/dev/null)" != "root" ] && [ "$(id -un &2>/dev/null)" != "root" ] ; then
  echo "  NO!

Error: You must be root to run this script.
Enter
sudo su
"
  exit 1
fi
echo "  OK";


#install aptitude before, if you don`t have it:
apt-get update
apt-get install aptitude
# or if you prefer apt-get use:
# alias aptitude='apt-get'

# finish all apt-problems:
aptitude update
aptitude -f install
#apt-get -f install


# remove all your existing PHP packages. You can list them with dpkg -l| grep php
PHPLIST=$(for i in $(dpkg -l | grep php|awk '{ print $2 }' ); do echo $i; done)
echo these pachets will be removed: $PHPLIST 
# you need not to purge, if you have upgraded from karmic:
aptitude remove $PHPLIST
# on a fresh install, you need purge:
# aptitude remove --purge $PHPLIST


#Create a file each in /etc/apt/preferences.d like this (call it for example /etc/apt/preferences.d/php5_2);
#
#Package: php5
#Pin: release a=karmic
#Pin-Priority: 991
#
#The big problem is that wildcards don't work, so you will need one such stanza for each PHP package you want to pull from karmic:

echo ''>/etc/apt/preferences.d/php5_2
for i in $PHPLIST ; do echo "Package: $i
Pin: release a=karmic
Pin-Priority: 991
">>/etc/apt/preferences.d/php5_2; done

# duplicate your existing sources.list replacing lucid with karmic and save it in sources.list.d:
#sed s/lucid/karmic/g /etc/apt/sources.list | sudo tee /etc/apt/sources.list.d/karmic.list

# better exactly only the needed sources, cause otherwise you can get a cachsize problem:
echo "# needed sources vor php5.2:
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic main restricted

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates universe

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
" >> /etc/apt/sources.list.d/karmic.list

aptitude update

apache2ctl restart

echo install new from karmic:
aptitude -t karmic install $PHPLIST

# at the end retry the modul libapache2-mod-php5 in case it didn't work the first time:
aptitude -t karmic install libapache2-mod-php5

apache2ctl restart

---

### Post by ikt on 2011-02-08
Problem is your sources.list got changed from lucid to karmic, you just want to change your sources.list back again.

Many ways to do it, tons of guides on it, just to explain real quick (bed time!) you will want to change all the 'karmic' to 'lucid' in the following section which is inside your /etc/apt/sources.list and that should fix it.

```
deb http://de.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic main restricted

deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

deb http://de.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic universe
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe

deb http://de.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
```

---

### Post by Bit Banger on 2011-02-12
Good to know about /etc/apt/sources.list, thanks, but I found that sources.list was unmodified.  The script just created the files /etc/apt/preferences.d/php5_2 and /etc/apt/sources.list.d/karmic.list, both of which I deleted, ran aptitude update, problem solved.

---

