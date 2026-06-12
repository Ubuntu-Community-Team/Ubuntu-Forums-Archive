---
title: "apt-get problem - EOFError: EOF read where object expected"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by eivindw on 2007-11-15
Been trying to search the forums without finding this problem.

When I run the update manager in Gnome, the following error occurs:

> **Software index is broken**
... Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

When I run both Synaptic or the command line with the -f flag I get the following output:

```
[sudo] password for eivindw:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-bittorrent python-gmenu
Suggested packages:
  python-gmenu-dbg
The following packages will be upgraded:
  python-bittorrent python-gmenu
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
6 not fully installed or removed.
Need to get 0B/182kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 98040 files and directories currently installed.)
Preparing to replace python-bittorrent 3.4.2-11ubuntu2 (using .../python-bittorrent_3.4.2-11ubuntu3~7.10_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 7, in <module>
    import pyversions
EOFError: EOF read where object expected
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 7, in <module>
    import pyversions
EOFError: EOF read where object expected
dpkg: error processing /var/cache/apt/archives/python-bittorrent_3.4.2-11ubuntu3~7.10_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 7, in <module>
    import pyversions
EOFError: EOF read where object expected
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace python-gmenu 2.20.0-0ubuntu1 (using .../python-gmenu_2.20.1-0ubuntu1_i386.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 7, in <module>
    import pyversions
EOFError: EOF read where object expected
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 7, in <module>
    import pyversions
EOFError: EOF read where object expected
dpkg: error processing /var/cache/apt/archives/python-gmenu_2.20.1-0ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 7, in <module>
    import pyversions
EOFError: EOF read where object expected
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace hwdb-client-common 0.6.11 (using .../hwdb-client-common_0.6.11_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 7, in <module>
    import pyversions
EOFError: EOF read where object expected
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 7, in <module>
    import pyversions
EOFError: EOF read where object expected
dpkg: error processing /var/cache/apt/archives/hwdb-client-common_0.6.11_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 7, in <module>
    import pyversions
EOFError: EOF read where object expected
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-bittorrent_3.4.2-11ubuntu3~7.10_all.deb
 /var/cache/apt/archives/python-gmenu_2.20.1-0ubuntu1_i386.deb
 /var/cache/apt/archives/hwdb-client-common_0.6.11_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Seems to me the same error is repeated for all the 3 packages mentioned (python-bittorrent, python-gmenu and hwdb-client-common).

Tried marking python-bittorrent for removal. But it seems like it's going to remove a lot of other packages, including ubuntu-desktop. So I haven't dared try that yet.

I'm pretty new to Ubuntu and the apt system. Would appreciate any suggestions to fix this problem. Synaptic won't let me install anything before the problem is fixed..

---

### Post by eivindw on 2007-11-17
Is there anyone who can suggest anything on this? Or point me to a different forum/direction? Is this the wrong forum for this kind of questions?

Seems all i find on google when searching for the problem is my own post.. :(

---

### Post by codeworker1 on 2008-01-23
Hi.
Had a similar problem with EOF in a different 'import <python file>' in the install.
The problem is with the file that is being imported.

Looking at you post, find and have a look at the file 'pyversions.py' that is imported. 

Something like:  find . -name pyversions.py

Open the file in a editor and scroll to the bottom of the file (you need to be root). 
If there is no return at the very end of the code add one, save the file and try doing another update.

This cured my problem (the same as yours but in a different python file).

Cheers.
Codeworker1

---

