---
title: "Terminal problems with reinstall"
date: 2022-04-14
forum: Installation &amp; Upgrades
---

### Post by robertcull1 on 2022-04-14
I was having problems with my old installation of 18.04 and I wanted to reinstall. My installation was all on one partition. I used the instructions here to make:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

to make a separate /home partition.

Then I installed 18.04 on the root partition.

Now I have a number of problems.

When I first start up a terminal, I get:

```
-bash: /usr/local/bin/virtualenvwrapper.sh: No such file or directory
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
```

I still get a prompt, which seems to work alright. But every time I use a command, I usually get a:

```
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
```

error.

---

### Post by ActionParsnip on 2022-04-14
Does the system boot OK despite the error?

---

### Post by ActionParsnip on 2022-04-14
Possible fix here
[https://stackoverflow.com/questions/53825857/error-ld-so-object-libgtk3-nocsd-so-0-from-ld-preload-cannot-be-preloaded](https://stackoverflow.com/questions/53825857/error-ld-so-object-libgtk3-nocsd-so-0-from-ld-preload-cannot-be-preloaded)

---

### Post by robertcull1 on 2022-04-15
It boots fine.

Now it says:

```
/usr/bin/python3: Error while finding module specification for 'virtualenvwrapper.hook_loader' (ModuleNotFoundError: No module named 'virtualenvwrapper')
virtualenvwrapper.sh: There was a problem running the initialization hooks. 


If Python could not import the module virtualenvwrapper.hook_loader,
check that virtualenvwrapper has been installed for
VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3 and that PATH is
set properly.
```

---

### Post by TheFu on 2022-04-15
Looks like a python2 vs python3 dependency issue.  Python2 was deprecated and removed in 2020.  18.04 should ship with python2 still and all system tools should expect that version.

If someone decided to upgrade the python2 that the system requires to python3, bad things will happen.   Bad things that prevent booting and most other system things.  It is possible to have both python2 and python3 on the system. It is best to force all python3 uses into a virtual python environment and to take steps to ensure whoever does administration of the system doesn't have any python3 that could be confused with python2.  

I had a similar issue with perl when I moved from 16.04 to 18.04.  I have 5+ different perl environments controlled by the perlbrew tool (perl's virtual environment tool) and forgot to revert to the system perl before do-release-upgrade.  The result was really, really, ugly.

If nobody did any python3 stuff, then I can only guess that the installer was updated in some way to break python2.

None of my 18.04 servers is having any python related issues, BTW.  But I haven't attempted an 18.04 install in a few years.  At this point, I'd only be installing 20.04 which has moved to python3 for everything (breaking a number of python2 programs). But to be fair, the world was told that python2 was deprecated for a long time. We were warned.

---

