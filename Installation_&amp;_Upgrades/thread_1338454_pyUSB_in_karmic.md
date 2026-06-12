---
title: "pyUSB in karmic"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by lazerradial2003 on 2009-11-26
I'm currently trying to install pyusb in Ubuntu Karmic. I've tried installing from the repositories and manually by downloading the tarball from SourceForge and running sudo setup.py install which gives the following output:

running install
running build
running build_ext
running install_lib
running install_egg_info
Writing /usr/local/lib/python2.6/dist-packages/pyusb-0.4.2-py2.6.egg-info

When I try and import usb.core which is one of the modules with the package I get the message "ImportError: No module named core" however "import usb" works fine. 

Anyone got any ideas how to troubleshoot this?

---

### Post by solar george on 2009-11-26
how are you importing it, have you tried
```
from usb import core
```

---

### Post by lazerradial2003 on 2009-11-26
Thanks for the reply, turned out the problem was that I was using commands for the 1.0 branch of pyusb but had downloaded the 0.4.x branch (which is the version made available on sourcefoge). 1.0 can be downloaded from the SVN (svn co [https://pyusb.svn.sourceforge.net/svnroot/pyusb](https://pyusb.svn.sourceforge.net/svnroot/pyusb) pyusb 
)

---

### Post by hubearth on 2012-09-05
I'm using Ubuntu 10.04 (Lucid) and I had to install pyusb version 1.0 to make it work. The problem is that Lucid only includes version 0.4 in its repository, so I had to install add a new source. Check out this site:
[https://launchpad.net/~gekkio/+archive/pyusb](https://launchpad.net/~gekkio/+archive/pyusb)

---

### Post by overdrank on 2012-09-05
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

