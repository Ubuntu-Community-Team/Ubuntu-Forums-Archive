---
title: "apt-get always shows 0 updates since months"
date: 2016-02-17
forum: Installation &amp; Upgrades
---

### Post by zyHEpEJ on 2016-02-17
Hello,

I have the following problem, that "apt-get update && apt-get dist-upgrade" always shows:

```

Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

This began happen a few months ago and I dont know how to fix this or why it started to happen. I wanted to do a security update today because of the glibc catastrophy.

```

ldd --version
ldd (Ubuntu GLIBC 2.21-0ubuntu4) 2.21

```


I guess that isnt the newest version, [http://www.ubuntu.com/usn/usn-2900-1/](http://www.ubuntu.com/usn/usn-2900-1/) says it should be: 2.21-0ubuntu4.1


My system is:


```

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 15.04
Release:        15.04
Codename:       vivid

```


My /etc/apt/sources.list file:


```

deb http://mirror.de.leaseweb.net/ubuntu/ vivid main restricted
deb-src http://mirror.de.leaseweb.net/ubuntu/ vivid main restricted
deb http://mirror.de.leaseweb.net/ubuntu/ vivid universe
deb-src http://mirror.de.leaseweb.net/ubuntu/ vivid universe
deb http://mirror.de.leaseweb.net/ubuntu/ vivid multiverse
deb-src http://mirror.de.leaseweb.net/ubuntu/ vivid multiverse
deb http://mirror.de.leaseweb.net/ubuntu/ vivid-backports main restricted universe multiverse
deb-src http://mirror.de.leaseweb.net/ubuntu/ vivid-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ vivid-security restricted main universe multiverse
deb http://mirror.de.leaseweb.net/ubuntu/ vivid-updates restricted main universe multiverse

```

---

### Post by PaulW2U on 2016-02-17
Ubuntu 15.04 is now "end of life" - see [Ubuntu 15.04 (Vivid Vervet) End of Life reached on February 4 2016]("https://lists.ubuntu.com/archives/ubuntu-announce/2016-February/000204.html").

The announcement was also posted on these forums: [http://ubuntuforums.org/showthread.php?t=2312517](http://ubuntuforums.org/showthread.php?t=2312517)

The version that you referred to in the USN is for Ubuntu 15.10.

Time to upgrade before 15.04's repositories are moved to "old releases" which will cause you further problems.

---

### Post by zyHEpEJ on 2016-02-17
Shouldn't do apt-get dist-upgrade give option to upgrade to newest stable? But it doesnt. How do I upgrade to 15.10 then without doing a complete new installation?

Edit: Ok kicked in the upgrade with the distribution upgrade tool. Weird, I always thought apt-get dist-upgrade would warn me there was a stable distribution upgrade available.

---

### Post by QIII on 2016-02-17
Because EOL means End Of Life and that means no more support of any kind.  Canonical ceases development on that release.  Completely.  LTS (Long Term Support) releases are supported for 5 years.

dist-upgrade does not take you to the next release.  It upgrades everything in your current release.  do-release-upgrade ugrades to the next release, but you can't do that from an unsupported release.

You could go the route of the "old-releases" upgrade through several other EOL releases, which is nearly certain to end in disaster.  That would be the only way to upgrade from where you are -- and it would most likely not work.

Or you can do a fresh install of a currently supported release.

---

### Post by deadflowr on 2016-02-17
> **zyHEpEJ said:**
> Shouldn't do apt-get dist-upgrade give option to upgrade to newest stable? But it doesnt.

Nope
to do that, it is a different command:
```
do-release-upgrade
```
dist-upgrade simply upgrades packages for the existing release you have.

Edit: ninja'd. maybe I should stop waddling about sometimes.

---

### Post by zyHEpEJ on 2016-02-18
But the command for doing a simple package upgrade is "apt-get upgrade" and I always thought doing a system upgrade, aka going to the next stable system wide release, there was apt-get dist-upgrade for. Thanks for helping though! I am on 15.10 now and all seems to work well.

---

### Post by deadflowr on 2016-02-19
> **zyHEpEJ said:**
> But the command for doing a simple package upgrade is "apt-get upgrade" and I always thought doing a system upgrade, aka going to the next stable system wide release, there was apt-get dist-upgrade for. Thanks for helping though! I am on 15.10 now and all seems to work well.

All apt-get commands run within the same release.
upgrade and dist-upgrade both install updates for the current release in use.
But they do it differently.
upgrade does it safely, and will not install or remove anything not currently installed on the system.
dist-upgrade can and will install new software, sometimes it will need to remove software as well. This can be considered less safe.
From it's manual page
man apt-get:
```
upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.

       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The dist-upgrade
           command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages. 
```

---

