---
title: "Hellanzb not working on feisty"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by VuDu on 2007-01-22
Did anyone manage to get hellanzb (0.10-1) to work on feisty fawn herd 2?
I tried to dist-upgrade but had no success when running hellanzb. Then I clean installed from the iso, because there might be some problem with the update... but still it doesn't work.

the install from from the universe rep works but when I try to run it I get this

```
vudu@vudumachine:~$ hellanzb 
Traceback (most recent call last):
  File "/usr/bin/hellanzb", line 14, in <module>
    from Hellanzb.Core import main
  File "/var/lib/python-support/python2.5/Hellanzb/Core.py", line 12, in <module>
    import optparse, os, signal, sys, time, thread, threading, Hellanzb, Hellanzb.PostProcessor
  File "/var/lib/python-support/python2.5/Hellanzb/PostProcessor.py", line 15, in <module>
    from Hellanzb.PostProcessorUtil import *
  File "/var/lib/python-support/python2.5/Hellanzb/PostProcessorUtil.py", line 13, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize
```

I tried to compile the sources and I get this:

```

vudu@vudumachine:~/hellanzb-0.11-trunk$ python setup.py install
/usr/lib/python2.5/distutils/dist.py:263: UserWarning: Unknown distribution option: 'app'
  warnings.warn(msg)
running install
error: invalid Python installation: unable to open /usr/include/python2.5/pyconfig.h (No such file or directory)

```

So it seems that there's some problem with python, no?
Everything worked ok on Edgy.

Thanks in advance :)

---

### Post by VuDu on 2007-01-25
Help, anyone?

---

### Post by XtremeBain on 2007-01-28
Was having the same trouble trying to compile a Listen snapshot.  It turns out that the python dev packages weren't installed.

```
sudo apt-get install python2.5-dev
```

Things are back to normal :)

---

### Post by VuDu on 2007-02-12
Yes, I didn't seem to have that package installed but bow that I do the problems persists! Damn!
I've tried python-2.5-dbg and it's the same...
I've apt-get'ed the hellanzb from the ubuntu repositories, should it deal with all the dependencies?

---

### Post by VuDu on 2007-02-15
For what I saw on the Hellanzb changelog:

> 
v0.11:

o Fixed the error:
  ImportError: cannot import name daemonize
  with Twisted 2.5


It's a known bug. I've installed v0.11 from source and it's working again! ;)
Hope the add it to the reps asap! :)

---

### Post by AlterEgo on 2007-03-12
Version 0.12 is out. Works fine installed manually too.

---

### Post by VuDu on 2007-05-02
Yes, everything is working ok now... but why is still version 0.10 the last version on the repositories?? Even debian has the 0.13!

[http://packages.ubuntu.com/feisty/net/hellanzb](http://packages.ubuntu.com/feisty/net/hellanzb)
VS
[http://packages.debian.org/testing/net/hellanzb](http://packages.debian.org/testing/net/hellanzb)

---

### Post by VuDu on 2007-05-07
What can one do to update the version on the repositories? Launch a bug report? :S

---

### Post by rai4shu2 on 2007-05-07
No need:

[https://bugs.launchpad.net/ubuntu/+source/hellanzb/+bug/112662](https://bugs.launchpad.net/ubuntu/+source/hellanzb/+bug/112662)

---

### Post by VuDu on 2007-05-07
Thanks ;)
2 days ago and still no replies though :(

---

