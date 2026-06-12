---
title: "Installing gcc 4.2.0 on Hardy"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by tgrimley on 2008-08-04
I need to use 4.2.0 for compiling some mex functions within Matlab so that I don't end up with some nasty seg faults. I'm not an expert c programmer or anything so I am not really sure what needs to be done to install gcc 4.2.0.  I am currently in the middle of a ./configure, make, make install, but I'm not sure if this is the right approach.

Ideally I'd like to just install some debs or something... but if anyone could point me somewhere that will give me instructions on installing gcc if it needs flags or anything...

Any help would be appreciated.

---

### Post by KatBuntu on 2008-08-04
By default ubuntu comes with a gcc preinstalled, i don't know if it's the version you want, try this on a terminal:
```
$gcc <source.c>
```
If you receive a error of command not found, try this:
```
#apt-get install gcc build-essential
```
Don't complicate things, use google and apt-get.

---

