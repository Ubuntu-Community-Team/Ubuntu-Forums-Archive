---
title: "do-release-upgrade 10.04.3 -&gt; 12.04"
date: 2014-01-14
forum: Installation &amp; Upgrades
---

### Post by stschulze on 2014-01-14
hi,

after do-release-upgrade .... the login tells me: 10.04.3 .... not 12.04 ......

i have used these howto: [http://wiki.reelbox4you.tv/doku.php/avantgarde/bedienung/ubuntu_release_upgrade](http://wiki.reelbox4you.tv/doku.php/avantgarde/bedienung/ubuntu_release_upgrade)

i have upgrade without problem, after restart :

```

root@ReelBox:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    (R)Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid

```

why not 12.04?


after install lsb-core:
```

root@ReelBox:~# lsb_release -a
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    (R)Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid

```

/etc/issue :
```

(R)Ubuntu 10.04.3 LTS \n \l

```

/etc/issue.dpkg-dist :
```

Ubuntu 12.04 LTS \n \l

```

/etc/apt/sources.list
```

# deb cdrom:[Kubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.2)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


deb http://de.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
# deb http://de.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
# deb-src http://de.archive.ubuntu.com/ubuntu/ lucid-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://de.archive.ubuntu.com/ubuntu/ precise universe
# deb http://de.archive.ubuntu.com/ubuntu/ lucid-updates universe
# deb-src http://de.archive.ubuntu.com/ubuntu/ lucid-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu.
## team, and may not be under a free licence. Please satisfy yourself as to.
## your rights to use the software. Also, please note that software in.
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ precise multiverse
# deb http://de.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

```

```

root@ReelBox:~# aptitude update && aptitude safe-upgrade
Ign http://de.archive.ubuntu.com precise InRelease
Treffer http://de.archive.ubuntu.com precise Release.gpg
Treffer http://de.archive.ubuntu.com precise Release
Treffer http://de.archive.ubuntu.com precise/main Sources
Treffer http://de.archive.ubuntu.com precise/restricted Sources
Treffer http://de.archive.ubuntu.com precise/universe Sources
Treffer http://de.archive.ubuntu.com precise/multiverse Sources
Treffer http://de.archive.ubuntu.com precise/main i386 Packages
Treffer http://de.archive.ubuntu.com precise/restricted i386 Packages
Treffer http://de.archive.ubuntu.com precise/universe i386 Packages
Treffer http://de.archive.ubuntu.com precise/multiverse i386 Packages
Treffer http://de.archive.ubuntu.com precise/main TranslationIndex
Treffer http://de.archive.ubuntu.com precise/multiverse TranslationIndex
Treffer http://de.archive.ubuntu.com precise/restricted TranslationIndex
Treffer http://de.archive.ubuntu.com precise/universe TranslationIndex
Treffer http://de.archive.ubuntu.com precise/main Translation-de
Treffer http://de.archive.ubuntu.com precise/main Translation-en
Treffer http://de.archive.ubuntu.com precise/multiverse Translation-de
Treffer http://de.archive.ubuntu.com precise/multiverse Translation-en
Treffer http://de.archive.ubuntu.com precise/restricted Translation-de
Treffer http://de.archive.ubuntu.com precise/restricted Translation-en
Treffer http://de.archive.ubuntu.com precise/universe Translation-de
Treffer http://de.archive.ubuntu.com precise/universe Translation-en
                                 
Es werden keine Pakete installiert, aktualisiert oder entfernt.
0 Pakete aktualisiert, 0 zusätzlich installiert, 0 werden entfernt und 0 nicht aktualisiert.
0 B an Archiven müssen heruntergeladen werden. Nach dem Entpacken werden 0 B zusätzlich belegt sein.                                                
root@ReelBox:~# 


```
 bye
stschulze

---

### Post by Frogs Hair on 2014-01-14
You might have to preform an end of life upgrade with the 10.04 desktop repositories closed . [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by stschulze on 2014-01-14
thanks, but i think after upgrade i'm on a 12.04 system, but the login message isn't changed. you don't think so ... repository's on precise and aptitude and apt-get say ... no more updates after upgrading system ...

the eol-repository dont work. i get error on start of upgrade.

---

### Post by stschulze on 2014-01-15
Sinne Upgrade i have answered some questions with N= Use Old file

because These i have the Problem. If i anser with Y, Login Shows 12.04 ....

---

### Post by steve103 on 2014-04-18
> **Frogs Hair said:**
> You might have to preform an end of life upgrade with the 10.04 desktop repositories closed . [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Hmmm... I've had a read - at one point, it looked promising - but I think it is a guide to upgrading elder systems than mine...  Yesterday, before 14.04 was released, I was running the latest Long Term Support version: 12.04.4:
[INDENT][FONT=courier new]**# lsb_release -a**[/FONT][/INDENT]
[INDENT][FONT=courier new]No LSB modules are available.[/FONT][/INDENT]
[INDENT][FONT=courier new]Distributor ID: Ubuntu[/FONT][/INDENT]
[INDENT][FONT=courier new]Description:    Ubuntu 12.04.4 LTS[/FONT][/INDENT]
[INDENT][FONT=courier new]Release:        12.04[/FONT][/INDENT]
[INDENT][FONT=courier new]Codename:       precise[/FONT][/INDENT]
[INDENT][FONT=courier new]**# **
[/FONT][/INDENT]

So, up until yesterday - the 17th April - there was no LTS upgrade path open to me.  It seems weird that I should need to do a special "EOLUpgrade" today.  In favour of the idea, the Ubuntu Releases page (found via the EOLUpgrades page) states that 12.04.4 goes EOL this monht (i.e April 2014) but doesn't specify a date.  Against the idea, the EOLUpgrades page seems to have no relevant information detailing how to transition from 12.04.4 to 14.04 - which, I expect, would be the most common upgrade path for production servers.

Am I overlooking something specific on the EOLupgrades page?

[ **Whoops**  I replied thinking I was reading a different thread... :-S ]

---

