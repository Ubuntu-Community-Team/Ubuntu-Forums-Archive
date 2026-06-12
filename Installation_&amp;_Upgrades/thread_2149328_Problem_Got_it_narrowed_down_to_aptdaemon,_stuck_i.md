---
title: "Problem: Got it narrowed down to aptdaemon, stuck in a loop now."
date: 2013-05-28
forum: Installation &amp; Upgrades
---

### Post by p2bc on 2013-05-28
Have had a problem of one way or another for two months now with installing packages after a heck of a lot of searching and checking and double checking I gotten ride of most but this one is getting to me now, its turn into an endless loop. Got a broken package "aptdeamon", to fix it would be simple enough, but it is a dependent of other packages, python-aptdaemon and the like, which all want to be re-installed but can't because aptdeamon is broken, and aptdeamon can't be fixed because python-aptdaemon comes back with errors when it tried to re-install. Do you see the endless loop.

I did do some searching on these forums and else where for aptdeamon problems and found things from a year ago, but they don't seem to apply here, but might be what cause it to be broken initially, who knows. Right now I am looking to get out of the loop so I can address the aptdaemon broken issue.

Now I have done every varient of:
```

sudo apt-get  -f install
sudo apt-get --fix-broken install

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo dpkg --configure -a

```
... you can think of and more that I have not posted here.

Used Synaptic to try fix broken package.
Tried to Ubuntu Center, but can't since it use python-aptdaemon.

I truely believe if I could isolate the install of just aptdaemon without the re-install happening first 90% of my problem would be solve. But no matter which was I try, it always try to run the re-install (ie python-aptdeamon) before aptdaemon fix.

Here is just one of several examples of the errors I get, for the record I did an "autoremove" just before and got a similiar error, and as you can see the old files were still there.
```

sudo apt-get --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2:i386 libnumber-compare-perl libqt4-declarative:i386
  libqt4-script:i386 libqt4-network:i386 libfile-find-rule-perl
  libqt4-dbus:i386 sni-qt:i386 libmysqlclient18:i386 libqt4-xmlpatterns:i386
  libqtcore4:i386 libqt4-sql:i386 libqt4-xml:i386 libtext-glob-perl
  libxss1:i386 libqtgui4:i386 libqt4-sql-mysql:i386 libqtwebkit4:i386
  libaudio2:i386 libxv1:i386 libmng1:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apport language-selector-common language-selector-gnome python-apport
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
  python-problem-report
The following packages will be upgraded:
  apport language-selector-common language-selector-gnome python-apport
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
  python-problem-report
8 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.
22 not fully installed or removed.
Need to get 0 B/16.4 MB of archives.
After this operation, 10.2 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 372856 files and directories currently installed.)
Preparing to replace python-aptdaemon.gtk3widgets 0.43+bzr805-0ubuntu8 (using .../python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu9_all.deb) ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu9_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 36, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named ConfigParser
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-aptdaemon.pkcompat 0.43+bzr805-0ubuntu8 (using .../python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu9_all.deb) ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu9_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 36, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named ConfigParser
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-aptdaemon 0.43+bzr805-0ubuntu8 (using .../python-aptdaemon_0.43+bzr805-0ubuntu9_all.deb) ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/python-aptdaemon_0.43+bzr805-0ubuntu9_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 36, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named ConfigParser
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace language-selector-gnome 0.79.2 (using .../language-selector-gnome_0.79.3_all.deb) ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/language-selector-gnome_0.79.3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 36, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named ConfigParser
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace language-selector-common 0.79.2 (using .../language-selector-common_0.79.3_all.deb) ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/language-selector-common_0.79.3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 36, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named ConfigParser
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-problem-report 2.0.1-0ubuntu17.1 (using .../python-problem-report_2.0.1-0ubuntu17.2_all.deb) ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/python-problem-report_2.0.1-0ubuntu17.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 36, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named ConfigParser
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-apport 2.0.1-0ubuntu17.1 (using .../python-apport_2.0.1-0ubuntu17.2_all.deb) ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/python-apport_2.0.1-0ubuntu17.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 36, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named ConfigParser
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace apport 2.0.1-0ubuntu17.1 (using .../apport_2.0.1-0ubuntu17.2_all.deb) ...
apport stop/waiting
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pyclean", line 64
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/apport_2.0.1-0ubuntu17.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              apport start/running
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 36, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named ConfigParser
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace virtualbox 4.1.12-dfsg-2ubuntu0.2 (using .../virtualbox_4.1.12-dfsg-2ubuntu0.2_amd64.deb) ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: error processing /var/cache/apt/archives/virtualbox_4.1.12-dfsg-2ubuntu0.2_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                                File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu9_all.deb
 /var/cache/apt/archives/python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu9_all.deb
 /var/cache/apt/archives/python-aptdaemon_0.43+bzr805-0ubuntu9_all.deb
 /var/cache/apt/archives/language-selector-gnome_0.79.3_all.deb
 /var/cache/apt/archives/language-selector-common_0.79.3_all.deb
 /var/cache/apt/archives/python-problem-report_2.0.1-0ubuntu17.2_all.deb
 /var/cache/apt/archives/python-apport_2.0.1-0ubuntu17.2_all.deb
 /var/cache/apt/archives/apport_2.0.1-0ubuntu17.2_all.deb
 /var/cache/apt/archives/virtualbox_4.1.12-dfsg-2ubuntu0.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Anyways would appreciate some advise. Thanks

---

### Post by dino99 on 2013-05-28
you should have better chance to fix it if you boot in recovery mode: enable the network, then select "dpkg" to try fixing the system, and finally select "resume" to continue normal booting.

if your system have some ppas activated, then you might have some possible conflicts, try to purge them first (ppa-purge). If that fail, then a fresh new install is the best choice to get a clean installation. (can be done using the mini-iso)

---

### Post by p2bc on 2013-05-28
Thanks I'll try that.

---

### Post by p2bc on 2013-05-28
Well tried it and no dice.

 I have considered a fresh install but I would like to exhaust all the possibilities first.

---

