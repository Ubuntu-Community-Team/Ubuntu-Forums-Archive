---
title: "huge apt-get problem, can't work around . . ."
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by rmmst49 on 2007-03-22
Dapper x86

also, this is a work machine, so i would REALLY not have to reinstall my OS to fix this problem.  However, this error is killing me and i will have to reinstall from scratch if i can't work this one out.

can anyone point out my error or show me how to resolve this error?  apt-get is stuck, i cannot install or remove anything without giving me the same 

xfonts-intl-european
E: Sub-process /usr/bin/dpkg returned an error code (1)

error.

any help GREATLY appreciated.  Thanks

```
root@prak:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  xfonts-intl-european
The following packages will be upgraded:
  file libmagic1 libmysqlclient15off mysql-common
4 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/1716kB of archives.
After unpacking 315kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 277481 files and directories currently installed.)
Removing xfonts-intl-european ...
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exit
dpkg: error processing xfonts-intl-european (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xfonts-intl-european
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

/etc/apt/sources.list

```
####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main

deb http://archive.ubuntu.com/ubuntu dapper restricted
deb-src http://archive.ubuntu.com/ubuntu dapper restricted

deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main

deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main

deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
#deb http://archive.ubuntu.com/ubuntu dapper-backports main
#deb-src http://archive.ubuntu.com/ubuntu dapper-backports main

#deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
#deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu dapper-backports universe
#deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

#deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
#deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main
```

---

### Post by zvacet on 2007-03-22
Move # from your deb backports (for example:#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main   to deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main).Synaptic>edit>fix broken packages
Try again.And if it is don´t work try 
```
sudo dpkg --configure -a
```

---

### Post by someone7663663 on 2007-03-23
Im having a very similar problem. If anyone can find a solution to this and post it, that would rock!

---

### Post by mverrilli on 2007-03-24
* Edit, oops, I'm having this trouble, but in Feisty, I was using search and forgot to check what subforum I was in.

---

