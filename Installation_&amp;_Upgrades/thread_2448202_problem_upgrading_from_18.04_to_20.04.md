---
title: "problem upgrading from 18.04 to 20.04"
date: 2020-08-04
forum: Installation &amp; Upgrades
---

### Post by marsh0404 on 2020-08-04
Apologises in advance if this is too basic a question or inappropriate for this forum. If anyone can help it would be much appreciated. My own skill base is very basic.

I'm trying to upgrade from ubuntu 18.04 to 20.04 using "sudo do-release-upgrade" but I get the error message below. Can anyone suggest what I can do to resolve this problem and be able to upgrade? Thanks.


Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 11, in <module>
    from UpdateManager.Core.MetaRelease import MetaReleaseCore
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 25, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'

---

