---
title: "install nfs-common fails on ubuntu 13.10"
date: 2015-06-21
forum: Installation &amp; Upgrades
---

### Post by bluethundr2 on 2015-06-21
I'm trying to install nfs-common on ubuntu 13.10

```

#apt-get install nfs-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package nfs-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'nfs-common' has no installation candidate

```

And when I do I get the above error. 

These are the repos that I have enabled:

```

deb http://us-east-1.ec2.archive.ubuntu.com/ubuntu/ saucy main
deb-src http://us-east-1.ec2.archive.ubuntu.com/ubuntu/ saucy main


deb http://us-east-1.ec2.archive.ubuntu.com/ubuntu/ saucy-updates main
deb-src http://us-east-1.ec2.archive.ubuntu.com/ubuntu/ saucy-updates main


deb http://us-east-1.ec2.archive.ubuntu.com/ubuntu/ saucy universe
deb-src http://us-east-1.ec2.archive.ubuntu.com/ubuntu/ saucy universe
deb http://us-east-1.ec2.archive.ubuntu.com/ubuntu/ saucy-updates universe
deb-src http://us-east-1.ec2.archive.ubuntu.com/ubuntu/ saucy-updates universe








deb http://security.ubuntu.com/ubuntu saucy-security main
deb-src http://security.ubuntu.com/ubuntu saucy-security main
deb http://security.ubuntu.com/ubuntu saucy-security universe
deb-src http://security.ubuntu.com/ubuntu saucy-security universe

```

Can someone please help me get past this error so I can install the nfs client on this machine?

Thanks,
Tim

---

### Post by mörgæs on 2015-06-21
13.10 has reached end of life. You should consider a fresh install of 14.04.2 or 15.04.

---

### Post by bluethundr2 on 2015-06-21
I tried to do a do-release-upgrade to go from 13.10 to 14.04.

But I seem to be running into a new issue:

```

Broken ubuntustudio-font-meta:amd64 Depends on xfonts-scalable [ amd64 ] < none -> 1:1.0.3-1 > ( x11 )
  Considering xfonts-scalable:amd64 1 as a solution to ubuntustudio-font-meta:amd64 9999
  Re-Instated xfonts-scalable:amd64
Done




A fatal error occurred


Please report this as a bug and include the files
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in
your report. The upgrade has aborted.
Your original sources.list was saved in
/etc/apt/sources.list.distUpgrade.


Traceback (most recent call last):


File "/tmp/ubuntu-release-upgrader-qukl0a/trusty", line 10, in
<module>
sys.exit(main())


File
"/tmp/ubuntu-release-upgrader-qukl0a/DistUpgrade/DistUpgradeMain.py",
line 244, in main
if app.run():


File
"/tmp/ubuntu-release-upgrader-qukl0a/DistUpgrade/DistUpgradeController.py",
line 1827, in run
return self.fullUpgrade()


File
"/tmp/ubuntu-release-upgrader-qukl0a/DistUpgrade/DistUpgradeController.py",
line 1780, in fullUpgrade
if not self.askDistUpgrade():


File
"/tmp/ubuntu-release-upgrader-qukl0a/DistUpgrade/DistUpgradeController.py",
line 976, in askDistUpgrade
if not self.cache.installTasks(self.tasks):


File
"/tmp/ubuntu-release-upgrader-qukl0a/DistUpgrade/DistUpgradeCache.py",
line 808, in installTasks
pkg.mark_install()


File "/usr/lib/python2.7/dist-packages/apt/package.py", line 1297, in
mark_install
fixer.resolve(True)


SystemError: E:Unable to correct problems, you have held broken
packages.
=== Command detached from window (Sun Jun 21 21:06:45 2015) ===
=== Command terminated with exit status 1 (Sun Jun 21 21:06:45 2015) ===

```

I'd prefer to save the effort of rebuilding my mail server from scratch, if I could get this distribution upgrade to work. Can I have some advice on how to get past this error?

Thanks,
Tim

---

