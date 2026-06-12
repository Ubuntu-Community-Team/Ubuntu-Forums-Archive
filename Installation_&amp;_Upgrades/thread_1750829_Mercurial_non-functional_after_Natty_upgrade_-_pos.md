---
title: "Mercurial non-functional after Natty upgrade - possible Python library issue"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by brettski74 on 2011-05-05
I upgraded from Maverick to Natty a few days ago. Prior to the upgrade, mercurial was working fine. Tonight I tried to do my first commit since the upgrade and it fails with:

```
blg@odin:~/dev/mortgage$ hg status
abort: couldn't find mercurial libraries in [/usr/bin /usr/lib/python27.zip /usr/lib/python2.7 /usr/lib/python2.7/plat-linux2 /usr/lib/python2.7/lib-tk /usr/lib/python2.7/lib-old /usr/lib/python2.7/lib-dynload /usr/lib/python2.7/site-packages]
(check your install and PYTHONPATH)
blg@odin:~/dev/mortgage$ 

```

My first thought was that maybe the upgrade uninstalled mercurial for some reason, however, KPackageKit shows it installed. I did a reinstall using apt-get instead, but this generated the following errors.

```
blg@odin:~/dev/mortgage$ apt-get install --reinstall mercurial
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
blg@odin:~/dev/mortgage$ sudo apt-get install --reinstall mercurial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libva-x11-1 g++-4.4 libstdc++6-4.4-dev libcddb2 libdvbpsi6 libx264-98 libupnp3 libxcb-randr0 libiso9660-7 libgnomevfs2-extra libxdot4
  apport-hooks-medibuntu firefox-branding libtar esound-clients libvcdinfo0 libebml2 libmatroska2 libpoppler-glib5 libsdl-image1.2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 78 not upgraded.
3 not fully installed or removed.
Need to get 0 B/1,539 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 239828 files and directories currently installed.)
Preparing to replace mercurial-common 1.7.5-1ubuntu1 (using .../mercurial-common_1.7.5-1ubuntu1_all.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 11, in <module>
    import sys,os,shutil
  File "/usr/lib/python2.7/shutil.py", line 12, in <module>
    import collections
  File "/usr/lib/python2.7/collections.py", line 8, in <module>
    from _collections import deque, defaultdict
ImportError: No module named _collections
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 11, in <module>
    import sys,os,shutil
  File "/usr/lib/python2.7/shutil.py", line 12, in <module>
    import collections
  File "/usr/lib/python2.7/collections.py", line 8, in <module>
    from _collections import deque, defaultdict
ImportError: No module named _collections
dpkg: error processing /var/cache/apt/archives/mercurial-common_1.7.5-1ubuntu1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 11, in <module>
    import sys,os,shutil
  File "/usr/lib/python2.7/shutil.py", line 12, in <module>
    import collections
  File "/usr/lib/python2.7/collections.py", line 8, in <module>
    from _collections import deque, defaultdict
ImportError: No module named _collections
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace mercurial 1.7.5-1ubuntu1 (using .../mercurial_1.7.5-1ubuntu1_i386.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 11, in <module>
    import sys,os,shutil
  File "/usr/lib/python2.7/shutil.py", line 12, in <module>
    import collections
  File "/usr/lib/python2.7/collections.py", line 8, in <module>
    from _collections import deque, defaultdict
ImportError: No module named _collections
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 11, in <module>
    import sys,os,shutil
  File "/usr/lib/python2.7/shutil.py", line 12, in <module>
    import collections
  File "/usr/lib/python2.7/collections.py", line 8, in <module>
    from _collections import deque, defaultdict
ImportError: No module named _collections
dpkg: error processing /var/cache/apt/archives/mercurial_1.7.5-1ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 11, in <module>
    import sys,os,shutil
  File "/usr/lib/python2.7/shutil.py", line 12, in <module>
    import collections
  File "/usr/lib/python2.7/collections.py", line 8, in <module>
    from _collections import deque, defaultdict
ImportError: No module named _collections
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mercurial-common_1.7.5-1ubuntu1_all.deb
 /var/cache/apt/archives/mercurial_1.7.5-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
blg@odin:~/dev/mortgage$
```

I've also tried a reinstall of python via apt-get as well. Both python-2.6 and Python-2.7 appear to be installed, but based on the problems above, it looks like the python-2.7 installation may have some library issues. Unfortunately, python is not a language I'm familiar with, so I don't know where to look next. The only similar error messages I can find in the Python bug reports relate to python 3, so I'm not sure if they're relevant here or not.

Any advice would be greatly appreciated.

---

