---
title: "Error when updating to Ubuntu 16.04"
date: 2016-08-25
forum: Installation &amp; Upgrades
---

### Post by manabulous on 2016-08-25
Hi!

I haven't used my Virtual Box in about 3 months and today when I returned, I realized there was a distro update to 16.04. Anytime I try to update using any sort of command, I get this error:

[ATTACH=CONFIG]270861[/ATTACH]

(text: E: The package linux-headers-3.13.0-92 needs to be reinstalled, but I can't find an archive for it.E: Internal error opening cache (1). Please report.)

And when I run apt-get update, I get this:

Reading package lists... Done                
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Unknown Multi-Arch type 'no' for package 'libxapian-dev'
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'kwin'
W: Unknown Multi-Arch type 'no' for package 'kwin-dev'
W: Unknown Multi-Arch type 'no' for package 'kwin-wayland'
W: Unknown Multi-Arch type 'no' for package 'kwin-x11'
W: Unknown Multi-Arch type 'no' for package 'libkf5sysguard-dev'
W: Ignoring Provides line with DepCompareOp for package php-psr-http-message-implementation
W: Ignoring Provides line with DepCompareOp for package php-psr-log-implementation
W: Ignoring Provides line with DepCompareOp for package php-seclib
W: Ignoring Provides line with DepCompareOp for package php-sabre-http
W: Ignoring Provides line with DepCompareOp for package php-math-biginteger
W: Ignoring Provides line with DepCompareOp for package pypy-cffi
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Unknown Multi-Arch type 'no' for package 'libxapian-dev'
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'kwin-dev'
W: Unknown Multi-Arch type 'no' for package 'kwin-wayland'
W: Unknown Multi-Arch type 'no' for package 'kwin-x11'
W: Unknown Multi-Arch type 'no' for package 'libkf5sysguard-dev'
W: Ignoring Provides line with DepCompareOp for package pypy-cffi
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Ignoring Provides line with DepCompareOp for package php-math-biginteger
W: Ignoring Provides line with DepCompareOp for package pypy-cffi
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Ignoring Provides line with DepCompareOp for package pypy-cffi
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
W: You may want to run apt-get update to correct these problems

Any help would be appreciated.

Thanks!

---

### Post by manabulous on 2016-08-25
To Bucky Ball:

I have, that's where I first encountered the issue.
I recently tried running the command sudo update-manager and this is what I get:

user@user-VirtualBox:~$ sudo update-manager
[sudo] password for user: 
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 114, in <module>
    app = UpdateManager(data_dir, options)
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 113, in __init__
    self.options and self.options.use_proposed)
  File "/usr/lib/python3/dist-packages/UpdateManager/MetaReleaseGObject.py", line 44, in __init__
    MetaReleaseCore.__init__(self, useDevelopmentRelease, useProposed)
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 94, in __init__
    cache = apt.Cache()
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 107, in __init__
    self.open(progress)
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 152, in open
    self._depcache = apt_pkg.DepCache(self._cache)
SystemError: E:The package linux-headers-3.13.0-92 needs to be reinstalled, but I can't find an archive for it.
user@user-VirtualBox:~$ 

I know that the error has to do with the system not being able to read/find the header packages.

---

