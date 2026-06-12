---
title: "How To Get Source For 2.6.15-27-386 kernel"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by GaryH on 2006-10-09
Hi All,
I need to write a module for Dapper to drive custom hardware I'm developing. I've installed gcc, make, gdb, and other development tools and I'm able to make and debug rudimentary C programs. My next step is to make a .ko file. To do this I need the source for my version of kernel which is 2.6.15-27-386. For the life of me I can't figure out how to do this. Research I've done so far indicates that apt-get is a good way to get the source and headers. Something like the following:

Quote:
sudo apt-get install kernel-source
sudo apt-get install kernel-headers

Doing the above two things doesn't get me source which is synchronized with my kernel. Does anybody know how to get source for 2.6.15-27-386 or at least enough source so I can build a kernel space driver?

Thanks in advance,
GaryH

---

### Post by angkor on 2006-10-09
To install the headers for the kernel you are currently running try:

```
sudo apt-get install linux-headers-`uname -r`
```

For the source I can only find this, maybe that's what your looking for:

```
 apt-cache search linux-source
linux-source - Linux kernel source with Ubuntu patches
linux-source-2.6.15 - Linux kernel source for version 2.6.15 with Ubuntu patches
```

I think you will only need the headers but I'm not sure.

---

### Post by GaryH on 2006-10-10
Thank you angkor! All I needed were the headers to get my program to build. The module inserts in kernel space just fine too! There are no version synchronization problems at all. Now to finish writing the module and debug it.
Thanks again,
GaryH

---

