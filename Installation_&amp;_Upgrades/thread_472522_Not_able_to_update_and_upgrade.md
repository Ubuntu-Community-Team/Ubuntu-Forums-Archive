---
title: "Not able to update and upgrade"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by badguitarist on 2007-06-13
Hi,

I am facing a lot of problems with my ubuntu 6.06 desktop. Firstly i am unable to run the synaptic package manager as it says there are broken packages on the system. When i use the broken filter to view them, it shows the following packages;

libc6-dev
libc6-i386

I am not able to fix these packages.

Also when i run update, here is the error i am getting towards the end.

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/Release](http://wine.budgetdedicated.com/apt/dists/dapper/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

When i run sudo apt-get install -f  ....this is the error that is showing,

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6.ds1-13) but 2.3.6-0ubuntu20.4 is installed
  libc6-i386: Depends: libc6 (= 2.3.6.ds1-13) but 2.3.6-0ubuntu20.4 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Also none of the office applications are working on my system. I am using AMD64 bit system with ubuntu6.06 64 bit version.

The system seems to be in a mess and i don't know what all are wrong in it. Please throw some light into my problems and how to fix them. Thanks.

---

### Post by moffa on 2007-06-13
Try using aptitude to fix it ```
 sudo aptitude install -f 
```

Also please check your repositories, since the Wine repository you are using is only for the i386 architecture.  You should deactivate any extra repositories that are not for your architecture (ie you're probably using a i386 repository even though you are using the amd64 architecture) since the only 64-bit repository for Ubuntu only works for 7.04.

---

### Post by badguitarist on 2007-06-13
Hey...i've removed the unwanted repositories and tried running sudo apt-get install -f...i am still getting these errors about the broken packages.

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6.ds1-13) but 2.3.6-0ubuntu20.4 is installed
  libc6-i386: Depends: libc6 (= 2.3.6.ds1-13) but 2.3.6-0ubuntu20.4 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

the "Fix broken Packages" link on the synaptic package manager is also generating the same errror

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Can you please tell me what should i do about this error?...

---

