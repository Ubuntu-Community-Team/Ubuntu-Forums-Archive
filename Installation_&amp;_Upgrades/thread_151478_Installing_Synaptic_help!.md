---
title: "Installing Synaptic help!"
date: 2006-03-28
forum: Installation &amp; Upgrades
---

### Post by fake_punk on 2006-03-28
Hey all, I am a newbie to Linux and I am trying to install Synaptic, but I am getting the following problem:

rees@ubuntu:~$ sudo dpkg -i /home/rees/synaptic_0.57.8_i386.deb
Selecting previously deselected package synaptic.
(Reading database ... 57500 files and directories currently installed.)
Unpacking synaptic (from .../rees/synaptic_0.57.8_i386.deb) ...
dpkg: dependency problems prevent configuration of synaptic:
 synaptic depends on libapt-pkg-libc6.3-6-3.11; however:
  Package libapt-pkg-libc6.3-6-3.11 is not installed.
 synaptic depends on libcairo2 (>= 1.0.2-2); however:
  Version of libcairo2 on system is 1.0.2-0ubuntu1.1.
 synaptic depends on libgcc1 (>= 1:4.0.2); however:
  Version of libgcc1 on system is 1:4.0.1-4ubuntu9.
 synaptic depends on libglib2.0-0 (>= 2.8.5); however:
  Version of libglib2.0-0 on system is 2.8.3-0ubuntu1.
 synaptic depends on libpango1.0-0 (>= 1.10.3); however:
  Version of libpango1.0-0 on system is 1.10.1-0ubuntu1.
 synaptic depends on libstdc++6 (>= 4.0.2-4); however:
  Version of libstdc++6 on system is 4.0.1-4ubuntu9.
 synaptic depends on libxml2 (>= 2.6.23); however:
  Version of libxml2 on system is 2.6.21-0ubuntu1.
 synaptic depends on libxrender1 (>= 1:0.9.0.2); however:
  Version of libxrender1 on system is 1:0.9.0-1.
dpkg: error processing synaptic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 synaptic

What should I do to update all these things?  Sorry if this is in the wrong forum.:KS

---

### Post by frodon on 2006-03-28
Hey, synaptic is already installed (it is by default after a fresh install), the KDE equivalent is adept.
Read this link to know how synaptic works : [https://wiki.ubuntu.com/SynapticHowto?](https://wiki.ubuntu.com/SynapticHowto?)

If you use KDE, open adept and search for synaptic and choose to install it, that's all ;)

---

