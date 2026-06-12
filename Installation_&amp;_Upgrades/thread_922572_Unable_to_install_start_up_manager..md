---
title: "Unable to install start up manager."
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by float379 on 2008-09-17
Hey!! For some reason my start up manager does not install. I end up with the following error message when i try to install it,using the synaptic package manager:


```
E: /var/cache/apt/archives/startupmanager_1.9.11-1~hardy1_all.deb: subprocess pre-installation script returned error exit status 1

```

Could some one please tell me how to fix this? And is it possible to change the usplash using the cli? I currently use ubuntu 8.04 and am relatively new to linux.

Thanks in advance

---

### Post by Partyboi2 on 2008-09-17
Hi, can you post the whole output to```
 sudo apt-get install startupmanager
``` from a terminal (Applications>Accessories>Terminal) If you are wanting to change the splash you could try [[COLOR=Blue]this[/COLOR]]("http://www.zimbio.com/Ubuntu+Linux/articles/354/Changing+Boot+Up+Splash+Ubuntu")

---

### Post by float379 on 2008-09-18
Sure, here is the entire output to sudo apt-get install startupmanager

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  startupmanager
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/90.4kB of archives.
After this operation, 1040kB of additional disk space will be used.
(Reading database ... 121148 files and directories currently installed.)
Unpacking startupmanager (from .../startupmanager_1.9.11-1~hardy1_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1891, in <module>
    main()
  File "/usr/bin/pycentral", line 1885, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1349, in run
    pkg.prepare(used_runtimes, old_used_runtimes, old_pkg)
  File "/usr/bin/pycentral", line 998, in prepare
    os.makedirs(d2)
  File "/usr/lib/python2.5/os.py", line 171, in makedirs
    mkdir(name, mode)
OSError: [Errno 2] No such file or directory: '/usr/lib/python2.5/site-packages/bootconfig'
dpkg: error processing /var/cache/apt/archives/startupmanager_1.9.11-1~hardy1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/startupmanager_1.9.11-1~hardy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by float379 on 2008-09-18
By the way, the linked did help a fair bit, thanks! But i guess it would still be more convenient to have the start up manager up and running :p

---

### Post by Partyboi2 on 2008-09-18
I am not sure what has happened, maybe you should considering opening a [[COLOR=Blue]bugreport[/COLOR]]("https://bugs.launchpad.net/ubuntu/+filebug") up.

---

### Post by float379 on 2008-09-20
Hmmm.. guess i'll think about that, i'm quite content using the command line though. Thanks!

---

