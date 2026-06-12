---
title: "Can't upgrade to 7.10"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by lukemack on 2007-11-15
Hi,

I am trying to upgrade from 7.04 to 7.10 but it stalls at the upgrade step 'fetching file 54 of 55' and then eventually errors out, saying that the connection to cycleide.uni.cc timed out. Is there a way round this? I am based in the UK if there is a mirror I can change to? 

Many thanks,

<L>

---

### Post by taurus on 2007-11-15
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by lukemack on 2007-11-15
thanks - that pointed me to the problem. I removed that entry from the list and it is working now.

---

### Post by tlwong on 2007-11-15
I have not been able to upgrade my Ubuntu 7.04 to 7.10 after several trial.  These are the error messages I got after upgrading halfway.

[http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:) Could not resolve 'wine.lowvoice.nl'
[http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not resolve 'wine.lowvoice.nl'
[http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:) Could not resolve 'wine.lowvoice.nl'
[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2:](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2:](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

Need some help to figure out how to solve this problem.  Any help is much appreciated.

Tee

---

### Post by taurus on 2007-11-15
> **tlwong said:**
> I have not been able to upgrade my Ubuntu 7.04 to 7.10 after several trial.  These are the error messages I got after upgrading halfway.

[http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:) Could not resolve 'wine.lowvoice.nl'
[http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not resolve 'wine.lowvoice.nl'
[http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:) Could not resolve 'wine.lowvoice.nl'
[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2:](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2:](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

Need some help to figure out how to solve this problem.  Any help is much appreciated.

Tee

Maybe you should post your /etc/apt/sources.list too.  I can tell you one thing right now that you need to comment out all those extra repos that you added in like automatix because that is one sure way to break your system if you want to upgrade with those in your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by cfrivas on 2007-11-16
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.gz) Could not resolve 'wine.lowvoice.nl'

Help please, I wish to update my 7.04 to 7.10 but I get these errors above. Do I uninstall WINE ?

---

### Post by taurus on 2007-11-16
> **cfrivas said:**
> Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.gz) Could not resolve 'wine.lowvoice.nl'

Help please, I wish to update my 7.04 to 7.10 but I get these errors above. Do I uninstall WINE ?

No but you need to comment out by placing a # in front of those repos in your /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by MusicmanJustLC on 2007-11-17
Hey there. When I tried upgrading to 7.10 I got this error message: "Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://za.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)"

So being fairly new to linux, I have no idea what that really means. Can someone please help?

---

### Post by MusicmanJustLC on 2007-11-17
Oh, and this is my source list if it helps:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by PmDematagoda on 2007-11-17
> **MusicmanJustLC said:**
> Hey there. When I tried upgrading to 7.10 I got this error message: "Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://za.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)"

So being fairly new to linux, I have no idea what that really means. Can someone please help?

It might be a problem with the server, go to System>Administration>Software Sources and then change the server to one that is close to you and then try upgrading again.

---

### Post by MusicmanJustLC on 2007-11-17
Thanks, that seems to be working... I'll let you know when the stuff finishes downloading in a few hours, lol... Stoopid slow internet :neutral:

---

