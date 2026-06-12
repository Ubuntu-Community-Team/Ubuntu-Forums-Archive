---
title: "Unable to upgrade / reinstall and remove gmountiso"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by squidaway on 2010-05-01
Hi, when i try to upgrade my system via apt i get the following error:

> 
user@user-desktop:~$ sudo apt-get upgrade

Reading package lists... Done                  
Building dependency tree                       
Reading state information... Done              
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
17 not fully installed or removed.                            
Need to get 0B/16.6kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

(Reading database ... 240370 files and directories currently installed.)
Preparing to replace gmountiso 0.4-0ubuntu3 (using .../gmountiso_0.4-0ubuntu3_all.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...

Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2196, in <module>
    main()
  File "/usr/bin/pycentral", line 2190, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1645, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 381, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 414, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing /var/cache/apt/archives/gmountiso_0.4-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/gmountiso_0.4-0ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

user@user-desktop:~$


apt-get remove gmountiso won't let me remove it either.

> 
user@user-desktop:~$ sudo apt-get remove gmountiso

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  gmountiso

0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
17 not fully installed or removed.
After this operation, 180kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing gmountiso (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 gmountiso
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@user-desktop:~$



what to do? :confused:

---

### Post by squidaway on 2010-05-01
Found this page:
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/369691](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/369691)
Seems to be much the same problem, but i still cant get it working :confused:

Also tried:
sudo apt-get -f install
apt-get --purge remove gmountiso

The bug-page here has some workarounds, but i cant get any of the two to work in my case.
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096)

I need some help with this. Cause it seems as if i cant install any updates without fixing this first. ](*,)

---

