---
title: "Dapper to Hardy: update-manager -d offers a bunch of packages"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by candlerb on 2008-11-19
I am trying to upgrade a Dapper system to Hardy.

If I uncomment the dapper-updates line in /etc/apt/sources.list and then sudo update-manager -d, instead of getting a button which says "New distribution release available" it instead offers me 51 new packages, totalling 155MB of download.

I am wondering if it is safe to proceed, or there is something wrong with my system which prevents a distribution upgrade from working. The base ubuntu packages appear to be present as far as I can tell:

```

$ dpkg-query -l | grep ubuntu-
ii  ubuntu-artwork                         28                Ubuntu themes and artwork
ii  ubuntu-base                            0.120                The Ubuntu base system (transitional package
ii  ubuntu-desktop                         0.120                The Ubuntu desktop system
ii  ubuntu-docs                            6.06.2                The Ubuntu Documentation Project
ii  ubuntu-keyring                         2005.01.12.1                GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal                         0.120                Minimal core of Ubuntu
ii  ubuntu-sounds                          0.3                Ubuntu's GNOME audio theme
ii  ubuntu-standard                        0.120                The Ubuntu standard system

```

and I don't know how else I might have broken it.

My /etc/apt/sources.list is attached, with the dapper-updates lines commented back out.

This system *does* receive security updates from time to time, and these all get applied.

Should I investigate the problem further, or just press the button to take these 155MB of updates? It doesn't seem right, and I don't want to end up in a situation where I have neither a complete Dapper nor a complete Hardy.

Any pointers for where I should look are appreciated. All the pages I've read about upgrading Dapper to Hardy just say that update-manager -d will show a release upgrade button.

Thanks,

Brian Candler.

---

### Post by overdrank on 2008-11-19
Hi and as I understand it from here
[https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS](https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS)
When you activate the repo then update the system then after the update you will use the command gksu update-manager then you will have the option to upgrade to Hardy 8.04

---

### Post by candlerb on 2008-11-19
[https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS](https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS)

Thanks - that's one of the pages I was following, but it still doesn't make it clear to me what to expect.

My system *was* fully up-to-date. Then I enabled dapper-updates, and then I got offered 51 new updates. These updates include core stuff like gzip and base-files.

Is it normal to have to do this (apparently) partial update, *then* do a distro upgrade to 8.04?

What would happen if I took these 51 packages, but then declined to take the distro upgrade later? Would I have a system which is neither Dapper nor Hardy?

Put another way: are these 51 updated packages part of Dapper, or part of Hardy? If they're part of Dapper, why wasn't I offered them before? Perhaps because I didn't have dapper-updates enabled?

In that case, should I, as a Dapper user, have had dapper-updates enabled all along? Have I been missing important updates over the last 2 years? Are these updates somehow "nice-to-have", but not "critical" like the ones I got through the security updates channel?

---

### Post by candlerb on 2008-11-26
OK, I bit the bullet: I enabled dapper-updates, took the 51 updates, and rebooted as it asked.

Now update-manager -d offers me 8.04, but when it starts I get a load of errors about hash sum mismatches:

```

W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2  Hash Sum mismatch
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.

```

Googling around, there seem to be two solutions offered:

(1) Change to the master repositories (i.e. not a mirror)

(2) Do some command-line magic:

sudo aptitude upgrade
sudo aptitude dist-upgrade
sudo aptitude install update-manager-core
sudo do-release-upgrade

I tried (1) by removing the gb. prefixes from all the sources. Same error. So I put /etc/apt/sources.list back how it was.

I tried (2). The first two updated zero packages. The third line said: "Couldn't find any package whose name or description matched "update-manager-core". Not surprisingly, the fourth line failed with command not found.

But after this I tried gksu "update-manager" (without the -d), and for some reason it worked! At least, it's now in the process of downloading 1,479 files.

Bizarre, but it looks like problem is solved.

For completeness, here is my /etc/apt/sources.list just before the upgrade.

```

deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## MAJOR BUG FIX UPDATES
## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## UNIVERSE
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## BACKPORTS
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

## SECURITY
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

## OTHERS
# deb http://debian.slimdevices.com stable main
# deb http://packages.freecontrib.org/plf/ dapper free non-free

```

---

### Post by artifex on 2008-12-04
I've jumped on this bandwagon as well. Everything goes fine at upgrade with do-release-upgrade but I have a lot of 'ri' packages with 'dpkg --list' like this:

```
ri  zoo                         2.10-20                     manipulate zoo archives

```

What this ri means and how to correct it? I've read some dpkg manuals but found no description of that. The problem really raises at php5-mcrypt. dpkg --list shows php5-mcrypt but php does not find this extension and 'apt-get install' says that I have the latest version. Finally I have to remove and install php5 again. So this status means some unhealthy things to me and I would like to solve it.

---

### Post by candlerb on 2008-12-04
> **artifex said:**
> What this ri means and how to correct it?

The meaning of the flags is shown, somewhat cryptically, at the top of the dpkg-query output:

```

$ dpkg-query -l | head -3
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)

```

So it looks like requested for removal, but currently installed. I don't know why though (dependencies?) 'dpkg-query --status pkgname' may give you more info.

---

### Post by candlerb on 2008-12-04
Also, maybe you need to enable 'hardy universe' and 'hardy-security universe' in /etc/apt/sources.list. My machine says:

```

$ apt-cache showpkg zoo
Package: zoo
Versions: 
2.10-20 (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages
                  MD5: e26ba1e8123629679188f5a049095c25


Reverse Depends: 
  ark,zoo
  mikmod,zoo
  ark,zoo
  amavisd-new,zoo
Dependencies: 
2.10-20 - libc6 (2 2.6.1-1) 
Provides: 
2.10-20 - 
Reverse Provides: 

```

I did have some problems before enabling universe.

---

### Post by artifex on 2008-12-05
Thanks for your answers!

> **candlerb said:**
> So it looks like requested for removal, but currently installed. I don't know why though (dependencies?) 'dpkg-query --status pkgname' may give you more info.
Displays the following:
```
Package: zoo
Status: deinstall ok installed
Priority: optional
Section: utils
Installed-Size: 156
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 2.10-20
Depends: libc6 (>= 2.6.1-1)
Description: manipulate zoo archives
```
Looks normal for me. I think do-release-upgrade care about the order of package installation so dependencies are handled through upgrade process. For example php5 package installed before php5-* modules. May I wrong?

> **candlerb said:**
> Also, maybe you need to enable 'hardy universe' and 'hardy-security universe' in /etc/apt/sources.list.
Both were enabled.

---

