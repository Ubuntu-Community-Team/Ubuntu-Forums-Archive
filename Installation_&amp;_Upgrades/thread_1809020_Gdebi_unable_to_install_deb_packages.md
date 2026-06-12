---
title: "Gdebi unable to install deb packages"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by radiobert on 2011-07-21
Hi all,
Recently my Gdebi cannot be started by clicking on any .deb files nor with context menu "open with...". Now I can't install deb files using Gdebi anymore, and must use dpkg instead. I then removed Gdebi and install again, but the result is the same.
I tried starting GDebi from terminal with parameter "--help", and this is what I get: 

```
tyf@tyf-desktop:~$ gdebi --help
Traceback (most recent call last):
  File "/usr/bin/gdebi", line 35, in <module>
    from GDebi.GDebiCli import GDebiCli
  File "/usr/lib/python2.6/dist-packages/GDebi/GDebiCli.py", line 35, in <module>
    from DebPackage import DebPackage, Cache
  File "/usr/lib/python2.6/dist-packages/GDebi/DebPackage.py", line 33, in <module>
    from debian_bundle.debfile import DebFile
  File "/usr/lib/pymodules/python2.6/debian_bundle/debfile.py", line 18, in <module>
    import gzip
ValueError: bad marshal data
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 53, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 18, in <module>
    from problem_report import ProblemReport
  File "/usr/lib/python2.6/dist-packages/problem_report.py", line 14, in <module>
    import zlib, base64, time, UserDict, sys, gzip, struct
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/gdebi", line 35, in <module>
    from GDebi.GDebiCli import GDebiCli
  File "/usr/lib/python2.6/dist-packages/GDebi/GDebiCli.py", line 35, in <module>
    from DebPackage import DebPackage, Cache
  File "/usr/lib/python2.6/dist-packages/GDebi/DebPackage.py", line 33, in <module>
    from debian_bundle.debfile import DebFile
  File "/usr/lib/pymodules/python2.6/debian_bundle/debfile.py", line 18, in <module>
    import gzip
ValueError: bad marshal data

```
Has anybody dealt with this problem before? What should I do now?:confused:

---

### Post by radiobert on 2011-07-25
huh, finally solved the problem, just by using the following command:
```
sudo aptitude reinstall python2.6
```
everything works fine again!:)

---

