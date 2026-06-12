---
title: "LUCID: Problem downloading Repositories/Packages"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by sanchino on 2010-06-24
Hi all,

I did the UPGRADE from Karmic Koala to Lucid, and everything was going well. But now I've been having problems with the UBUNTU UPDATE tool for the last 2 weeks. Every time I try to do an update check on the packages, I get the following message:
[INDENT]*Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)*[I]

Some index files failed to download, they have been ignored, or old ones used instead.[/I]
[/INDENT]I need help ASAP. I've tried changing the servers to MAIN and others, and still no way to solve it. I've also checked for other posts, but haven't found a solution yet. Here's my SOURCES LIST (gksudo gedit /etc/apt/sources.list)

[INDENT]# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main universe restricted multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

[/INDENT]Thanks for your time...

---

### Post by bolucpap on 2010-06-24
At first glance it seems as if the line:
```

deb http://archive.ubuntu.com/ubuntu  lucid deb-src http://archive.ubuntu.com/ubuntu/ lucid main universe restricted multiverse

```
Should instead read as:
```

deb http://archive.ubuntu.com/ubuntu  lucid 
deb-src http://archive.ubuntu.com/ubuntu/ lucid main universe restricted multiverse

```

I'm not sure how exactly white space in the file is treated, but before trying anything try doing a 
```

gksudo gedit /etc/apt/sources.list

```

then inserting a carriage return (or linefeed, never can remember which is which) so that the line reads as the second code block.

Hope this helps,

Boluc

---

### Post by drs305 on 2010-06-24
You have two lines that were combined somehow. 

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)  lucid [COLOR="Red"]deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main universe restricted multiverse
[/COLOR]deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free


Open gedit as root and make this change to separate the lines and add the repositories. You can use copy/paste to make the change:
```
gksu gedit /etc/apt/sources.list
```
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)  lucid [COLOR="Red"]main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main universe restricted multiverse[/COLOR]
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free


---

### Post by sanchino on 2010-06-24
Hey guys, 

Thx a lot for the help. I finally what **drs305** suggested and it worked!!!! Finaly!

Best...

---

