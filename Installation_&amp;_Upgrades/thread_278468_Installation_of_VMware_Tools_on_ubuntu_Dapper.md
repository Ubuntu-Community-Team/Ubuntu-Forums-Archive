---
title: "Installation of VMware Tools on ubuntu Dapper"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by kobutak on 2006-10-16
How do I find the location of the header files for the C compiler that are compatible with my running Kernel?  VMWare installation cannot continue if I cannot provide the location correctly.  /usr/src/linux/include is empty but /usr/include has an older version.

Running kernel is version 2.6.15-27-386

Anyone done this before? Suggestions are welcome.

Thanks!

---

### Post by kuja on 2006-10-16
First, install the kernel headers. That should be something like linux-headers-yourarchitecture (dapper) or linux-headers-generic (edgy). 

Then, the directory you want to use is /usr/src/linux-headers-`uname -r`/

---

### Post by kobutak on 2006-10-19
Kuja,

Thanks a lot, it worked just fine.

---

### Post by Gre0Gor on 2006-10-20
Ive got the same problems. I know where headers are located but nothing happen :)

The path "/usr/src/linux-headers-2.6.15-23" is an existing directory, but it
does not contain a "linux" subdirectory as expected.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

where is the problem ?

---

### Post by jeroen6bis on 2006-10-23
> **Gre0Gor said:**
> The path "/usr/src/linux-headers-2.6.15-23" is an existing directory, but it
does not contain a "linux" subdirectory as expected.

You forget the subdir /include

---

