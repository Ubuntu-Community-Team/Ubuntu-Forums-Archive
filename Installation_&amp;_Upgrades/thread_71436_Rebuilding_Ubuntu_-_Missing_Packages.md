---
title: "Rebuilding Ubuntu - Missing Packages"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by monkeywork on 2005-10-03
Rebuilding my Hoary box and running into a problem where I am unable to install the following packages:

sun-j2re1.5
w32codecs
acroread-plugin
azureus

Following the guide located here:  [http://ubuntuguide.org](http://ubuntuguide.org)
Can anyone offer suggestions?

my sources.list file is listed below:

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

## Backports
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
#deb http://acm.cs.umn.edu/ubp/ hoary-backports main universe multiverse restricted
deb http://acm.cs.umn.edu/ubp/ hoary-extras main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse

```

---

### Post by wspgeek on 2005-10-03
What do you get when you try running apt-get on any of those packages?

I just posted on a similar problem where a list of dependencies would show up but that they were "uninstallable".

---

### Post by pestie on 2005-10-03
Same problem here. It looks to me like some of those packages don't even exist any more. Here's what I get:
```

# aptitude install azureus
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following packages have unmet dependencies:
azureus: Depends: sun-j2sdk1.5 which is a virtual package. or
java2-runtime which is a virtual package.

```
It looks to me like some packages that used to exist, like w32codecs and the Sun JRE, are now missing from backports. If anyone figures this out, I hope they post here. Situations like this make my head want to explode.

---

