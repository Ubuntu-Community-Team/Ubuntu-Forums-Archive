---
title: "Build distro from installed system"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by kostus1974 on 2006-06-21
I have Ubuntu 6.06 LTS installed (well, first, I has 5.10 installed from CD, and then upgrade to 6.06 LTS from internet).

The Question:

 Can I build distro (set of directories or even bootable iso-image) from my installed system?

 In other words, I want to run some program, which search my installation and build a distribution with packages that installed on it (optionally with my configurations bu default, but it's not important).

Is it possible?

--
Konstantin N. Terskikh,
[http://www.toxsoft.ru/](http://www.toxsoft.ru/)

---

### Post by Jussi Kukkonen on 2006-06-21
[QUOTE=kostus1974]
 Can I build distro (set of directories or even bootable iso-image) from my installed system?
[/QUOTE]

I don't think there's an easy way to do that. 

What you can do is create a metapackage that lists all the packages you want installed an your machines, and install that metapackage after installing plain Ubuntu on a machine -- that's just one additional step in the install procedure and you can do it from a repo or a CD (if you've burned the debs on a CD of course).

See [http://ubuntuforums.org/showthread.php?p=1104071](http://ubuntuforums.org/showthread.php?p=1104071).

---

### Post by kostus1974 on 2006-06-21
Ok, rearrange the question.

 Can I re-build (restore) already installed package?

For example: I has some .deb, install it and then remove that .deb.
Can I restore .deb from installed components and configuration parts in installation database?

--
Konstantin N. Terskikh
[http://www.toxsoft.ru/](http://www.toxsoft.ru/)

---

