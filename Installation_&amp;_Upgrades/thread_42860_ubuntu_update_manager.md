---
title: "ubuntu update manager"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by James_Black on 2005-06-19
When I start the Ubuntu Update Manager, I get this message:

```
Your system has broken packages!

This means that some dependencies of the installed packages are not satisfied. Please use "Synaptic" or "apt-get" to fix the situation.
``` 

When I hit "OK" I get this message:

```

Failed to run /usr/bin/update-manager:
Child terminated with 1 status
```

What is wrong, because it used to work before? This is what I have in my sources.list:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main

## Backports
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted
deb http://backports.ubuntuforums.org/ubp hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/ubp hoary-extras main universe multiverse restricted 
```

---

### Post by Xian on 2005-06-19
Two Options: You can fix your broken packages with APT or you can open Synaptic with the command line and from the main menu goto Edit > Fix Broken Packages.

1.
```
$ sudo apt-get -f install
```
2. ```
 $ sudo synaptic
```

---

