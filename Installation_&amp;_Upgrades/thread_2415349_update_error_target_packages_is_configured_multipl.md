---
title: "update error target packages is configured multiple times"
date: 2019-03-24
forum: Installation &amp; Upgrades
---

### Post by tomdf on 2019-03-24
HI guys,

i have a small problem and maybe you would be so kind and help me. 

when i do an update on my ubuntu 18.04 server i get an error 

--------------------------

```
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:19
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:19
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:19
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:19
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:19
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:19
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:29
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:29
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:29
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:29
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:29
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:29
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:21
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:21
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:21
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:21
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:21
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:21
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:31
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:31
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:31
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:31
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:31
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:31
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:51
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:51
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:51
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:51
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:51
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:51
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:53
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:53
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:53
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:53
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:53
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:19
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:19
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:19
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:19
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:19
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:19
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:29
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:29
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:29
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:29
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:29
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:8 and /etc/apt/sources.list:29
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:21
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:21
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:21
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:21
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:21
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:21
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:31
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:31
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:31
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:31
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:31
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list:31
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:51
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:51
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:51
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:51
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:51
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:51
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:53
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:53
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:53
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:53
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:53
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:53
```

---------------------
this is my sources.list
--------------------
```
# deb [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic main restricted universe multiverse restricted


# deb [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic-updates main restricted universe multiverse restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted universe multiverse restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic main restricted universe multiverse restricted
# deb-src [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic main restricted universe multiverse restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic-updates main restricted universe multiverse restricted
# deb-src [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic-updates main restricted universe multiverse restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic universe
# deb-src [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic universe
deb [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic-updates universe
# deb-src [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic multiverse
# deb-src [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic multiverse
deb [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic-updates multiverse
# deb-src [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main restricted universe multiverse release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic-backports main restricted universe multiverse restricted universe multiverse
# deb-src [http://asi-fs-n.contabo.net/ubuntu](http://asi-fs-n.contabo.net/ubuntu) bionic-backports main restricted universe multiverse restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted universe multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted universe multiverse restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports main restricted universe multiverse
```

can anybody give me an idea how to fix this problem?

thanks in advance for your kind help

Tom

---

### Post by Bashing-om on 2019-03-24
tomdf; Hello - 

The system is telling you what the issue is and where the problems lie :)

All we got to do is remove the duplicate entries.

To make finding the correct identified lines, please post - Between Code Tags -:
 code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
the output of terminal command:
```

cat -n /etc/apt/sources.list

```

Such then that you can easily correlate what the errors are to what is in the /etc/apt/sources.list  file.
Then - as I am terminally minded - we fire up your favorite text editor and repair the damage.

[INDENT][INDENT]simple as falling out of bed wide awake
[/INDENT][/INDENT]

---

### Post by tomdf on 2019-03-25
Hi there,

thanks a lot for your kind help.
this is the sources.list and i did delete already something there.
As i understand line 2 and line 3 have the same repository bionic updates universe is this right?
so i should delete line 3 right?

Is there a recomended sources.list for ubuntu 18.04 webserver?

thanks for your help 

```

deb http://asi-fs-n.contabo.net/ubuntu bionic main restricted universe multiverse restricted
deb http://asi-fs-n.contabo.net/ubuntu bionic-updates main restricted universe multiverse restricted
deb http://asi-fs-n.contabo.net/ubuntu bionic-updates universe
deb http://asi-fs-n.contabo.net/ubuntu bionic multiverse
deb http://asi-fs-n.contabo.net/ubuntu bionic-updates multiverse
deb http://asi-fs-n.contabo.net/ubuntu bionic-backports main restricted universe multiverse restricted universe multiverse
deb http://security.ubuntu.com/ubuntu bionic-security main restricted universe multiverse restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
deb http://archive.ubuntu.com/ubuntu bionic universe
deb http://archive.ubuntu.com/ubuntu bionic-backports main restricted universe multiverse

```

---

### Post by deadflowr on 2019-03-25
> Is there a recomended sources.list for ubuntu 18.04 webserver?
The sources are the same, by default.
Whether desktop or server.

I'd recommend removing the entries with single repositories like these

```
deb http://asi-fs-n.contabo.net/ubuntu bionic-updates universe
deb http://asi-fs-n.contabo.net/ubuntu bionic multiverse
deb http://asi-fs-n.contabo.net/ubuntu bionic-updates multiverse
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
deb http://archive.ubuntu.com/ubuntu bionic universe
```
since all those are already mentioned in the other entries listed.
And remove the duplicate restricted, universe, and multiverse entries in the backports entry here
```
deb http://asi-fs-n.contabo.net/ubuntu bionic-backports main restricted universe multiverse **restricted universe multiverse**
```

---

### Post by Bashing-om on 2019-03-25
tomdf; Hey - hey

Heed  deadflowr's last.

As an example of a working sources list file: this is mine:
> 
#
deb [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) bionic main restricted universe multiverse

deb [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) bionic-security main restricted universe multiverse

deb [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) bionic-updates main restricted universe multiverse

deb [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) bionic-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner


For MY use case. where it is bare bones; only what I need. From a fast mirror site that is kept updated.
Note I have no need in this install for source code thus "src" is not included, and you may or may not want the backports and partner repos.

[INDENT]hope this helps
[/INDENT]

---

