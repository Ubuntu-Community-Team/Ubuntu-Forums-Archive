---
title: "Processing was halted because there were too many errors"
date: 2016-11-29
forum: Installation &amp; Upgrades
---

### Post by wildweaselmi2 on 2016-11-29
Today I tried to upgrade my 14.x version of Ubuntu by performing a sudo do-release-upgrade after I made sure all updates were performed and system was rebooted.

The upgrade started spitting out errors and eventually produced
```
Processing was halted because there were too many errors.


Upgrade complete


The upgrade has completed but there were errors during the upgrade
process.


To continue please press [ENTER]
=== Command terminated with exit status 1 (Tue Nov 29 13:54:04 2016) ===

```


In another window I tried to run sudo apt-get -f install and am getting the following
```
Preparing to unpack .../python-gobject-2_2.28.6-12ubuntu1_i386.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
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
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 20, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: No module named 'apt_pkg'


Original exception was:
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
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 20, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: No module named 'apt_pkg'


Original exception was:
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-gobject-2_2.28.6-12ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
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
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 20, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: No module named 'apt_pkg'


Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-appindicator_12.10.1+15.04.20141110-0ubuntu1_i386.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
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
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 20, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: No module named 'apt_pkg'


Original exception was:
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
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 20, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: No module named 'apt_pkg'


Original exception was:
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-appindicator_12.10.1+15.04.20141110-0ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
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
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 20, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: No module named 'apt_pkg'


Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin (2.23-0ubuntu4) ...
Errors were encountered while processing:
 /var/cache/apt/archives/python-gobject-2_2.28.6-12ubuntu1_i386.deb
 /var/cache/apt/archives/python-appindicator_12.10.1+15.04.20141110-0ubuntu1_i386.deb
W: No sandbox user '_apt' on the system, can not drop privileges
E: Sub-process /usr/bin/dpkg returned an error code (1)  

```

I'm not sure what to do to make sure I don't loose my server.  I feel if I reboot it may not come back up.  Does anyone have any suggestions on how to approach this?

---

### Post by ian-weisser on 2016-11-29
1) Backup your data first. A reinstall may be unavoidable.

2) An approximate number of errors during the upgrade would be helpful. 3? 300?
Check /var/log for an upgrade log.

3) Test apt: 'sudo apt update' and 'sudo apt upgrade'. If either errors, please show us the complete output.
If apt is broken, then we must fix it using dpkg...sometimes a tedious process.

---

