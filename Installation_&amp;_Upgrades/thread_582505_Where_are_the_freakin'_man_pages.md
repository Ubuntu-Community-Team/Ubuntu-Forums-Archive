---
title: "Where are the freakin' man pages?"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by rumplefreakinstiltskin on 2007-10-19
Where are the freakin' man pages?  This is supposed to be linux, not Windows.  There's supposed to be man pages.  They're called man pagest because they are MANdatory, not because they are MANual pages.

Argh.

root@zuul:~# man 2 write
No manual entry for write in section 2
See 'man 7 undocumented' for help when manual pages are not available.
root@zuul:~# man 3 printf
No manual entry for printf in section 3
See 'man 7 undocumented' for help when manual pages are not available.
root@zuul:~#
root@zuul:~# apt-get install manpages-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package manpages-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package manpages-dev has no installation candidate
root@zuul:~# 

Ok, where the hell are they?

Unacceptable.  Absolutely unacceptable.

Oh yeah:
root@zuul:~# cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
root@zuul:~#

---

### Post by FredB on 2007-10-20
Why are you using root to read manpages ?

It works here. manpages-dev is installed without problems. Try to update your apt database before shouting.

> PRINTF(3)                  Linux Programmer’s Manual                 PRINTF(3)

NAME
       printf,   fprintf,  sprintf,  snprintf,  vprintf,  vfprintf,  vsprintf,
       vsnprintf - formatted output conversion

SYNOPSIS
       #include <stdio.h>

       int printf(const char *format, ...);
       int fprintf(FILE *stream, const char *format, ...);
       int sprintf(char *str, const char *format, ...);
       int snprintf(char *str, size_t size, const char *format, ...);

```
fred@fredo-gutsy:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
```

---

### Post by rumplefreakinstiltskin on 2007-10-20
> Why are you using root to read manpages ?

Because I happened to be root on account of trying to get the man pages.  Root's not allowed to read man pages?

> Try to update your apt database before shouting.

How do I do that?

Reading what few man pages are available doesn't seem to help.

e.g.:

# man apt
...
BUGS
       This manpage isn’t even started.
...




Nice.    Author should be shot.


I was shouting because those particular man pages, sec. 2 and 3. I can hardly imagine anyone saying to themselves, "let's omit those."  If a person thinks that is a good idea, it is hard to imagine they would make a distribution which would fit my needs.  It is a bad start, and I'm thinking maybe it is an indication that ubuntu is just not for me.

For me, It is sad to see linux go down a road in which people think it is ok to omit the man pages.

---

### Post by FredB on 2007-10-20
> **rumplefreakinstiltskin said:**
> > Why are you using root to read manpages ?

Because I happened to be root on account of trying to get the man pages.  Root's not allowed to read man pages?

I didn't say that. But I was just curious to see why you were using that account.

  > [quote]Try to update your apt database before shouting.[/quote]How do I do that?

> Reading what few man pages are available doesn't seem to help.

e.g.:

# man apt
...
BUGS
       This manpage isn’t even started.
...

In a normal account : sudo apt-get update ; in root, apt-get update

> Nice.    Author should be shot.


Where did I say that ?

> I was shouting because those particular man pages, sec. 2 and 3. I can hardly imagine anyone saying to themselves, "let's omit those."  If a person thinks that is a good idea, it is hard to imagine they would make a distribution which would fit my needs.  It is a bad start, and I'm thinking maybe it is an indication that ubuntu is just not for me.

Manpages-dev are not install by default, because it is not a system for developpers by conception. But they can be added flawlessly.

> For me, It is sad to see linux go down a road in which people think it is ok to omit the man pages.

Oh ?

Before doing apt-get update, be sure that your /etc/apt/sources.list looks something like this :

```

# 
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://fr.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://fr.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://fr.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse

```

fr.archive may be replaced by your own country abbreviation.

---

