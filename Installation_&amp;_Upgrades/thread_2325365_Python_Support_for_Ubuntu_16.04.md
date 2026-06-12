---
title: "Python Support for Ubuntu 16.04"
date: 2016-05-21
forum: Installation &amp; Upgrades
---

### Post by Downshift_Artist on 2016-05-21
Hello all. I'm having an issue with 16.04 and installing the needed python dependencies for the Folding@Home client.  I understand that 16.04 comes pre-loaded with python-3, but it's not backward compatible.  Should I just uninstall 16.04 and go back to 15.10 where I didn't have this issue or is there a fix for this?  Thanks.

---

### Post by him610 on 2016-05-21
FWIW, just checked my python version... (it came with the default installation)
```
$ python -V
Python 2.7.11+ 
```
```
$ uname -a
Linux SN68S 4.4.0-22-generic #39-Ubuntu SMP Thu May 5 16:52:40 UTC 2016 i686 athlon i686 GNU/Linux
```

---

### Post by Downshift_Artist on 2016-05-21
Hmm, so it seems I just need to somehow be able to install python-support, but for whatever reason I simply can't

```
$ sudo apt-get install python-supportReading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-support is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'python-support' has no installation candidate



```

---

### Post by him610 on 2016-05-21
There is no package, *python-support*.

What makes you think you don't already have support for python?

Did you follow the Linux install guide for folding@home? 
[https://folding.stanford.edu/home/guide/linux-install-guide/]("https://folding.stanford.edu/home/guide/linux-install-guide/")

---

### Post by Impavidus on 2016-05-22
Ubuntu 16.04 comes with both python 2 and python 3 out of the box. Python 2 is the default.```
$ python3 --version
Python 3.5.1+

$ python2 --version
Python 2.7.11+

$ python --version
Python 2.7.11+
```

Don't go back to Ubuntu 15.10. It will reach end-of-life in 2 months.

---

