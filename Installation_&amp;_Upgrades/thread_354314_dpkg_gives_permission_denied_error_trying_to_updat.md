---
title: "dpkg gives permission denied error trying to update after clean edgy installation"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by csalt on 2007-02-05
(Error is at the bottom) I just installed a clean installation of edgy on a new core 2 duo msi machine, with software raid 1. everything went great!

I installed subversion, mysql-server, and a few other packages, then i uncommented the backports, universe and multiverse lines in sources.list:

```
#
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

I then realized that there were a lot of updates that synaptic wanted to install. that's fine, i went for it, it downloaded 170MB of data. then, when it runs, i get this:

```
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/tar_1.15.91-2ubuntu0.3_i386.deb (--unpack):
 unable to open files list file for package `liblcms1': Permission denied
Errors were encountered while processing:
 /var/cache/apt/archives/tar_1.15.91-2ubuntu0.3_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.

```

i tried clearing the cache, downloading again, i tried removing 'liblcms1' which doesn't work because ubuntu-desktop depends on it (but i get the same error anyway). i'm stuck.

any thoughts?

---

