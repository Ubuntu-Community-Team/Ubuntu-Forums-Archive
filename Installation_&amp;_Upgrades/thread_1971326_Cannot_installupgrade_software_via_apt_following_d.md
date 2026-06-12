---
title: "Cannot install/upgrade software via apt following do-release-upgrade"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by wfurn on 2012-05-02
I've just attempted to upgrade from Oneiric to Precise using do-release-upgrade -d.  Only 3 packages were upgraded during the process (relating to acrobat and flash).  My /etc/apt/sources.list has been updated so it no longer contains any references to 'oneiric' but /etc/lsb-release tells me that I'm still running the older release.  

I'm now no longer able to upgrade or install new software via apt:

root@guava:~# apt-get install musescore
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package musescore is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'musescore' has no installation candidate
root@guava:~# apt-cache policy musescore
musescore:
  Installed: (none)
  Candidate: (none)
  Version table:
     1.2+dfsg-1 0
        -10 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe amd64 Packages
root@guava:~# grep precise /etc/apt/sources.list | grep universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe

Whilst running Oneiric I'd previously been using apt-pinning to grab versions of certain packages from the Precise repos but all that's been deliberately disabled now.  

Has anyone any ideas as to what the problem might be?

Regards,

Will Furnass

---

### Post by zvacet on 2012-05-02
If your source list is updated try with

```
sudo apt-get update && sudo apt-get upgrade
```

---

