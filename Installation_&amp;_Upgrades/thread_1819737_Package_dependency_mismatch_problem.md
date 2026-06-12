---
title: "Package dependency mismatch problem"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by lagerratrobe on 2011-08-06
Hi All,

I've been having a consistent problem installing packages to my 64-bit Maverick box that I can't seem to find a solution for.  Basically, I seem to have a version mismatch between what I have installed on the machine, and what is available via the repositories I have enabled.  Here's an example:

```
$ sudo apt-get install libtiff4-dev

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libtiff4-dev : Depends: libtiff4 (= 3.9.4-2) but 3.9.4-2ubuntu0.4 is to be installed
E: Broken packages
```

This is driving me a bit crazy and in the past I have gone out and found the different minor release version of the package, downloaded it, and then installed it manually with synaptic.  This is NOT what I want to keep doing though, and if it's possible for me to *fix* the version mismatch somehow, I'd like to do that.  Here is some info that might be useful.

OS info:

```
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
```

Current repositories:

```
$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu/ maverick main restricted

#deb http://archive.ubuntu.com/ubuntu/ maverick universe
#deb-src http://archive.ubuntu.com/ubuntu/ maverick universe

#deb http://archive.ubuntu.com/ubuntu/ maverick multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ maverick multiverse

#deb http://archive.canonical.com/ubuntu maverick partner
#deb-src http://archive.canonical.com/ubuntu maverick partner

# MongoDB repo
deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen
```

If anyone an advise me how to get out of this mess, I'd appreciate it.

Roger

---

