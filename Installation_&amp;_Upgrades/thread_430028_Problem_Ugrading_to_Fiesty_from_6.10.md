---
title: "Problem Ugrading to Fiesty from 6.10"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by Aktrop on 2007-05-01
When upgrading using the Update Manager, I get the error message that it failed to get some packages (two are specificed, though cut and past doesn't seem to work, so I can't tell you what they are!) - it says there is some network problem (though my Internet connection seems to work just fine!).

Any help would be great!

---

### Post by zvacet on 2007-05-02
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by Aktrop on 2007-05-02
I tried that, but no help. I get the same error message when I try to upgrade via update manager:

Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Please help!!:confused:

---

