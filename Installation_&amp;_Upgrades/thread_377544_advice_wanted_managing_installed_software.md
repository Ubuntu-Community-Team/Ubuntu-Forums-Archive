---
title: "advice wanted: managing installed software"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by tanguyr on 2007-03-06
Hello,

I am quite new to both Linux in general and Ubuntu in particular, and i would like to ask the readers of this forum for any tips and tricks they might have come up with to help me manage my machine's configuration.

My problem:

On my machine, i have installed software from various sources:

- packages installed the "normal" way with the package manager
- software installed from source or binaries *not* available in the repositories (subversion 1.4, Rails 1.2, Oracle 10g, etc.)
- software installed from "within" other software (Ruby gems, Eclipse plug-ins, etc) - note that some of this software, like Eclipse, *is* installed from apt-get, but contains extra code not installed from apt-get...

My question is what's the best way to manage this? I've already borked my eclipse setup somehow and had to reinstall eclipse + all plugins from scratch... and i can't install software like trac from the repositories, because it has a dependency on subversion... but the version in the repository is older than the version i am running. Everything seems to pile up willy-nilly in /usr/bin and other "common" locations, and i can already see that this just isn't going to scale. Some people i was talking to about this told me that the way to go was to make your own debs for all software you want to install and then manage it from apt-get/Adept, but that sounds a bit daunting...

This is my first Linux install and i count on it getting borked once in a while (i.e. this is a "training wheels" install, not my final configuration, and i will reinstall from scratch sooner rather than later). If you have worked out any kind of system for managing these different kinds of software side by side (by side), i would *love* to hear your thoughts.

Thanks for your time,
/t

---

### Post by tommcd on 2007-03-06
One thing you can do (if you haven't already) is to use checkinstall instead of <make install> when compiling programs from source. Checkinstall (available from synaptic) will account for dependencies and create the program as a .deb file which will then show up in synaptic and be much easier to uninstall or reinstall than just using <make install> does.
Compiling from source or using third party repos is always a risk. On the other hand, it is a good way to learn stuff also, just proceed with caution unless you don't mind breaking and reinstalling ubuntu.
So with checkinstall it is:
./configure
make
sudo checkinstall

---

### Post by tanguyr on 2007-03-07
> **tommcd said:**
> One thing you can do (if you haven't already) is to use checkinstall instead of <make install> when compiling programs from source. Checkinstall (available from synaptic) will account for dependencies and create the program as a .deb file which will then show up in synaptic and be much easier to uninstall or reinstall than just using <make install> does.

Hello Tommcd,

Thanks for the info - no, i was not aware of this checkinstall program. I will install it and take it for a spin. 

Regs,
/t

---

