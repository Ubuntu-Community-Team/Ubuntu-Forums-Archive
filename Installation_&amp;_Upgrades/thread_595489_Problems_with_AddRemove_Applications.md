---
title: "Problems with Add/Remove Applications"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Austin17 on 2007-10-28
Hi, just today I started having problems with the Add/Remove Applications. I found several post on these forums with similar problems, but none of the solutions helped. When I try to install some programs in Ubuntu from the Add/Remove Applications program I get the message that I can't install it because it will not work on my i386 machine. I have tried updating and at the end of the long list of checking for updates I get this message:


```
Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/Release  Unable to find expected entry  web/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-backports/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```


I have changed update servers, and tried selecting everything for updates, but nothing seems to work. Help would be appreciated. Thanks!

[B]
~-~-~-~-~-~-~-~-~-~
EDIT:
A friend of mine with a similar computer build sent me his sources list, and everything works now.
[/B]

---

### Post by Pumalite on 2007-10-28
I think posting your sources.list would help others to help you:
cat /etc/apt/sources.list

---

### Post by zvacet on 2007-10-28
```
gksudo gedit /etc/apt/sources.list
```

If you see # sign in front of these lines remove it.Save and close.

```
sudo aptitude update
```

---

### Post by Austin17 on 2007-10-28
Here is my sources list:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.media.mit.edu/ubuntu/ gutsy web multiverse restricted universe main
deb-src http://ubuntu.media.mit.edu/ubuntu/ gutsy web multiverse restricted universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse


#AUTOMATIX REPOS START







#AUTOMATIX REPOS END
deb http://www.ansemreport.com/pidgin/repo feisty feisty-backports
deb http://security.ubuntu.com/ubuntu/ gutsy-security web multiverse restricted universe main
deb-src http://ubuntu.media.mit.edu/ubuntu/ gutsy-security web multiverse restricted universe main #Added by software-properties
deb http://ubuntu.media.mit.edu/ubuntu/ gutsy-updates web multiverse restricted universe main
deb-src http://ubuntu.media.mit.edu/ubuntu/ gutsy-updates web multiverse restricted universe main #Added by software-properties
deb http://ubuntu.media.mit.edu/ubuntu/ gutsy-backports web multiverse restricted universe main
deb-src http://ubuntu.media.mit.edu/ubuntu/ gutsy-backports web multiverse restricted universe main #Added by software-properties
```

---

### Post by Austin17 on 2007-10-29
Sorry for the double post, but does anyone know what might be the problem?

---

### Post by Austin17 on 2007-10-29
Sorry for the triple post, but I got the problem fixed. A friend of mine with a similar computer build sent me his sources list, and everything works now.

---

### Post by Tris2006 on 2007-10-30
> Sorry for the triple post, but I got the problem fixed. A friend of mine with a similar computer build sent me his sources list, and everything works now.

Your welcome. :grin:

---

