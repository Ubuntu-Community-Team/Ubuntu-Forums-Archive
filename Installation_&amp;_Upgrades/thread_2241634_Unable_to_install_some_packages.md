---
title: "Unable to install some packages"
date: 2014-08-27
forum: Installation &amp; Upgrades
---

### Post by alfirdaous on 2014-08-27
Hello everyone,

I am unable to install packages, I've got theses errors:

```

Err http://ma.archive.ubuntu.com/ubuntu/ quantal-updates/universe python-compizconfig i386 1:0.9.8.6-0ubuntu1
  404  Not Found [IP: 91.189.88.153 80]
Fetched 1,023 kB in 22s (46.1 kB/s)                                                                                                  
Failed to fetch http://ma.archive.ubuntu.com/ubuntu/pool/main/g/gconf/gir1.2-gconf-2.0_3.2.5-0ubuntu4_i386.deb  404  Not Found [IP: 91.189.88.153 80]
Failed to fetch http://ma.archive.ubuntu.com/ubuntu/pool/universe/c/compiz/python-compizconfig_0.9.8.6-0ubuntu1_i386.deb  404  Not Found [IP: 91.189.88.153 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Thanks in advance

---

### Post by TheFu on 2014-08-27
12.10 support ended in May. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)  
Either move to 12.04 or 14.04.

Also - please show the exact command entered when asking for help.  Is the system fully up-to-date with all patches?

---

### Post by alfirdaous on 2014-08-27
I think 14.04 has some issues, and I now used the below one (part of the errors):

```

root@alfirdaous:/home/alfirdaous# apt-get update && apt-get -y upgrade

W: Failed to fetch http://ma.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://ma.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://ma.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by TheFu on 2014-08-27
Looks like the repo has removed 12.10 files.
[http://ma.archive.ubuntu.com/ubuntu/dists/](http://ma.archive.ubuntu.com/ubuntu/dists/)

You can point to a different repo, if you like, but ...

Again - it is time to move to 1204 or 1404.

---

### Post by QIII on 2014-08-27
All releases have "issues".  It is the nature of the beast for Ubuntu, other Linux distros, Windows, OS X, BSD, etc.

Please see [this]("http://ubuntuforums.org/showthread.php?t=2229730").   

The staff recommends a fresh installation of a supported release (12.04 or 14.04 at this time) and no longer supports requests for support for non-supported releases.  We would rather that members focus their time on supported releases rather than on releases that have passed their EOL (End of Life).

Please feel free to start a new thread if you need help doing a fresh installation and would like to preserve your important files.

Thread closed.

---

