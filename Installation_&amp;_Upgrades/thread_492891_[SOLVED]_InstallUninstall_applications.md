---
title: "[SOLVED] Install/Uninstall applications"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by epais on 2007-07-05
Two days ago, I install the aplication "weather-util" to see what was this (I am a new Ubuntu user). And after that I try to remove it.

The message appears as follow:

------------------------------------------------------------------------------------------------------
[I][I]emanuel@emanuel-ubuntu:~$ sudo apt-get remove weather-util
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  weather-util
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/14.2kB of archives.
After unpacking 123kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 119519 files and directories currently installed.)
Removing weather-util ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in ?
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 953, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 198, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 130, in default_version
    raise ValueError, "the symlink /usr/bin/python does not point to the python default version. It must be reset to point to %s" % debian_default
ValueError: the symlink /usr/bin/python does not point to the python default version. It must be reset to point to python2.5
dpkg: error processing weather-util (--remove):
 subprocess pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in ?
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 875, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 198, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 130, in default_version
    raise ValueError, "the symlink /usr/bin/python does not point to the python default version. It must be reset to point to %s" % debian_default
ValueError: the symlink /usr/bin/python does not point to the python default version. It must be reset to point to python2.5
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 weather-util
E: Sub-process /usr/bin/dpkg returned an error code (1)
---------------------------------------------------------------------------------------------------------------

From this time, after this error, I was unable to install or uninstall anything, even the upgrades.
The error is always the same. 

Can anybody helps me?

Thanks

---

### Post by bigken on 2007-07-05
try this in a terminal sudo dpkg --configure -a

---

### Post by epais on 2007-07-05
thanks BigTen, but the same error appears after doing the command you said:
emanuel@emanuel-ubuntu:~$ sudo dpkg --configure -a
Password:
emanuel@emanuel-ubuntu:~$ sudo apt-get remove weather-util
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  weather-util
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/14.2kB of archives.
After unpacking 123kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 119519 files and directories currently installed.)
Removing weather-util ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in ?
    main()
....................................
........................

---

### Post by bigken on 2007-07-05
go to synaptics and look for broken packages if you find any remove them

---

### Post by epais on 2007-07-05
No broken packages... sorry

---

### Post by epais on 2007-07-05
I think, I have some problem in "gdebi-core" or anything similar to this.

---

### Post by bigken on 2007-07-05
have you tried sudo apt-get update sudo apt-get upgrade

---

### Post by epais on 2007-07-05
It's very strange, I believe. the answer is the same, look:

emanuel@emanuel-ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/14.2kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 119520 files and directories currently installed.)
Preparing to replace gdebi-core 0.2.4ubuntu1 (using .../gdebi-core_0.2.4ubuntu1_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in ?
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
..........................................................
....................................................

---

### Post by epais on 2007-07-06
It's solved with a help from Cesare Tirabassi :

"sudo ln -sf /usr/bin/python2.5 /usr/bin/python"

---

### Post by bigken on 2007-07-06
pleased you got it sorted :D

---

