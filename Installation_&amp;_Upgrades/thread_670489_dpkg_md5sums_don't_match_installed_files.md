---
title: "dpkg md5sums don't match installed files"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by chaggy22 on 2008-01-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/183848](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/183848) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				On several systems I've installed with Gutsy, corrupted files show up in the form of some program seg faulting. I've traced it to mismatched MD5SUMS on files from installed packages. Today on one of my machines g++ segfaults compiling a "Hello World" C++ program.

```
$ g++ foo.cpp
g++: Internal error: Segmentation fault (program cc1plus)
...
```

Dpkg shows a correctly installed g++

```
$ dpkg -l g++*
...
ii g++-4.1 4.1.2-16ubuntu2 The GNU C++ compiler
...
```

But a check of the md5sums for the installed files in that package show that cc1plus is corrupt.

```
$ cd /; md5sum -c /var/lib/dpkg/info/g++-4.1.md5sums |grep -v OK$
usr/lib/gcc/x86_64-linux-gnu/4.1/cc1plus: FAILED

$ md5sum /usr/lib/gcc/x86_64-linux-gnu/4.1/cc1plus
0d80eb1af3474bb5b40c672afbf30678 /usr/lib/gcc/x86_64-linux-gnu/4.1/cc1plus
$ grep cc1plus /var/lib/dpkg/info/g++-4.1.md5sums
60c0d86b806492fe0dcb0749a13a4676 usr/lib/gcc/x86_64-linux-gnu/4.1/cc1plus
```

The solution appears to be forcing a reinstall via:

```
$ sudo apt-get install --reinstall g++-4.1
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 2 not upgraded.
Need to get 0B/2842kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?
(Reading database ... 42496 files and directories currently installed.)
Preparing to replace g++-4.1 4.1.2-16ubuntu2 (using .../g++-4.1_4.1.2-16ubuntu2_amd64.deb) ...
Unpacking replacement g++-4.1 ...
Setting up g++-4.1 (4.1.2-16ubuntu2) ...

$ md5sum /usr/lib/gcc/x86_64-linux-gnu/4.1/cc1plus
60c0d86b806492fe0dcb0749a13a4676 /usr/lib/gcc/x86_64-linux-gnu/4.1/cc1plus
```

Apt-get didn't need to re-download the package, and the .deb file MD5 looks fine, so this isn't a network issue.

I have seen this behavior on several machines, all are Gutsy, x86 32 and 64 bit. This happens on packages that come both from the base OS install and from apt-get later on. Hardware failure is unlikely because of the diversity of hardware that I have (Dell, IBM, laptop, server, destkops, etc.). I have noticed it within a couple hours of installing and later on, probably just from not using that package yet.

I've now started checking out the file MD5 sums on all packages for a system with the following:
```
$ cd /; for i in /var/lib/dpkg/info/*.md5sums; do md5sum -c $i |grep -v 'OK$'; done
```

Sometimes this reports false-positives: In the case of entries for /usr/bin/{col,colcrt,colrm} etc, There are 2 packages that own these files and one has clobbered the other. But in most other cases, it's actually a corrupted file.

A few of the packages on my various systems that I've had to reinstall were:
    g++-4.1
    libc6-dev
    libstdc++6-4.1-dev
    vim-runtime
    valgrind
    findutils

I of course have searched bug reports, forums, google, etc. Does anyone else see these issues? I appreciate any insight folks may have on this.

Thanks,
Tim

---

