---
title: "corrupted file system"
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by tp21 on 2013-03-11
hi,
after an update yesterday, my file system was corrupted. i couldn't log in because there were errors found while cheking the disk drive. after a series of fsck and reboots and recovery modes, i managed to log in. the first thing i wanted to do is to install gsmartcontrol to check the filesystem, but i found out that i can't load synaptic, and my dpkg gives error, so i can not install anything manually.
i don't know where to start to rescue the disk.
please help
thanks
ubuntu 12.10 on apple macbook pro

---

### Post by darkod on 2013-03-11
You can start by posting the error dpkg gives you. Sometimes it's only a file that you can delete. Also, you can try solving broken or unconfigured packages with:
```
sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by tp21 on 2013-03-11
thanks for the answer.
here are the dpkg errors:
dpkg: warning: files list file for package 'popularity-contest' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcaca0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ghostscript-x' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'myspell-en-za' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libshout3:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ttf-farsiweb' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnl1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtag1-vanilla:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libexempi3:amd64' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'phonon-backend-xine' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by tgalati4 on 2013-03-11
That does not look good.  Typically when you are missing files for installed packages, that points to a failing drive.  It's possible that your apt cache has been corrupted, because dpkg can't correlate the files list with installed files for several packages.

```
sudo apt-get clean
sudo apt-get check
sudo apt-get moo
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

---

### Post by tp21 on 2013-03-12
thanks, it really doesn't look good.
i tried to install smartmontools, but i received a bunch of errors: 
heissam@orbit:/var/lib/dpkg/info$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smartmontools is already the newest version.
The following packages were automatically installed and are no longer required:
  calligra-l10n-de calligra-l10n-engb cdparanoia duplicity easytag gir1.2-caribou-1.0
  gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gkbd-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-ibus-1.0
  gir1.2-indicate-0.7 gir1.2-syncmenu-0.1 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-totem-plparser-1.0 gir1.2-upowerglib-1.0
  gir1.2-xkl-1.0 gjs glib-networking:i386 gpsd gstreamer0.10-plugins-good:i386
  gstreamer0.10-x:i386 gtk2-engines:i386 gtk2-engines-murrine:i386
  gtk2-engines-pixbuf:i386 hyphen-en-us ibus-gtk:i386 icoutils k3b-data
  kde-base-artwork kde-baseapps-data kde-runtime-data kde-workspace-data
  kde-workspace-kgreet-plugins kdevelop-l10n kdevelop-php-docs-l10n kdevelop-php-l10n
  ksysguardd lib32gcc1 lib32stdc++6 lib32z1 libaa1:i386 libaio1:i386 libao4:i386
  libatk1.0-0:i386 libaudiofile1:i386 libavc1394-0:i386 libboost-thread1.49.0
  libcaca0:i386 libcanberra-gtk-module:i386 libcanberra-gtk0:i386 libcanberra0:i386
  libcap2:i386 libcaribou-common libcaribou0 libcdt4 libcln6 libcroco3:i386
  libcupsimage2:i386 libcurl3:i386 libdbus-glib-1-2:i386 libdmapsharing-3.0-2
  libdv4:i386 libesd0:i386 libgail-common:i386 libgail18:i386 libgconf-2-4:i386
  libgdbm3:i386 libgettextpo0:i386 libgjs0c libgnome-keyring0:i386 libgps20
  libgrantlee-core0 libgraph4 libgraphicsmagick3 libgstreamer1.0-0 libgtk2.0-0:i386
  libgudev-1.0-0:i386 libgvc5 libibus-1.0-0:i386 libid3-3.8.3c2a libidn11:i386
  libiec61883-0:i386 libjpeg-progs libk3b6 libkdecorations4abi1 libkdgantt2
  libkephal4abi1 libkexiv2-11 libkexiv2-data libkleo4 libkmanagesieve4 libkolabxml0
  libkpgp4 libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4 libkwineffects1abi4
  libkwinglutils1abi1 libkwinnvidiahack4 libkworkspace4abi2 libmad0:i386
  libmarblewidget14 libmediastreamer1 libmikmod2:i386 libmx-1.0-2 libmx-bin
  libmx-common libnspr4:i386 libnss3:i386 libodbc1:i386 libopenconnect2 libortp8
  libpathplan4 libpeas-common libplasma-geolocation-interface4 libplasmaclock4abi3
  libplasmagenericshell4 libpoppler-qt4-4 libprocesscore4abi1 libprocessui4a
  libproxy1:i386 libpulse-mainloop-glib0:i386 libpulsedsp:i386 libqalculate5
  libqalculate5-data libqapt-runtime libqapt1 libqimageblitz4 libqoauth1
  libqt4-designer:i386 libqt4-opengl:i386 libqt4-qt3support:i386 libqt4-svg:i386
  libqtwebkit4:i386 libraw1394-11:i386 librsvg2-2:i386 librsvg2-common:i386 librsync1
  librtmp0:i386 libsdl-image1.2:i386 libsdl-mixer1.2:i386 libsdl-net1.2:i386
  libsdl-ttf2.0-0:i386 libsdl1.2debian:i386 libshout3:i386 libsolidcontrol4abi2
  libsolidcontrolifaces4abi2 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386 libspeex1:i386
  libsrtp0 libssl0.9.8:i386 libstdc++5:i386 libsync-menu1 libtag1-vanilla:i386
  libtag1c2a:i386 libtaskmanager4abi3 libtdb1:i386 libunistring0:i386
  libvorbisfile3:i386 libwavpack1:i386 libweather-ion6 libwebp2:i386 libxaw7:i386
  libxerces-c3.1 libxine1 libxine1-bin libxine1-ffmpeg libxine1-misc-plugins libxine1-x
  libxmu6:i386 libxp6:i386 libxss1:i386 libxtst6:i386 libxv1:i386 marble-data
  marble-plugins mythes-de-ch odbcinst1debian2:i386 oxygen-cursor-theme
  plasma-containments-addons plasma-dataengines-addons plasma-scriptengine-javascript
  plasma-widget-folderview plasma-widget-message-indicator rhythmbox-data
  shared-desktop-ontologies software-center-aptdaemon-plugins xaw3dg:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python3-apport python3-problem-report
