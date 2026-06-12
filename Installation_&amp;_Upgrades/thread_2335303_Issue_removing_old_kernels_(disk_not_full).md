---
title: "Issue removing old kernels (disk not full)"
date: 2016-08-27
forum: Installation &amp; Upgrades
---

### Post by miked87 on 2016-08-27
I have gone back and removed all but one of the legacy kernels installed on my (fairly fresh) installation of 16.04 however one is refusing to be installed citing a dependency issue. Note that I have plenty of space (~350M) in /boot.

```
dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r)
```

yields ...
```

pi  linux-image-4.4.0-34-generic                4.4.0-34.53                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
```

When I try and --purge the old kernel ...

```
dpkg: dependency problems prevent removal of linux-image-extra-4.4.0-34-generic:
 linux-image-generic depends on linux-image-extra-4.4.0-34-generic.

dpkg: error processing package linux-image-extra-4.4.0-34-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-extra-4.4.0-34-generic

```

When I try and remove linux-image-generic, I get ...
```
dpkg: dependency problems prevent removal of linux-image-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.34.36).

dpkg: error processing package linux-image-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-generic
```

Which seems somewhat a circular dependency. Note that I am booting into the following kernel:
```
uname -r
4.7.2-040702-generic
```

Note that I removed kernels both older and more recent than 4.4.0.34.36 without issue, but some reason this one doesn't want to leave.

Thanks,
Mike

---

### Post by ubfan1 on 2016-08-27
Did you try any of the --force-thing options, like maybe --force-remove-reinstreq  ?

---

### Post by Impavidus on 2016-08-27
No circular dependencies here.

linux-generic is a metapackage depending on linux-image-generic

linux-image-generic is a metapackage depending on the latest linux-image-4.4.0-**-generic and linux-image-extra-4.4.0-**-generic. The latest version is 4.4.0-34.

The linux-generic and linux-image-generic packages make sure you automatically get the latest kernel that has been packaged and tested for your release of Ubuntu. This indirect arrangement was chosen so that the old kernel doesn't get uninstalled automatically. You run a different kernel, 4.7.2. I'm not so sure this can still be called a fairly fresh installation of Ubuntu 16.04, but it's possible. You must have installed it in some other way.

If you wish to get rid of the 4.4.0 kernel series, you have to uninstall linux-generic, linux-image-generic and linux-headers-generic, all of which are metapackages (=packages that have dependencies, but no contents). Also make sure that you get the kernel updates and headers (if you need those) for the 4.7 kernel.

---

### Post by miked87 on 2016-08-27
Thank you. This makes sense and addressed the issue. Do metapackages exist and are installed only for the 'official' Ubuntu distribution kernel releases ... as apposed to all kernel releases? 

Note that by 'fresh install' I mean I installed 16.04 on new partitions < 2w ago ... after which I immediately upgraded the kernel to the newest stable version.

Being new to both Linux and this forum ... how do I mark a thread as 'solved'?

Mike

---

### Post by wildmanne39 on 2016-08-28
Go to thread tools at the top of the thread and you can mark it solved from there.

---

