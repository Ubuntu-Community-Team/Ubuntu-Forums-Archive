---
title: "Upgrade to Gutsy not going well"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by dean20007 on 2007-10-24
I tried to upgrade to gutsy from fiesty tonight and the first thing I did was try to prepare the system by selecting update manager then check this failed. I checked the /var/log/main.log file and the output is below. Have I done something incredibly stupid or is this a problem anyone else is having



```
xxxxx@xxxxxx-desktop:/var/log/dist-upgrade$ cat main.log 
2007-10-24 19:25:57,746 INFO release-upgrader version '0.81' started
2007-10-24 19:25:58,532 DEBUG lsb-release: 'feisty'
2007-10-24 19:25:58,533 DEBUG _pythonSymlinkCheck run
2007-10-24 19:25:59,578 DEBUG checkViewDepends()
2007-10-24 19:25:59,579 DEBUG getRequiredBackports()
2007-10-24 19:26:01,387 ERROR IOError in cache.update(): 'Failed to fetch http://www.backports.org/debian/dists/stable/ucf/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz 404 Not Found
'. Retrying (currentRetry: 0)
2007-10-24 19:26:47,726 DEBUG cancelClicked
2007-10-24 19:26:47,733 ERROR IOError in cache.update(): 'Failed to fetch http://ubuntu.beryl-project.org/dists/feisty/Release.gpg 
Failed to fetch http://ubuntu.beryl-project.org/dists/feisty/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://ubuntu.beryl-project.org/dists/feisty/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://ubuntu.beryl-project.org/dists/edgy/Release.gpg 
Failed to fetch http://ubuntu.beryl-project.org/dists/edgy/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz 404 Not Found
Failed to fetch http://www.backports.org/debian/dists/stable/ucf/binary-i386/Packages.gz 404 Not Found
'. Retrying (currentRetry: 1)
2007-10-24 19:26:47,831 ERROR IOError in cache.update(): 'Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/Release.gpg 
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/i18n/Translation-en_GB.bz2 
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg 
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_GB.bz2 
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_GB.bz2 
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg 
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_GB.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_GB.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_GB.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_GB.bz2 
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg 
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/i18n/Translation-en_GB.bz2 
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_GB.bz2 
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/Release.gpg 
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/i18n/Translation-en_GB.bz2 
Failed to fetch http://ubuntu.beryl-project.org/dists/feisty/Release.gpg 
Failed to fetch http://ubuntu.beryl-project.org/dists/feisty/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://ubuntu.beryl-project.org/dists/feisty/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://www.albertomilone.com/drivers/edgy/latest/32bit/binary/Release.gpg 
Failed to fetch http://www.albertomilone.com/drivers/edgy/latest/32bit/binary/en_GB.bz2 
Failed to fetch http://www.albertomilone.com/drivers/edgy/latest/32bit/binary/en_GB.bz2 
Failed to fetch http://ubuntu.beryl-project.org/dists/edgy/Release.gpg 
Failed to fetch http://ubuntu.beryl-project.org/dists/edgy/main/i18n/Translation-en_GB.bz2 
Failed to fetch http://www.backports.org/debian/dists/stable/Release.gpg 
Failed to fetch http://www.backports.org/debian/dists/stable/ucf/i18n/Translation-en_GB.bz2 
Failed to fetch http://people.debian.org/~dexter/dists/php5/Release.gpg 
Failed to fetch http://people.debian.org/~dexter/dists/php5/woody/i18n/Translation-en_GB.bz2 
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg 
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/debian-installer/i18n/Translation-en_GB.bz2 
'. Retrying (currentRetry: 2)
2007-10-24 19:26:47,831 ERROR doUpdate() failed complettely
2007-10-24 19:26:50,901 DEBUG marking 'release-upgrader-apt' for install
2007-10-24 19:26:50,998 DEBUG marking 'release-upgrader-dpkg' for install
2007-10-24 19:26:51,128 DEBUG pre-requists item: '<pkgAcquire::ItemIterator object: Status: 1 Complete: 0 Local: 0 IsTrusted: 0 FileSize: 1924684 DestFile:'/tmp/tmpLyq4M1/backports/partial/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' DescURI: 'http://gb.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ub' 
2007-10-24 19:26:51,129 ERROR pre-requists item 'http://gb.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' is NOT trusted

```

---

### Post by Bragador on 2007-10-24
It says "failed to fetch" so it seems to be a connection problem.

Did you try to upgrade from other servers?

Go in Administration->Software Sources and click "download from", select "other" and select "best server".

Or simply select one manually.

If it doesn't work then it's not a connection problem.

---

### Post by dean20007 on 2007-10-25
Tried various servers all seem to fail at 77 of 82. Internet connection seems fine. 

These are the error messages I see when attempting to check from the update manager

```
http://ubuntu.beryl-project.org/dists/feisty/Release.gpg
http://ubuntu.beryl-project.org/dists/feisty/main/i18n/Translation-en_GB.bz2
http://ubuntu.beryl-project.org/dists/feisty/main/i18n/Translation-en_GB.bz2
http://ubuntu.beryl-project.org/dists/edgy/Release.gpg
http://ubuntu.beryl-project.org/dists/edgy/main/i18n/Translation-en_GB.bz2
http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz: 404 Not Found
http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz: 404 Not Found
http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz: 404 Not Found
http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz: 404 Not Found
http://www.backports.org/debian/dists/stable/ucf/binary-i386/Packages.gz: 404 Not Found
```

and

```
W: GPG error: http://download.tuxfamily.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
```

---

### Post by ice60 on 2007-10-25
i upgraded my laptop yesterday and it worked perfectly :cool: 

i made sure i only used the base repos that are supported by ubuntu and got rid of all the others. i generated the sources from here -
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
and only used **Ubuntu supported packages** and **Ubuntu community supported packages** for the upgrade, then added more after it was all installed and working.

i've used linux for a few years and that was the first time i'd done an upgrade :)

and this is the command i used to do the upgrade -
```
gksu "update-manager -c"
```

[color=blue]EDIT[/color] so these were the repos i used (i picked UK repos, that's were i live :D)
```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://gb.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://gb.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://gb.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://gb.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse
```
i should add it worked perfectly for me, but i've no idea if just using those repos and using that upgrade command is the best way or not ??

---

### Post by jithu2k1 on 2007-10-28
Run these commands in a terminal window to get the gpg keys for gutsy.

```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update
```


This should solve the gpg public key error for the tuxfamily.org downloads for gutsy

---

