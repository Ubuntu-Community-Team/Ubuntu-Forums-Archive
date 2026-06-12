---
title: "cannot import name '_error' from partially initialized module 'libdnf'"
date: 2022-11-16
forum: Installation &amp; Upgrades
---

### Post by snagara-07 on 2022-11-16
Hi, 

As we are migrating from centos 7 to ubuntu 22.04, I need to migrate from yum to dnf, yum is not supported on ubuntu 22.04 LTS. So I installed "dnf" package and "yum4" too.
with python 3.11.0rc1. 

when I did "import dnf" I'm getting below error:

Traceback (most recent call last):
  File "/sandbox/sandbox1/snagara/SreeRam/repo/unity-stratus/install/repos/./resolve_deps.py", line 6, in <module>
    import optparse, sys, dnf.base ,logging
  File "/usr/lib/python3/dist-packages/dnf/__init__.py", line 30, in <module>
    import dnf.base
  File "/usr/lib/python3/dist-packages/dnf/base.py", line 29, in <module>
    import libdnf.transaction
  File "/usr/lib/python3/dist-packages/libdnf/__init__.py", line 8, in <module>
    from . import error
  File "/usr/lib/python3/dist-packages/libdnf/error.py", line 13, in <module>
    from . import _error
ImportError: cannot import name '_error' from partially initialized module 'libdnf' (most likely due to a circular import) (/usr/lib/python3/dist-packages/libdnf/__init__.py)

Should be standard error I believe. I need help to fix this. I could have renamed _error.py in libdnf, but I need input from this forum.

---

### Post by Paddy Landau on 2022-11-17
Ubuntu isn't really made for dnf. It's a Debian derivative and is made for apt instead.

Are you trying to install downloaded apps? The preferred method for installation on Ubuntu is via the standard repositories, snap, or flatpak, instead of using downloaded files. Have a look in the Software Store to see if it has the apps that you want. You can also check flatpak, which isn't installed by default, but I can walk you through it if you want.

---

