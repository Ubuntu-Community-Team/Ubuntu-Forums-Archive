---
title: "apt-get update issues"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by maindoor on 2007-12-13
just did a sudo apt-get update and gzip is reporting some errors.
tried running gzip on a local file, works fine. opened adept-manager
list of packages listed is very less. Has someone faced this issue ?

Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Sources
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages [4912kB]
99% [3 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Sources
Fetched 191B in 4s (46B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
skumar@skumar:~/Desktop/cvsup/cvsup-snap-16.1h$


Regards,
maindoor.

---

### Post by PmDematagoda on 2007-12-13
Post the results of:-

```
cat /etc/apt/sources.list
```

---

### Post by maindoor on 2007-12-13
Thanks for getting back on this so soon

$ cat /etc/apt/sources.list

# deb [http://ppa.launchpad.net/avassalotti/ubuntu](http://ppa.launchpad.net/avassalotti/ubuntu) RELEASE main
# deb-src [http://ppa.launchpad.net/avassalotti/ubuntu](http://ppa.launchpad.net/avassalotti/ubuntu) RELEASE main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main universe restricted multiverse

This is what I get:

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages [4912kB]
99% [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Sources
Fetched 191B in 4s (39B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Regards,
Sanjeev.

---

### Post by maindoor on 2007-12-13
anyone's got any clue on this one ?

---

### Post by PmDematagoda on 2007-12-13
I am afraid I do not understand your output of the command I gave you, from the error messages you are supposed to be having more repositories, could you please post the **full** output of:-

```
cat /etc/apt/sources.list
```

---

