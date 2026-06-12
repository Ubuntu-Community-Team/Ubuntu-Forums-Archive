---
title: "Problem installing from multiverse"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by georgefairbanks on 2008-05-20
I have multiverse enabled but cannot install argouml.  It appears in the local listing for packages but aptitude (and apt-get) cannot see it.  Thoughts?

1.  argouml not found for installation

```

# aptitude install argouml                                                       (05-20 10:01)
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package matching "argouml".  However, the following
packages contain "argouml" in their description:
  libdtdparser-java libocl-argo-java libgef-java libnsuml-java libi18n-java
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

```

2.  Yet multiverse enabled

```

# grep multiverse /etc/apt/sources.list                                          (05-20 10:04)
## multiverse WILL NOT receive any review or updates from the Ubuntu
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

3.  And apt knows about it in its local listing

```

# grep argouml /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_gutsy_multiverse_source_Sources
Package: argouml
Binary: argouml, argouml-doc
Directory: pool/multiverse/a/argouml
 075be770f2986769a64408a8d2b9dab0 956 argouml_0.19.6-2.1.dsc
 ae056e94dbe9b8d8b63f4012bca169d9 4349738 argouml_0.19.6.orig.tar.gz
 bc08fcc5af97fbccc2f8a5de1fea5093 7337 argouml_0.19.6-2.1.diff.gz

```

---

### Post by dstew on 2008-05-20
Those are source packages, not binary packages. Try **apt-get source argouml**.

---

### Post by georgefairbanks on 2008-05-20
Thanks!

---

