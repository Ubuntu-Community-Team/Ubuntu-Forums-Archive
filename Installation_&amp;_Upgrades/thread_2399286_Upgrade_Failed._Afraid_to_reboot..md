---
title: "Upgrade Failed. Afraid to reboot."
date: 2018-08-23
forum: Installation &amp; Upgrades
---

### Post by Tadaen_Sylvermane on 2018-08-23
It ran through the upgrade process, then stopped with an error leaving a few packages undone. When I run the command again, this is what I get.

```
jason@failbox:~$ sudo do-release-upgrade[sudo] password for jason: 
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 11, in <module>
    from UpdateManager.Core.MetaRelease import MetaReleaseCore
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 25, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN13debListParser12ParseDependsEPKcS1_RNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEES8_RjRKbSB_SB_RKS7_ version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 63, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
    import apport.fileutils
  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 23, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN13debListParser12ParseDependsEPKcS1_RNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEES8_RjRKbSB_SB_RKS7_ version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference


Original exception was:
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 11, in <module>
    from UpdateManager.Core.MetaRelease import MetaReleaseCore
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 25, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-36m-x86_64-linux-gnu.so: symbol _ZN13debListParser12ParseDependsEPKcS1_RNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEES8_RjRKbSB_SB_RKS7_ version APTPKG_5.0 not defined in file libapt-pkg.so.5.0 with link time reference

```

Doing a fresh install from 18.04 ISO. Like to know the answer to this though?

---

### Post by LHammonds on 2018-08-23
If you installed 18.04, what are you trying to accomplish with "do-release-upgrade"?  That command is for upgrading major versions such as 16.04 to 18.04.

If this was a fresh 18.04 install, then all you needed to do in order to get the latest patches and bring it to 18.04.1 is the following:

```

sudo apt update
sudo apt upgrade

```

---

### Post by Tadaen_Sylvermane on 2018-08-23
I was on 16.04. I tried to upgrade to 18.04 instead of fresh installing. I'm currently in process of installing 18.04 from an ISO as the upgrade ended in my opening post. Apologies for not being clear. Was pretty upset about this earlier today when I posted. Still working on recovery this afternoon. Had another issue take my time today.

I followed this in hopes of keeping useless junk off my system. Could this have caused my problem above when trying to upgrade?

[https://superuser.com/questions/615565/can-i-make-apt-get-always-use-no-install-recommends](https://superuser.com/questions/615565/can-i-make-apt-get-always-use-no-install-recommends)

---

### Post by LHammonds on 2018-08-24
I will have to defer this answer to others.  I do not do in-place upgrades nor have I used the no-install-recommends option.

Sorry for your troubles,
LHammonds

---