### Post by brettski74 on 2011-05-06
I've done a little more digging...

I have a vanilla linux installation tarball, so I extracted that onto a separate drive, chrooted into it, and built a vanilla Python 2.7.1 install there. It seems that the Python installation in my Natty installation is missing several shared objects - at least the following:

/usr/lib/python2.7/lib-dynload/_collections.so
/usr/lib/python2.7/lib-dynload/operator.so
/usr/lib/python2.7/lib-dynload/itertools.so
/usr/lib/python2.7/lib-dynload/select.so
/usr/lib/python2.7/lib-dynload/fcntl.so
/usr/lib/python2.7/lib-dynload/_struct.so
/usr/lib/python2.7/lib-dynload/binascii.so

I've copied them into my Natty install. I know this is not the "right" way, but given no better alternative, I figure I need to figure out and prove what's missing so I can figure out what packages haven't installed propertly and fix them. The mercurial and python reinstallation no longer errors, however, dpkg-query -l still lists both python and mercurial as half-installed and reinstallation required:

```
blg@odin:/var/cache/apt/archives$ dpkg-query -l mercurial
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version                        Description
+++-==============================-==============================-============================================================================
ii  mercurial                      1.7.5-1ubuntu1                 scalable distributed version control system
blg@odin:/var/cache/apt/archives$ dpkg-query -l python
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version                        Description
+++-==============================-==============================-============================================================================
ii  python                         2.7.1-0ubuntu5                 interactive high-level object-oriented language (default version)
blg@odin:/var/cache/apt/archives$ 
```

I had a look at the package contents of the python package using dpkg-query -L. It appears that the python libraries are not included in the main python package. I'm assuming they're installed as part of another package, but I haven't figured out how to find where, yet.

Beyond that, from the mercurial package file listing, it looks like the mercurial libraries are installed in /usr/lib/pyshared/python2.7/mercurial. I've updated my PYTHONPATH to /usr/lib/pyshared/python2.7:/usr/lib/pyshared/python2.7/mercurialbut I'm still getting the same problem when I try to run mercurial.

```
blg@odin:~/dev/mortgage$ hg status
abort: couldn't find mercurial libraries in [/usr/bin /usr/lib/pyshared/python2.7 /usr/lib/pyshared/python2.7/mercurial /usr/lib/python27.zip /usr/lib/python2.7 /usr/lib/python2.7/plat-linux2 /usr/lib/python2.7/lib-tk /usr/lib/python2.7/lib-old /usr/lib/python2.7/lib-dynload /usr/lib/python2.7/site-packages]
(check your install and PYTHONPATH)
blg@odin:~/dev/mortgage$ 
```

Again, I am confused. I'll keep digging, but any assistance would be much appreciated.

---

### Post by brettski74 on 2011-05-07
I reverted the default python version back to 2.6.6 by

  - changing the default version in /usr/share/python/debian_defaults and then
  - changing the symbolic link in /usr/bin to point to python2.6.

Mercurial now works, which solves my problem and for anyone else who's recently upgraded to Natty and finds mercurial to be broken, I'd suggest changing back to python 2.6.

That said, there still seems to be some problems with the python2.7 installation that comes with Natty. It would be good to identify whether this is something specific to my install or a more general problem with the  python2.7 packages. As mentioned earlier, I couldn't find a python 2.7 package that contained the missing library files, so I'm guessing it's a package problem, but given my limited knowledge of python or the debian packaging system, I'd welcome any input from any python/debian gurus on how to verify whether this is a more general problem worthy of a bug report.

Thanks.

---

### Post by muneson on 2011-05-22
I ran into the same thing and your solution fixed it, thanks.
However, the revert to 2.6 is not unproblematic -- utilities
for administration and similar may find themselves 
missing libraries. For instance,
in my case hp-setup stopped working. When started from 
the command-line it said that it couldn't find module
hpmudext. I found this for 2.7 but not for 2.6:

~$ ll /usr/lib/pyshared/python2.7/hpmudext.so 
-rw-r--r-- 1 root root 15024 2011-03-25 18:26 /usr/lib/pyshared/python2.7/hpmudext.so


~$ ll /usr/lib/pyshared/python2.6/hpmudext.so 
ls: cannot access /usr/lib/pyshared/python2.6/hpmudext.so: No such file or directory


I am unsure about general *.so compatibility between versions but if needed the first fix to be tried is perhaps symlinking. 

In this particular case I didn't bother to try -- hp-setup is not a very central utility and there are other tools for setting up printers.
The point, however, is that one should be aware of the risks of default version switching before taking the plunge.

---

