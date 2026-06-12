---
title: "Nvidia driver installation difficulties"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by penguin957 on 2007-03-05
I have been trying to install nvidia drivers for my nvidia 5500 OC but I have been getting the message
Error:  You do not appear to have the libc header files installed on you system.   Please install you distribution's libc development package.

If anyone can help me figure out what's going on I would greatly appreciate it!!

---

### Post by nyinge on 2007-03-05
You may be needing an essential-build meta package.
```
 sudo apt-get install essential-build 
```

See if that works.

---

### Post by penguin957 on 2007-03-05
When I do that I get...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package essential-build

---

### Post by ffxr on 2007-03-05
build-essential

i think it is.... look for it in synaptic if it might be a typo

---

### Post by ffxr on 2007-03-05
you might need some or all of these packages as well..

```
 sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev 
```

---

### Post by penguin957 on 2007-03-05
Thanks so much for the help!!! I am eternally in your debt.  Now if I only had the non-existant drivers to my external sound card haha.  Thank you!!

---

