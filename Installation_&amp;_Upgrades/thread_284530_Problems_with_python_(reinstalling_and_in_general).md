---
title: "Problems with python (reinstalling and in general)"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by caimex on 2006-10-25
For some odd reason my python broke](*,) 

Half of my python related programs won't start; they can't find their binaries in /usr/bin.

It all started when I tried to install python 2.5, but that was extremely painful because it was missing a bunch of necessary modules to run any programs. I didn't find an easy way to uninstall it (compiled from source), so I did a quick fix by making the python execuatable in /usr/bin ( a link) to point to python 2.4 instead(mistake!).

Now the packages python and python2.4 are messed up. I've looked everywhere for people experiencing the same problem but  found no solution.

Removing and then installing python requires to remove every python depandant program so that would be a pain.

I also stupidly tried to compile 2.4.4 from source which worked but it might have caused problems with the 2.4.2 that the repos have. :neutral: 

When I do sudo apt-get -f install I get the following error(I noticed it has something to do with a postinst file but I have no idea how to fix it)



```

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up python2.4 (2.4.3-0ubuntu6) ...
Compiling python modules in /usr/lib/python2.4 ...
/var/lib/dpkg/info/python2.4.postinst: line 20: /usr/bin/python2.4: No such file or directory
dpkg: error processing python2.4 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python:
 python depends on python2.4 (>= 2.4.2); however:
  Package python2.4 is not configured yet.
dpkg: error processing python (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4
 python
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

:(

Any help appreciated in fixing my completely idiotic mistakes.

---

