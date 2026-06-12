---
title: "How to get kernel-headers?"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by Izuil on 2006-09-18
How do i get the kernel headers for kernel 2.6.17.13 ?

---

### Post by bswilson on 2006-09-18
> **Izuil said:**
> How do i get the kernel headers for kernel 2.6.17.13 ?

Easy!  If you want the headers for your running kernel, use this command:

```
sudo apt-get install linux-headers-`uname -r`
```

Or, if you specifically want the headers for 2.6.17.13, then do (assuming you're on an i386 system):

```
sudo apt-get install linux-headers-2.6.17.13-386
```

---

### Post by Izuil on 2006-09-18
That gives me:

```
rob@rob-linux:~$ sudo apt-get install linux-headers-2.6.17.13-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.17.13-386

```

---

### Post by bswilson on 2006-09-18
> **Izuil said:**
> That gives me:

```
rob@rob-linux:~$ sudo apt-get install linux-headers-2.6.17.13-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.17.13-386

```

Well, I just updated my kernel last Friday, and I'm running 2.6.15-26-386.  I checked at kernel.org, and it appears that 2.6.17.13 just came out on 2006-09-09.  So you can compile it manually, or wait for it to be added to the Ubuntu repositories.  I personally am not as technical as many others here; I couldn't recommend compiling a new kernel because there are a LOT of options, ergo many choices to be made.

---

