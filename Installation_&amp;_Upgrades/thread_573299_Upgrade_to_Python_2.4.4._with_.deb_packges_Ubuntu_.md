---
title: "Upgrade to Python 2.4.4. with *.deb packges Ubuntu 6.06.1 LTS?"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by aidtwo on 2007-10-11
Hello.  What issues are there using debian packages from debian.org for etch to upgrade to Python version 2.4.4 on a Ubuntu 6.06.1 LTS system? An up-to-date (using "sudo apt-get update" and "sudo apt-get upgrade") Ubuntu 6.06.1 system only provides Python 2.4.3 (not the latest bug fix version of Python).

Python 2.4.4 is a requirement for Mailman" [http://www.list.org/index.html](http://www.list.org/index.html) on this system.  I cannot use the Mailman version available via apt-get for this system as it is an older release with a number of known security issues.

So, in attempt to upgrade Python to version 2.4.4, I forced the installation of packages downloaded from the following sites with "sudo dpkg -i --force-all *" (the command was executed in a directory that only contained the i386 package files from the following URLs):

[http://packages.debian.org/etch/python/python](http://packages.debian.org/etch/python/python)
[http://packages.debian.org/etch/python/python-minimal](http://packages.debian.org/etch/python/python-minimal)
[http://packages.debian.org/etch/python/python2.4](http://packages.debian.org/etch/python/python2.4)
[http://packages.debian.org/etch/python/python2.4-minimal](http://packages.debian.org/etch/python/python2.4-minimal)


This is the output from doing this:
```
(Reading database ... 33038 files and directories currently installed.)
Preparing to replace python2.4 2.4.4-3 (using python2.4_2.4.4-3_i386.deb) ...
Unpacking replacement python2.4 ...
Preparing to replace python 2.4.4-2 (using python_2.4.4-2_all.deb) ...
Unpacking replacement python ...
Preparing to replace python2.4-minimal 2.4.4-3 (using python2.4-minimal_2.4.4-3_i386.deb) ...
Unpacking replacement python2.4-minimal ...
Preparing to replace python-minimal 2.4.4-2 (using python-minimal_2.4.4-2_all.deb) ...
Unpacking replacement python-minimal ...
dpkg: python2.4-minimal: dependency problems, but configuring anyway as you request:
 python2.4-minimal depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.5.
Setting up python2.4-minimal (2.4.4-3) ...
Linking and byte-compiling packages for runtime python2.4...

dpkg: python-minimal: dependency problems, but configuring anyway as you request:
 python-minimal depends on dpkg (>= 1.13.20); however:
  Version of dpkg on system is 1.13.11ubuntu7.
Setting up python-minimal (2.4.4-2) ...
dpkg: python2.4: dependency problems, but configuring anyway as you request:
 python2.4 depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.5.
 python2.4 depends on libdb4.4; however:
  Package libdb4.4 is not installed.
 python2.4 depends on libreadline5 (>= 5.2); however:
  Version of libreadline5 on system is 5.1-7build1.
 python2.4 depends on libssl0.9.8 (>= 0.9.8c-1); however:
  Version of libssl0.9.8 on system is 0.9.8a-7ubuntu0.4.
Setting up python2.4 (2.4.4-3) ...

Setting up python (2.4.4-2) ...

```

I am concerned this is not the best way of doing this.  What is the best way to upgrade Python?

Thoughts and instructions about this would be greatly appreciated.  Thank you.

---

