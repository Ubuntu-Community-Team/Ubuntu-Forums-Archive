---
title: "Problems with upgrading to Dapper 6.06"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by mansys on 2006-06-01
I have a problem when i want to upgrade from current (breezy) to dapper 6.06

i run these commands more than 10 times but the upgrading process fails when it downloads about 40 files.

gksu "update-manager -d"

it appears to be like this

"W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)"

then this

"Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found"


can someone please help me with this problem

---

### Post by welsh_spud on 2006-06-01
It looks like the repository in question is out-of-action. It isn't official, so I think it is safe to remove it from the list.

In terminal type
```
sudo gedit /etc/apt/sources.list
```

Then find the lines that have the address [http://koti.mbnet.fi](http://koti.mbnet.fi)  in them, and add a # before the begining of the line.

After that, type in
```
sudo apt-get update
```

Then  ```
gksu update-manager -d
```

If you want, you can post your **sources.list** here and I will do it for you

---

### Post by smartalecks on 2006-06-01
I shall post mine:

```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.lowvoice.nl/apt breezy main
deb-src http://wine.lowvoice.nl/apt breezy main

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

#deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
#deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

## created by arnielistenremoved 
```

what should I change?

---

### Post by welsh_spud on 2006-06-01
That sources list should be fine now.

Type in terminal:
```
sudo apt-get update
```

Then
```
gksu update-manager -d
```

---

