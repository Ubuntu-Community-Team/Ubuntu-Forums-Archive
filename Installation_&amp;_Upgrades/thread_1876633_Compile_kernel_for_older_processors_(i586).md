---
title: "Compile kernel for older processors (i586)"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by lifeboy on 2011-11-06
Is it possible to compile an Ubuntu Kernel for sources for an i586 processor after Maverick (10.10)?  I found this note [3] [here]("https://help.ubuntu.com/11.04/installation-guide/i386/hardware-supported.html#ftn.id2768768"), that indicates that it is possible.

Which option(s) in the .config file should one then enable to compile a newer Ubuntu kernel without cmov (and cx8?) support?  Would selection a 486 type processor be all that's needed?

I'm currently running 10.04 on a Vortex processor for thin clients, so if there is a way to use a newer version I'd like to explore it.

---

### Post by MAFoElffen on 2011-11-06
> **lifeboy said:**
> Is it possible to compile an Ubuntu Kernel for sources for an i586 processor after Maverick (10.10)?  I found this note [3] [here]("https://help.ubuntu.com/11.04/installation-guide/i386/hardware-supported.html#ftn.id2768768"), that indicates that it is possible.

Which option(s) in the .config file should one then enable to compile a newer Ubuntu kernel without cmov (and cx8?) support?  Would selection a 486 type processor be all that's needed?

I'm currently running 10.04 on a Vortex processor for thin clients, so if there is a way to use a newer version I'd like to explore it.
That is for the Ubuntu built and patched kernels... I'm wondering if that is aN Ubuntu thng or a Linux Kernel thing?  I don't know.  Because when I test kernels and/or have kernel bugs, launchpad has me test it against the mainline PPA, which is from the Upstream source code, without any Ubuntu thrown in yet.  Having said that- Is your "condition" true for the generic mainline kernels without the Ubuntu added patches and extras?  Have you tried one?

Here you go.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Download the "x86" image and header file, with a matching "-all" header file. Put them into their own directory, go to that directory from a terminal and 
```

sudo dpkg -i *.deb

```

---

### Post by lifeboy on 2011-11-08
I don't have the time at the moment to investigate this, but I will in future.  In a sense this is a scouting question of sorts, to see what I can learn from the experience of others.  Thanks for your comments.

---

