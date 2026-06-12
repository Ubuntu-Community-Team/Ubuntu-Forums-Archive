---
title: "apt-get update &amp;&amp; apt-get upgrade does not install security updates"
date: 2015-12-02
forum: Installation &amp; Upgrades
---

### Post by ken18 on 2015-12-02
Ubuntu 14.04 - I'm trying to be a good Linux citizen by using the command line to check for and install updates on a regular basis.  But, for some reason, security updates aren't being installed.  I still get the green software updater icon that tells me there are 65MB worth of security updates to be installed.  What am I doing wrong?

---

### Post by ian-weisser on 2015-12-02
Please show us the complete output of the command.

---

### Post by ken18 on 2015-12-02
Thanks for your reply.  OK, here is the output:

```
Ign file:  InRelease
Get:1 file:  Release.gpg [181 B]
Get:2 file:  Release [196 B]
Ign file:  Translation-en_US
Ign file:  Translation-en
Ign http://us.archive.ubuntu.com trusty InRelease
Hit http://security.ubuntu.com trusty-security InRelease
Hit http://us.archive.ubuntu.com trusty-updates InRelease
Hit http://security.ubuntu.com trusty-security/main Sources
Ign http://archive.canonical.com trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease
Hit http://us.archive.ubuntu.com trusty-backports InRelease
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://archive.canonical.com trusty Release.gpg
Hit http://extras.ubuntu.com trusty Release.gpg
Hit http://security.ubuntu.com trusty-security/universe Sources
Hit http://us.archive.ubuntu.com trusty-updates/main Sources
Hit http://security.ubuntu.com trusty-security/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://archive.canonical.com trusty Release
Hit http://extras.ubuntu.com trusty Release
Hit http://security.ubuntu.com trusty-security/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://archive.canonical.com trusty/partner Sources
Hit http://extras.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://archive.canonical.com trusty/partner amd64 Packages
Hit http://extras.ubuntu.com trusty/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://archive.canonical.com trusty/partner i386 Packages
Hit http://extras.ubuntu.com trusty/main i386 Packages
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://archive.canonical.com trusty/partner Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Ign http://extras.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://us.archive.ubuntu.com trusty Release
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  linux-generic-lts-vivid linux-headers-generic-lts-vivid
  linux-image-generic-lts-vivid linux-signed-generic-lts-vivid
  linux-signed-image-generic-lts-vivid
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
```

---

### Post by grahammechanical on 2015-12-02
You are doing nothing wrong. These are kernel upgrades

> The following packages have been kept back:
  linux-generic-lts-vivid linux-headers-generic-lts-vivid
  linux-image-generic-lts-vivid linux-signed-generic-lts-vivid
  linux-signed-image-generic-lts-vivid

And they are kept back because the developers are not yet ready to release them. Perhaps there are other packages that need to be upgraded along with them. I am running the development version of 16.04. I update daily and I have the proposed repository enabled which should mean that I get updated packages before that are put into the stable update channel and right now I have 174 packages being held back including an upgrade to the kernel.

I could force those held back packages to be installed by running this command

```
sudo apt-get dist-upgrade
```

but doing that increases the risk of breakage because apt-get dist-upgrade will force the installation of those packages even by removing other packages. So, forcing the installation of that kernel upgrade may not cause problems but if it does then use the Grub boot menu Advanced options for Ubuntu to load into a previous kernel and then daily update/upgrade until the problem is fixed.

Regards.

---

### Post by kostkon on 2015-12-03
You can't install them with apt-get update either because the kernel updates always count as new packages or those are [phased updates]("http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04").

---

### Post by efflandt on 2015-12-06
See "man apt-get" (without quotes in a terminal) and the difference between "upgrade" and "dist-upgrade" (which updates current distribution, not to different Ubuntu version without doing something additional). "upgrade" just upgrades existing packages (but not any with changing dependencies). "dist-upgrade" is smarter about also upgrading packages that have changed or have new dependencies.

So unless you have some particular reason to use "upgrade" (which may hold back packages), to stay up to date with everything in your current Ubuntu version (similar to gui Software Updater) use "dist-upgrade" instead.

---

### Post by ken18 on 2015-12-09
Using 'dist-upgrade' instead of 'upgrade' installed the security updates.  I've always used 'upgrade' because the detailed instructions I've seen over the years to install specific packages use it. 

From a previous post in this thread, it sound's like 'dist-upgrade' can be dangerous if you are less than an expert user:

```
[COLOR=#000000] ...increases the risk of breakage because apt-get dist-upgrade will force the installation of those packages even by removing other packages...[/COLOR]
```

---

### Post by ian-weisser on 2015-12-09
Many shell commands may be dangerous if misused or misunderstood.
The shell does not have a safety net. Users sometimes fall.

Ordinary 'upgrade' is fine to use for most usage. Only kernel packages require 'dist-upgrade'. There are several good reasons for the difference...that mostly boil down to protecting you from surprise breakage.

---

