---
title: "Upgrading Kernel - Need Help!"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by J2897 on 2008-08-02
I installed Ubuntu 8.04 (kernal version is 2.6.24).

I installed Ubuntu by Mounting the Ubuntu .ISO image from within Windows.

A driver requires my kernal version to be 2.6.25.

How do I get my kernel to be version 2.6.25 or higher on this kind of installation?

I seem to be going round in circles reading one tutorial after another, but without getting anywhere.

Thanks in advance.

---

### Post by redraiderbum on 2008-08-02
What do you mean you mounted the iso from within windows and installed?  Did you not burn a disk for install?

To upgrade the kernel once ubuntu is installed you would just run a software update and restart.  I think I'm not understanding the situation.

---

### Post by J2897 on 2008-08-02
I have installed all the automatic updates and my kernel is at kernal version 2.6.24.
```
uname -r
```
[This]("http://uk.youtube.com/watch?v=MajFZigoiXA") is how I installed Ubuntu.

---

### Post by redraiderbum on 2008-08-02
That's cool.  Unfortunately, I did a quick check and my fully updated box is also 2.6.24.  It looks like the ubuntu 8.10 alpha starts with kernel 2.6.26 r2 right now.  You could try that.

You could also custom compile the 2.6.25 kernel.  Here is a possible tutorial:

[http://blog.gunbladeiv.com/2008/05/ubuntu-kernel-2625-on-hardy.html](http://blog.gunbladeiv.com/2008/05/ubuntu-kernel-2625-on-hardy.html)

---

### Post by zvacet on 2008-08-03
[Here]("http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html")

---

