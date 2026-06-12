---
title: "Upgrade Failed. Afraid to reboot."
date: 2018-08-23
forum: Installation &amp; Upgrades
---

### Post by Tadaen_Sylvermane on 2018-08-23
One would think a distro that is supposedly enterprise ready would be beyond this crap. Back to Debian. Adios.

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

---

### Post by ajgreeny on 2018-08-23
**Please do not create duplicate posts;** it is confusing for all including you and dilutes the forum's ability to help. 
[https://ubuntuforums.org/showthread.php?t=2399286&p=13794544#post13794544](https://ubuntuforums.org/showthread.php?t=2399286&p=13794544#post13794544)

Closed.

---

