---
title: "Python-apport, python-problem-report broken in Ubuntu 14.04"
date: 2014-11-15
forum: Installation &amp; Upgrades
---

### Post by rwohlhueter on 2014-11-15
Since upgrading to 14.04 (Ubuntu studio, on AMD64 machine), I have frequently gotten "system error" pop-ups, which seem to point to Python installation problems impinging, for example on the "printer-manager" module in the "settings manager" not functioning.

Using Synaptic in attempts to remove or reinstall offending software packages, I get errors (lots of output copied below), which point to python-apport and/or python-problem-report packages as culprits.  The current state of affairs is that Synaptic flags python-problem-report, installed verion 2.14.1-Oubuntu3.4 as "broken" (version3.5 is  is, but is okay); no effort to "fix broken packages" or remove or reinstall are of any avail.  I am thus unable to remove or reinstall other, potentially problematic packages.

Any hints at how to break out of this conundrum will be appreciated.

Bob Wohlhueter

[attempts to "apply" install, upgrade, of removal of any package gives these errors]

E: /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb: subprocess new pre-removal script returned error exit status 1


[detailed logs of synaptic errors are pasted below]

(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already[synaptic changes applied errors]

(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat


SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat


    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation scrip(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

t returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal scr(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

ipt returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal scr(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

ipt returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state;(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

 you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in g(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

et_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-pri(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

nter-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat


 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat


                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat


SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat


    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation scrip(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

t returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal scr(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

ipt returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal scr(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

ipt returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state;(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

 you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in g(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

et_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-pri(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

nter-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API[synaptic changes applied errors]

(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat


SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat


    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation scrip(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

t returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal scr(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

ipt returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal scr(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

ipt returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state;(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

 you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in g(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

et_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-pri(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

nter-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2(synaptic:15121): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 611451 files and directories currently installed.)
Preparing to unpack .../apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-problem-report_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-apport_2.14.1-0ubuntu3.5_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-problem-report_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-apport_2.14.1-0ubuntu3.5_all.deb
 /var/cache/apt/archives/python-cupshelpers_1.4.3+20140219-0ubuntu2.2_all.deb
 /var/cache/apt/archives/python-libxml2_2.9.1+dfsg1-3ubuntu4.4_amd64.deb
 /var/cache/apt/archives/python-numpy_1%3a1.8.2-0ubuntu0.1_amd64.deb
 /var/cache/apt/archives/python-requests_2.2.1-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package python-requests (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-problem-report (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-numpy (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
Setting up gconf2 (3.2.6-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 121, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 18, in get_valid_languages
    langs.add(l.split('_')[0])
TypeError: Type str doesn't support the buffer API
dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat


 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat


dpkg: error processing package gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-libxml2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package apport (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python-libxml2; however:
  Package python-libxml2 is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.

dpkg: error processing package python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python-cupshelpers; however:
  Package python-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu5.1); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-requests
 python-problem-report
 python-cupshelpers
 python-numpy
 system-config-printer-common
 gconf2
 python-libxml2
 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat


 apport
 system-config-printer-gnome
 apport-gtk
 python-apport
 libreoffice-gnome
 system-config-printer-udev
 xchat-common
 xchat

---

### Post by ian-weisser on 2014-11-15
Looks like you somehow managed to delete Python 2.7, or at least part of it's standard library.

ConfigParser is provided by the package *libpython2.7-minimal* . Try reinstalling that package.

---

### Post by rwohlhueter on 2014-11-15
Your idea provides a good hint; I think it's not a matter of deleting python2.7 or its standard library, but of pointing my shell to the wrong places.  In fact, I have a bunch of scientific software on my machine, some of which requires python2.7, some 3.4.  In fact, I had been tinkering a few weeks ago to get some new software working properly with python3.4.  Currently, I my /usr/bin has both python2.7 and python3.4, but /usr/bin/python is linked to 3.4.  Moreover, I have in my .cshrc file "setenv PYTHONHOME /usr/lib/python2.7:/usr/lib/python3.4"  and "setenv PYTHONPATH $BALL_HOME/ball/build/lib:$PYROSETTA/:/usr/local/lib/modeller9.12/lib/x86_64-intel8", 
I haven't re-tinkered these, because I sure it will break these other applications that I got working by so tinering.
But I would generalize the question:  Is there any suave way of directing applications which need 2.7 and its libs appropriately, while simultaneously directing applications requiring 3.4 and its libs to their appropriate place?

---

### Post by ian-weisser on 2014-11-15
> **rwohlhueter said:**
> /usr/bin/python is linked to 3.4
Ah, yes. That would certainly cause the problem you are having.
The system default is still 2.7. Not all packages have been converted to Python3 yet. That transition is ongoing.

> **rwohlhueter said:**
>  But I would generalize the question:  Is there any suave way of directing applications which need 2.7 and its libs appropriately, while simultaneously directing applications requiring 3.4 and its libs to their appropriate place?
I don't know of one. Scripts aren't aware of which interpreter they need until a human tells them...in the shebang line. 


While your package management is broken, it is unlikely that you will receive any security updates. If your system is online, it may have unpatched vulnerabilities. Do be sure to back up your data and protect your system from intrusion vectors.

---

### Post by rwohlhueter on 2014-11-16
Yeah, that's my conundrum now:  Synaptic flags package "python-apport" as broken, but "fix broken packages is to no avail.  Moreover, only options not grayed-out are "unmark", "mark for upgrade" and "mark for removal" -- neither upgade nor removel work (nor can I upgade or remove anything else with Synaptic.  When attempting to remove "python-apport", I get the message "E: python-apport: package is in a very bad inconsistent state; you should  reinstall it before attempting a removal".

Is there anyway I can force reinstallation outside of Synaptic?

---

### Post by rwohlhueter on 2014-11-16
Okay, I think I've got things fixed up.  Basically went through the error-flagged packages with `apt-get build-dep`.  Running this on python-launchpadlib and python-apport seems to have cleaned things up, that is no more nasty error messages, and "settings | printers" (which was the first problem I noticed) now works again.
I haven't dealt with the couple of external software packages that depend on Python3+.  But maybe I can figure out start-up scripts for them that set up a specific Python3.4 environment without applying these globally.

Thanks for your help.

---

