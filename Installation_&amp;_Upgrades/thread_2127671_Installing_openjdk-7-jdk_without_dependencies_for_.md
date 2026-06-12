---
title: "Installing openjdk-7-jdk without dependencies for X (like jre-headless)"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by Narigo on 2013-03-20
Hi there,

I want to install javac with the openjdk-7-jdk. The problem is that this installs millions of dependencies, mostly some stuff for X, which I don't need on my command line interface / ubuntu server installation. How can I get rid of these dependencies without loosing the ability to easily update the java installation?

The only pointer I've found is in a comment near the end of this link: [http://www.ubuntuupdates.org/package/core/quantal/main/base/openjdk-7-jdk](http://www.ubuntuupdates.org/package/core/quantal/main/base/openjdk-7-jdk)
> The proper fix is to create a -jdk-headless package, or not depending on these gnome packages at all (e.g. using XDG libraries).

I don't know how to do that and I'm not sure what to do here. Any pointers highly appreciated!

Thanks,
Joern

---

### Post by raztus on 2013-05-28
I'll second this request!  I'm installing openjdk-7-jdk inside a headless VM, so I have no need for these graphical packages.

---

