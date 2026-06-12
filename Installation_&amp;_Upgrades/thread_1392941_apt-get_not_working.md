---
title: "apt-get not working"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by ItsAaron on 2010-01-28
Hi.

Just as a starter, I am completely new to Ubuntu. I have always used windows and the most technical thing I know so far is Alt+F2 :P

Whenever I try to download an application with 'apt-get' I always get an error. For example, trying to get pidgin:

reading package lists ...done
building dependency tree
reading state information...done
Package pidgin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
libpurple-bin libpurple0
E: Package pidgin has no installation candidate

But I've also tried other ones which have worked perfectly with my friend such as 'sudo apt-get install build-essential'. It worked fine for him but I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

He suggested that maybe my laptop runs 32 bits and I'm using 64 bits Ubuntu, but I dont even know how I could check that or if it would do anything like this :S

Any help is appreciated. Thankyou in advance.

---

### Post by tachuela on 2010-01-28
Make sure your repositories are working ( Open )
Administration>Software Sources

---

### Post by Leppie on 2010-01-28
you can generate the sources.list here: [http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

---

### Post by firedragoneater on 2010-03-09
I had the same problem as you and I managed to fix it with the tips and advice above. Also it shouldn't matter about 32-bit and 64-bit in this case.

---

