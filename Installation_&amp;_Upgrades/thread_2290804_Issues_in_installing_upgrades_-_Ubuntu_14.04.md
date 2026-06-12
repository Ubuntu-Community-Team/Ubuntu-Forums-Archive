---
title: "Issues in installing upgrades - Ubuntu 14.04"
date: 2015-08-15
forum: Installation &amp; Upgrades
---

### Post by GarlicxSauce on 2015-08-15
Hey everyone,

I've recently re-installe Ubuntu 14.04 LTS cause i could not solve a booting problem i got cause of a new kernel i've installed and that apparently was in conflict with part of my hardware. Everything works smoothly besides the fact that since the very first start i can't install any Ubuntu update, i can install single software updates, but not the package and software updates of Ubuntu that are suggested. When i try to do so, the answer is Package installation failed, check your internet connection.

As a matter of fact thought, my internet connection works just fine and i have no problems with that whatsoever. Any idea what i could do?

Many thanks in advance!

---

### Post by Bashing-om on 2015-08-15
GarlicxSauce; Yeah ;

I do have a thought. In respect to downloading from the respective software repositories. In which repository is the desired package(s) located and do you have the access to this repository enabled ( Ubuntu Software Center -> sources ) ?
```

apt-cache show <package_name>

```
Will reveal the availability of a particular package and where it is located .

[INDENT][INDENT]wonderful little process
[/INDENT][/INDENT]

---

