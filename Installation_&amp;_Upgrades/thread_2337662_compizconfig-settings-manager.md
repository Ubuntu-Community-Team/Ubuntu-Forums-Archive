---
title: "compizconfig-settings-manager"
date: 2016-09-20
forum: Installation &amp; Upgrades
---

### Post by pete_evans on 2016-09-20
Hi,

I'm running 16.04, I was getting errors in the Software Updater regarding the above.  Playing around with Synaptic I eventually got the instruction to try & re-install.  It looks like an issue with the removal of existing stuff.  Anyone else seen this?

apt-get install compizconfig-settings-manager
 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  compizconfig-settings-manager
1 to upgrade, 0 to newly install, 0 to remove and 5 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/575 kB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously unselected package compizconfig-settings-manager.
(Reading database ... 534774 files and directories currently installed.)
Preparing to unpack .../compizconfig-settings-manager_1%3a0.9.12.2+16.04.20160823-0ubuntu1_all.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/compizconfig-settings-manager_1%3a0.9.12.2+16.04.20160823-0ubuntu1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/compizconfig-settings-manager_1%3a0.9.12.2+16.04.20160823-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

