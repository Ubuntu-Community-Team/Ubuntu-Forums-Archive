---
title: "From Gusty to Hardy- Xubuntu"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Wangsta on 2008-04-30
I decided to upgrade from gutsy to 8.04, but I ran into some problems.:confused::confused::confused:
While upgrading, I got this error message:

```
Error during update

A problem occurred during the update. 
This is usually some sort of network problem, please check your 
network connection and retry.
[CODE]Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
```[/CODE]

Any ideas on what's wrong? Also when I try to load all my repos, I get this:

```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of
 network problems. If available an older version of the failed index will be used. 
Otherwise the repository will be ignored. Check your network connection and the correct
 writing of the repository address in the preferences.


[CODE]http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg
http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2
http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2
http://security.ubuntu.com/ubuntu/dists/gutsy-security/web/i18n/Translation-en_US.bz2
http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2
http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release: Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release: Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
```[/CODE]

If it helps, it attempts to get Translation-en-Us pack or something like that, and it 'fails' alot while other files are marked as 'done' or 'hit'...

Help.... Please?

---

### Post by Pumalite on 2008-04-30
System>Administration>Software Sources>Download From>Other>Let it choose the best Server for you.
If not, post:
cat /etc/apt/sources.list

---

### Post by bapoumba on 2008-05-01
You still have gutsy repos in your sources.list.
Please use Pumalite's command and post the file.

---

### Post by Wangsta on 2008-05-01
I tried the command and this is what I got:

```
server@server:~$ cat /etc/apt/sources.list
deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy main restricted web
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy-updates main restricted web
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy universe
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy universe
deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy-updates universe
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy multiverse
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy multiverse
deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy-updates multiverse
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy-security main restricted web
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy-security main restricted
deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy-security universe
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy-security universe
deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy-security multiverse
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy-security multiverse
deb http://packages.medibuntu.org/ gutsy free non-free

```

When I switched to the server that Xubuntu picked for me, It told me I had to reload the repos, and I got this:
```

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of 
network problems. If available an older version of the failed index will be used.
 Otherwise the repository will be ignored. Check your network connection and the 
correct writing of the repository address in the preferences.


[CODE]http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/main/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/web/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/main/source/Sources.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/restricted/source/Sources.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/universe/source/Sources.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/multiverse/source/Sources.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/web/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/main/source/Sources.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/universe/source/Sources.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-security/web/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-security/main/source/Sources.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-security/restricted/source/Sources.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-security/universe/source/Sources.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz: 404 Not Found
```[/CODE]

---

### Post by Pumalite on 2008-05-01
Your upgrade did not work. All your repos are Gutsy:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Wangsta on 2008-05-01
That site doesn't really help.
It says:

> #Click the Check button to check for new updates.

#If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.

#A message will appear informing you of the availability of the new release. 
MY problem is that when I click the Check button, I get the horrible
> Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?) message...

---

### Post by Pumalite on 2008-05-01
Better do a clean install.

---

### Post by bapoumba on 2008-05-02
I'm not sure what the exact url for [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) is. I can get to the repos, but the /pub file is absent. You may have an error in your repos url.

Please use the regular ubuntu repos, **first to fully upgrade your gutsy install**, and then to upgrade to hardy.

Here are the repos url:
```
## General.
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

## Major bug fix updates.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

## Security.
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

```

You can replace your current sources.list with this one, then upgrade. Once everything is up to date, you should have the option to upgrade to hardy.

To edit the sources.list file, you can use nano, a small text editor working from the command line. Backup your file first.
```
cp /etc/apt/sources.list sources.list_bak
sudo nano /etc/apt/sources.list
```
Replace everything that is in the file with the repos above. Save the file with CTRL-O, exit nano with CTRL-X.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

