---
title: "Cannot upgrade - Error code 2"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by spincycle on 2006-10-29
Trying to upgrade on my Dell (upgrade worked fine on my L2000 AMD64), but cannot upgrade on desktop.  Consistently get the follow:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Have tried rebooting too.

Help :-)  ](*,) 

Thanks.

jim

---

### Post by nimrod_abing on 2006-10-29
> **spincycle said:**
> Trying to upgrade on my Dell (upgrade worked fine on my L2000 AMD64), but cannot upgrade on desktop.  Consistently get the follow:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)


Are these all the error messages you get? Because I just tried clicking on the links above and the Packages.bz2 downloads fine. You should try it again. If still fails with the same errors, then make sure have enough disk space in the partition that holds your /var directory.

---

### Post by spincycle on 2006-10-29
Thanks Nimrod.  Actually, those are the only messages I get.  I have plenty of disk space, and I have tried a few times.  However, I was able to solve the problem -- but don't really understand why.

The issue was clearly with one of the repositories, and the links worked, yet I didn't know which respository was the problem.  So, I went into Synaptic Package Manager, and de-selected every repository that was not "officially supported", and that did the trick!?!

Take care,

Jim

---

### Post by reyfer on 2006-10-30
> **spincycle said:**
> Trying to upgrade on my Dell (upgrade worked fine on my L2000 AMD64), but cannot upgrade on desktop.  Consistently get the follow:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Have tried rebooting too.

Help :-)  ](*,) 

Thanks.

jim

Just one question: why are you trying to upgrade from dapper to dapper? the links you posted both refer to dapper, not edgy. Did you change the sources.list so every instance of dapper reads edgy now?

---

### Post by spincycle on 2006-10-30
Hi Reyfer,  I'm not trying to upgrade from dapper to dapper.  I ran the upgrade to edgy (6.10), the fact that it spit out those links suggests there is a bug in the install process.

As I said, I was able to correct it by removing all unofficial repositories and re-running it.

Thanks.

jim

---

