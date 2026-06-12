---
title: "dpkg-deb error: Unexpected number of arguments to --control"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by Laysan_A on 2010-03-01
Hi, 
I just upgraded from jaunty and somewhere in the process (or just after, I'm no longer sure just when it started) I started getting this error whenever I try to install or upgrade a package. 

Some of my software isn't working properly - some won't even load - so I'm not sure if the installations are actually succeeding, or not. But apt-get install -f shows nothing but a list of stuff I need to autoremove (mostly dev files). 

This particular message is the output of the details tab in synaptic, but I've gotten the same thing in terminal from apt-get. 


> dpkg-deb: --control /var/cache/apt/archives/dpkg-awk_1.0.3_all.deb /var/lib/dpkg/tmp.ci
Selecting previously deselected package dpkg-awk.
(Reading database ... 415515 files and directories currently installed.)
Unpacking dpkg-awk (from .../dpkg-awk_1.0.3_all.deb) ...
dpkg-deb: --fsys-tarfile /var/cache/apt/archives/dpkg-awk_1.0.3_all.deb
Processing triggers for man-db ...
Setting up dpkg-awk (1.0.3) ...
dpkg-deb: --control -- /var/cache/apt/archives/binutils_2.20-0ubuntu2_amd64.deb /tmp/3WTX1yBFq8/DEBIAN
Unexpected number of arguments to --control
debsums: can't extract control info from /var/cache/apt/archives/binutils_2.20-0ubuntu2_amd64.deb
E: Problem executing scripts DPkg::Post-Invoke 'if [ -x /usr/bin/debsums ]; then /usr/bin/debsums --generate=nocheck -sp /var/cache/apt/archives; fi'
E: Sub-process returned an error code
A package failed to install.  Trying to recover:Thanks!

---

### Post by Soul-Sing on 2010-03-01
try these threads please: [http://ubuntuforums.org/showthread.php?t=1336548](http://ubuntuforums.org/showthread.php?t=1336548)
[http://www.khattam.info/2009/08/04/s...tatus-2-error/](http://www.khattam.info/2009/08/04/s...tatus-2-error/)
[https://bugs.launchpad.net/ubuntu/+s...ic/+bug/374136](https://bugs.launchpad.net/ubuntu/+s...ic/+bug/374136)

---

### Post by Laysan_A on 2010-03-01
Thanks for your swift reply leoquant. I checked the links you gave me and the first doesn't seem to be quite the same issue - unless I'm missing something. The second and third are broken.

---

### Post by Laysan_A on 2010-03-02
> try these threads please: [http://ubuntuforums.org/showthread.php?t=1336548](http://ubuntuforums.org/showthread.php?t=1336548)
[http://www.khattam.info/2009/08/04/s...tatus-2-error/](http://www.khattam.info/2009/08/04/s...tatus-2-error/)
[https://bugs.launchpad.net/ubuntu/+s...ic/+bug/374136](https://bugs.launchpad.net/ubuntu/+s...ic/+bug/374136)

Okay, I searched for these posts on their respective sites and found them. Apparently your links were incomplete or something. All these posts seem to relate to individual packages with failed installs, and the fixes describe how to get rid of them and reinstall them. All involve an error code 2 in the post installation script.

My problem shows up when I try to install/uninstall anything. It doesn't seem to involve any particular package, unless it's apt, and I don't get an error code 2. I admit I'm pretty ignorant when it comes to code issues, but I don't think we're quite on the same page here...
[]("https://bugs.launchpad.net/ubuntu/+s...ic/+bug/374136")

---

