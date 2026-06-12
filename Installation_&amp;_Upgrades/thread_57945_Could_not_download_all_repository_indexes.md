---
title: "Could not download all repository indexes"
date: 2005-08-18
forum: Installation &amp; Upgrades
---

### Post by munchkina on 2005-08-18
](*,) 

I am getting error messages trying to update my packages. What's going on there?
I tried to reload packages with Synaptic and got these:

** Could not download all repository indexes**

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz:) 401 Authorization Required

The following problems were found on your system:

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)

WHAT do I do now?  :-s

---

### Post by heimo on 2005-08-18
Read this:
[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

You need to change your sources.list to use mirrors.

---

### Post by munchkina on 2005-08-18
:grin: 
Thank you, cannot wait to get home to do this!
Thank you!

---

