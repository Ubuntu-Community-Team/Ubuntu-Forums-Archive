---
title: "Fiesty upgrade Failed to fetch and returned an error code (2)"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by swigrid on 2007-05-09
Is anybody, who sorted out this problem during upgrade from Edgy to Fiesty?

[PHP]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
[/PHP]

my source list is (if it will help):

[PHP]
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

#mplayer
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
# deb http://mirror.ubuntulinux.nl edgy-seveas extras

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse

#audacious
# deb http://static.audacious-media-player.org/ubuntu edgy main
# deb-src http://static.audacious-media-player.org/ubuntu edgy main

## Official Skype Repository
# deb http://download.skype.com/linux/repos/debian/ stable non-free

#jedit
# deb http://dl.sourceforge.net/sourceforge/jedit ./
# deb-src http://dl.sourceforge.net/sourceforge/jedit ./
[/PHP]

thanx guys... ;)

---

### Post by zvacet on 2007-05-09
I tryed links you give and sometimes just first one work and other not,and sometimes second work and others not.Maybe you can try to change server in software properties or just type

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by swigrid on 2007-05-09
I know i tried them too, and they works fine. And i can't change servers in software properties because it is upgrade providing by upgrade manager (that graphical interface). And as you could see in my source.list, those links are not included there. It means, that those links are provided by upgrade manager, which downloaded those links from somewhere...

and...
```

sudo aptitude upgrade

```
gave me this:
```

No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

thanx for ur reply

---