Suggested packages:
  python3-launchpadlib
The following packages will be upgraded:
  python3-apport python3-problem-report
2 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
60 not fully installed or removed.
Need to get 195 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal-updates/main python3-problem-report all 2.6.1-0ubuntu10 [9,444 B]
Get:2 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal-updates/main python3-apport all 2.6.1-0ubuntu10 [85.0 kB]
Get:3 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal/main xdiagnose all 3.2 [101 kB]
Fetched 195 kB in 0s (282 kB/s)
dpkg: warning: files list file for package 'popularity-contest' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcaca0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'hostname' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ghostscript-x' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-tlwg-typist' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'myspell-en-za' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libshout3:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdca0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ttf-farsiweb' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnl1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtag1-vanilla:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libntrack-qt4-1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libexempi3:amd64' missing; assuming package has no files currently installed
(Reading database ... 241138 files and directories currently installed.)
Preparing to replace python3-problem-report 2.6.1-0ubuntu9 (using .../python3-problem-report_2.6.1-0ubuntu10_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 24, in <module>
    import logging
  File "/usr/lib/python3.2/logging/__init__.py", line 27, in <module>
    from string import Template
  File "/usr/lib/python3.2/string.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/string.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, re, pwd, grp, os
  File "/usr/lib/python3.2/subprocess.py", line 381, in <module>
    import pickle
  File "/usr/lib/python3.2/pickle.py", line 37, in <module>
    import _compat_pickle
  File "/usr/lib/python3.2/_compat_pickle.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/_compat_pickle.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 24, in <module>
    import logging
  File "/usr/lib/python3.2/logging/__init__.py", line 27, in <module>
    from string import Template
  File "/usr/lib/python3.2/string.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/string.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 24, in <module>
    import logging
  File "/usr/lib/python3.2/logging/__init__.py", line 27, in <module>
    from string import Template
  File "/usr/lib/python3.2/string.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/string.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, re, pwd, grp, os
  File "/usr/lib/python3.2/subprocess.py", line 381, in <module>
    import pickle
  File "/usr/lib/python3.2/pickle.py", line 37, in <module>
    import _compat_pickle
  File "/usr/lib/python3.2/_compat_pickle.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/_compat_pickle.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 24, in <module>
    import logging
  File "/usr/lib/python3.2/logging/__init__.py", line 27, in <module>
    from string import Template
  File "/usr/lib/python3.2/string.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/string.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details
dpkg: error processing /var/cache/apt/archives/python3-problem-report_2.6.1-0ubuntu10_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 25, in <module>
    import logging
  File "/usr/lib/python3.2/logging/__init__.py", line 27, in <module>
    from string import Template
  File "/usr/lib/python3.2/string.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/string.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, re, pwd, grp, os
  File "/usr/lib/python3.2/subprocess.py", line 381, in <module>
    import pickle
  File "/usr/lib/python3.2/pickle.py", line 37, in <module>
    import _compat_pickle
  File "/usr/lib/python3.2/_compat_pickle.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/_compat_pickle.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 25, in <module>
    import logging
  File "/usr/lib/python3.2/logging/__init__.py", line 27, in <module>
    from string import Template
  File "/usr/lib/python3.2/string.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/string.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python3-apport 2.6.1-0ubuntu9 (using .../python3-apport_2.6.1-0ubuntu10_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 24, in <module>
    import logging
  File "/usr/lib/python3.2/logging/__init__.py", line 27, in <module>
    from string import Template
  File "/usr/lib/python3.2/string.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/string.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, re, pwd, grp, os
  File "/usr/lib/python3.2/subprocess.py", line 381, in <module>
    import pickle
  File "/usr/lib/python3.2/pickle.py", line 37, in <module>
    import _compat_pickle
  File "/usr/lib/python3.2/_compat_pickle.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/_compat_pickle.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 24, in <module>
    import logging
  File "/usr/lib/python3.2/logging/__init__.py", line 27, in <module>
    from string import Template
  File "/usr/lib/python3.2/string.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/string.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 24, in <module>
    import logging
  File "/usr/lib/python3.2/logging/__init__.py", line 27, in <module>
    from string import Template
  File "/usr/lib/python3.2/string.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/string.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, re, pwd, grp, os
  File "/usr/lib/python3.2/subprocess.py", line 381, in <module>
    import pickle
  File "/usr/lib/python3.2/pickle.py", line 37, in <module>
    import _compat_pickle
  File "/usr/lib/python3.2/_compat_pickle.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/_compat_pickle.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 24, in <module>
    import logging
  File "/usr/lib/python3.2/logging/__init__.py", line 27, in <module>
    from string import Template
  File "/usr/lib/python3.2/string.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/string.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details
dpkg: error processing /var/cache/apt/archives/python3-apport_2.6.1-0ubuntu10_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 25, in <module>
    import logging
  File "/usr/lib/python3.2/logging/__init__.py", line 27, in <module>
    from string import Template
  File "/usr/lib/python3.2/string.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/string.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, re, pwd, grp, os
  File "/usr/lib/python3.2/subprocess.py", line 381, in <module>
    import pickle
  File "/usr/lib/python3.2/pickle.py", line 37, in <module>
    import _compat_pickle
  File "/usr/lib/python3.2/_compat_pickle.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/_compat_pickle.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 25, in <module>
    import logging
  File "/usr/lib/python3.2/logging/__init__.py", line 27, in <module>
    from string import Template
  File "/usr/lib/python3.2/string.py", line 1
SyntaxError: Non-UTF-8 code starting with '\x8b' in file /usr/lib/python3.2/string.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python3-problem-report_2.6.1-0ubuntu10_all.deb
 /var/cache/apt/archives/python3-apport_2.6.1-0ubuntu10_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by tp21 on 2013-03-12
so i think the best would be now to make a fresh reinstalling of ubuntu.
i am running a macbook pro with double boot, osx and ubuntu. does anyone knows a good and easy way to reinstall ubutntu on his partition without a lot of hussels? do i need to wipe out the linux partition and start every thing from the beginning?
thanks

---

