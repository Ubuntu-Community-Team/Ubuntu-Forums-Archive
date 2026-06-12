---
title: "GCC and CPP dependency problems."
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by strm on 2007-05-13
Hello,
after attempting to install VLC-media player and running into some dependency problems I eventually ran into the following when running **apt-get -f install**:

```

root@lms-desktop:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  cpp-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed
  gcc-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed
  libgcc1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed
  libstdc++6: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

any simple suggestions on fixing these dependencies that does not involve completely removing all of the above packages and everything dependent on them then reinstalling them?

ps. i know i'm logged in as root, i'm new to ubuntu so that was the first thing i did.
ps2. i searched the forum for this topic and couldnt spot anything at first glance but forgive me if this has already been solved elsewhere.

---

### Post by taurus on 2007-05-13
How did you install gcc?  Did you install gcc as it or did you actually install the build-essential package?

can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by strm on 2007-05-20
I hadn't touched GCC since the fresh install of Ubuntu (edgy 6.10).
Heres my sources.list:
```

root@lms-desktop:/etc/apt# pwd
/etc/apt
root@lms-desktop:/etc/apt# cat sources.list

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
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
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

---

### Post by taurus on 2007-05-20
What happens when you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by strm on 2007-05-20
aptitude update
aptitude install build-essential

fixed the dependency problem, however i believe it downgraded some of the packages.

thanks.

---

