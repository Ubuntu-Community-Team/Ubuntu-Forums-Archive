---
title: "libglib2.0-dev ask for a package which version is older than I have installed"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by manou on 2007-03-21
Hello,

I need to install the package: libstreamer0.10-dev

It depends on libglib2.0-dev

Then, I try to install it but I can't because it depends on libglib2.0-0 (2.10.**2-1ubuntu3**), but in the system is installed (2.10.**3-0ubuntu1**)

If I try to remove libglib2.0-0 (2.10.3-0ubuntu1)  to install libglib2.0-dev and it can solve the dependencies by itself apt-get want to remove almost all the system. I almost do, but I think it should be other solution.

If I download libglib2.0-dev and install it with dpkg -i then I have a broken package message in synaptic.

It is very strange and maybe it is a problem from the package Ubuntu's source...

Also, how can i arrive to this situation? What I have done wrong?
I don't remember to change the sources.list ... very strange

I am using Xubuntu dapper and my repositories is like this:
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

Can somebody help me with this please ?

Thank you.

---

