---
title: "Synaptic-0.61"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by Commodore13 on 2008-02-06
What Am I doing wrong/What should I do to successfully install Synaptic
commodore13@Commodore13-laptop:~/Desktop/synaptic-0.61$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
commodore13@Commodore13-laptop:~/Desktop/synaptic-0.61$

---

### Post by taurus on 2008-02-06
You need the build-essential package if you want to build something from source.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Commodore13 on 2008-02-06
But I dont wanna build it from source.
May i have a link to a prebuilt?

---

### Post by taurus on 2008-02-06
> **Commodore13 said:**
> But I dont wanna build it from source.
May i have a link to a prebuilt?

Excuse me but if you don't want to build it from source, then why in the world did you run that command from a terminal, ./configure?

I assume you want synaptic as in the touchpad driver for X server?

```
sudo apt-get update
sudo apt-get install xserver-xorg-input-synaptics
```

But if you mean synaptic as in package manager, then it should already be on your system; otherwise, install it with

```
sudo apt-get update
sudo apt-get install synaptic
```

---

### Post by Commodore13 on 2008-02-06
Thank you, sorry for the confusion, I'm a n00b at linux, and was only following online intructions when I typed that command

---

### Post by bwtranch on 2008-02-06
Maybe you should play around with it. Download a tarball and see if you can make it work.

---

