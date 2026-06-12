---
title: "Custom Kernel"
date: 2004-12-23
forum: Installation &amp; Upgrades
---

### Post by log on 2004-12-23
Hello, I have been trying to get a custom kernel working so that I can install a module for my network card. Its a bit difficult since I dont have network access on the laptop :)

Anyway, I put the kernel on, compiled it as 

[http://www.ubuntulinux.org/wiki/KernelByHandHowto/view?searchterm=kernel%20source](http://www.ubuntulinux.org/wiki/KernelByHandHowto/view?searchterm=kernel%20source)

said but the kernel comes up with the error:
VFS: Cannot open root device "hda1" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)


This is what I have done to try to solve the problem:
- Compile reiserfs in the kernel (not as a module since its my / fs)
- root=/dev/hda1 is DEFINATLY a kernel option.

Ive been playing with this for a while and cant work it out. Ubuntu looks like a good distro but I really need net access to turn it into what I want...

---

### Post by diebels on 2004-12-28
Which network card?

---

