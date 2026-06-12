---
title: "Missing newline in deb package?"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by Falados on 2005-07-15
Hello, I just joined the forums and I'm a former Gentoo ricer.  I'm trying to get Ubuntu to work and already something has screwed up.  This is a clean install (nothing touched, this is how it ended up)  and it complains about a 'missing newline' in the debian file's package list.  Why is this problem appearing?  What reason is this even present? This is a clean install, I couldn't screw anything up that wasn't screwed up prior to my using it.

Edit: This is the message I receive (with pretty much all packages)
```
 
E: /var/cache/apt/archives/<pkgname>_<arch>.deb: files list file for package 'python-htmlgen' is missing final newline

``` 

Just replace pkgname with the package name and the arch with i386 and thats pretty much what happens to anything I try to update.

I fixed the problem by doing 'locate python-htmlgen' and then making my own list file in /var/lib/dpkg/info/ but I want to know how that file could have gotten corrupted before I even got to touch the system?

---

### Post by gabriel.ferreira on 2005-07-15
I have a problem like yours...
I have tried to install Ubuntu, but i get a problem after the 'base system installation'
I have the shiped CD from a friend, and it seems ok (not scratched). So i tried to follow all the steps of the installation (i even let the installer auto-partitioner do the work) but after booting the system for the first time, a message like this appears many times, for every step of the configuration..

<step of configuration> (...) libdl.so.2: no version information avaiable (...) required by /bin/bash

I don't know what to do. ](*,)

----> Strange solution:
my problem was due to a bad jumper configuration at the HD (for the system it looked like a MASTER, but it was set to CABLE SELECT). Once i fixed the jumpers so that the HD was actually MASTER, the problem was gone.

---

