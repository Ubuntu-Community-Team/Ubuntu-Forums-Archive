---
title: "Broken python-setuptools..."
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by bodiddlie on 2007-02-27
If I try to apt-get install anything that depends on python-setuptools, it errors out giving me this:

```
Setting up python-setuptools (0.6c3-1ubuntu4) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 861, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 195, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 120, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error processing python-setuptools (--configure):
 subprocess post-installation script returned error exit status 1

```

Any ideas what's going on here?

---

### Post by bodiddlie on 2007-02-28
Anything?  I'm not finding any answers anywhere.

---

### Post by cmay4 on 2007-09-04
I know your message is pretty old, but I am having the exact same problem.  I think its causing some other issues when I try to install packages.  Did you ever find a solution?

Thanks.

---

### Post by WinterWeaver on 2007-09-19
I'm having the same problem...

Tried to install pida when it started...
Now I cannot even uninstall BOA Contructor

---

