---
title: "[Maverick 10.10] Weird PyCentral (?) Bug After Upgrade - Dependency issue?"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by teamcoltra on 2010-10-25
I have seen other threads for this, but either they don't answer the question and the asker has given up... OR the solutions provided do not solve for my problem (and are dated). 

[http://paste2.org/p/1053150](http://paste2.org/p/1053150)

Here is the output that I get anytime I install something. It installs fine, but if I use a graphical client (synaptic / USC) it will tell me that the "install failed" although the application installed fine, because of the errors that get output.

This would just be an annoyance to me if it didn't involve telepathy-butterfly, which is the MSN connection thing for empathy. I kinda like my MSN friends :) 

This has happened ever since my upgrade to 10.10.

I have already purged each program, and reinstalled it... no luck. I also reinstalled python, and python-support.  I tried to rebuild all broken packages, but synaptic and apt-get don't see the packages as "broken", nor does it see them having dependency issues. 

Here is a slightly more difficult-to-read version, but hopefully it will help people with the issue find this thread and the answer that it will hopefully get soon. :)

```
teamcoltra@paradoxicon:~$ sudo apt-get install python-encutils python-cssutils telepathy-butterfly calibre python-speechd gnome-codec-install python-configglue ubuntuone-client libsyncdaemon-1.0-1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtest-exception-perl python-packagekit libpackagekit-qt-14 libktnef4 libavutil49 libkxmlrpcclient4 nspluginwrapper libkholidays4 kpackagekit
  libmodplug0c2 libftgl2 packagekit-backend-aptcc libboost-program-options1.40.0 kdelibs5 librpmio0 librpm0 libmagick++2 libdvbpsi5 libsyndication4
  kdesudo libalut0 libx264-85 libqgpgme1 virtuoso-nepomuk libhiglayout-java libsub-uplevel-perl libdebconf-kde0 libmatroska0 software-properties-kde
  libao2 zlib1g-dev libcv4 libkblog4 librpmbuild0 libqtassistantclient4 install-package packagekit libqt4-assistant gdebi-kde libkimproxy4 kdepimlibs5
  libkpimtextedit4 libhighgui4 update-manager-kde blender libpackagekit-glib2-14 libqt4-webkit libtorrent-rasterbar5 libkpimidentities4 libsox1a
  libopenjpeg2 libkde3support4 libebml0 libmpcdec3 libgpgme++2 packagekit-backend-apt
Use 'apt-get autoremove' to remove them.
Suggested packages:
  ubuntuone-client-dbg
The following NEW packages will be installed:
  calibre gnome-codec-install libsyncdaemon-1.0-1 python-configglue python-cssutils python-encutils python-speechd telepathy-butterfly ubuntuone-client
0 upgraded, 9 newly installed, 0 to remove and 63 not upgraded.
Need to get 7,913kB/8,086kB of archives.
After this operation, 29.8MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/universe python-encutils all 0.9.7~b2-2 [47.7kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick/universe python-cssutils all 0.9.7~b2-2 [139kB]                                                        
Get:3 http://us.archive.ubuntu.com/ubuntu/ maverick/main telepathy-butterfly all 0.5.14-1 [53.1kB]                                                         
Get:4 http://us.archive.ubuntu.com/ubuntu/ maverick/universe calibre all 0.7.18+dfsg-1 [7,673kB]                                                           
Fetched 7,913kB in 60s (130kB/s)                                                                                                                           
Selecting previously deselected package gnome-codec-install.
(Reading database ... 300220 files and directories currently installed.)
Unpacking gnome-codec-install (from .../gnome-codec-install_0.4.7ubuntu2_all.deb) ...
Selecting previously deselected package python-configglue.
Unpacking python-configglue (from .../python-configglue_0.9pre1-0ubuntu1_all.deb) ...
Selecting previously deselected package ubuntuone-client.
Unpacking ubuntuone-client (from .../ubuntuone-client_1.4.4.1-0ubuntu1_all.deb) ...
Selecting previously deselected package libsyncdaemon-1.0-1.
Unpacking libsyncdaemon-1.0-1 (from .../libsyncdaemon-1.0-1_1.4.4.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-encutils.
Unpacking python-encutils (from .../python-encutils_0.9.7~b2-2_all.deb) ...
Selecting previously deselected package python-cssutils.
Unpacking python-cssutils (from .../python-cssutils_0.9.7~b2-2_all.deb) ...
Selecting previously deselected package telepathy-butterfly.
Unpacking telepathy-butterfly (from .../telepathy-butterfly_0.5.14-1_all.deb) ...
Selecting previously deselected package calibre.
Unpacking calibre (from .../calibre_0.7.18+dfsg-1_all.deb) ...
Selecting previously deselected package python-speechd.
Unpacking python-speechd (from .../python-speechd_0.7-5ubuntu3_all.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up gnome-codec-install (0.4.7ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2304, in <module>
    main()
  File "/usr/bin/pycentral", line 2298, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1501, in run
    self.options.exclude, byte_compile_default=True)
  File "/usr/bin/pycentral", line 1085, in install
    rt.byte_compile(linked_files, bc_option, exclude_regex, ignore_errors)
  File "/usr/bin/pycentral", line 231, in byte_compile
    shell=False, stdin=subprocess.PIPE)
  File "/usr/lib/python2.6/subprocess.py", line 623, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1141, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
dpkg: error processing gnome-codec-install (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-configglue (0.9pre1-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2304, in <module>
    main()
  File "/usr/bin/pycentral", line 2298, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1501, in run
    self.options.exclude, byte_compile_default=True)
  File "/usr/bin/pycentral", line 1085, in install
    rt.byte_compile(linked_files, bc_option, exclude_regex, ignore_errors)
  File "/usr/bin/pycentral", line 231, in byte_compile
    shell=False, stdin=subprocess.PIPE)
  File "/usr/lib/python2.6/subprocess.py", line 623, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1141, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
dpkg: error processing python-configglue (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on python-configglue; however:
  Package python-configglue is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsyncdaemon-1.0-1:
 libsyncdaemon-1.0-1 depends on ubuntuone-client (>= 1.4.4.1-0ubuntu1); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing libsyncdaemon-1.0-1 (--configure):
 dependency problems - leaving unconfigured
Setting up python-encutils (0.9.7~b2-2) ...
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2304, in <module>
    main()
  File "/usr/bin/pycentral", line 2298, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1501, in run
    self.options.exclude, byte_compile_default=True)
  File "/usr/bin/pycentral", line 1085, in install
    rt.byte_compile(linked_files, bc_option, exclude_regex, ignore_errors)
  File "/usr/bin/pycentral", line 231, in byte_compile
    shell=False, stdin=subprocess.PIPE)
  File "/usr/lib/python2.6/subprocess.py", line 623, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1141, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
dpkg: error processing python-encutils (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-cssutils:
 python-cssutils depends on python-encutils; however:
  Package python-encutils is not configured yet.
dpkg: error processing python-cssutils (--configure):
 dependency problems - leaving unconfigured
Setting up telepathy-butterfly (0.5.14-1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2304, in <module>
    main()
  File "/usr/bin/pycentral", line 2298, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1501, in run
    self.options.exclude, byte_compile_default=True)
  File "/usr/bin/pycentral", line 1085, in install
    rt.byte_compile(linked_files, bc_option, exclude_regex, ignore_errors)
  File "/usr/bin/pycentral", line 231, in byte_compile
    shell=False, stdin=subprocess.PIPE)
  File "/usr/lib/python2.6/subprocess.py", line 623, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1141, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
dpkg: error processing telepathy-butterfly (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of calibre:
 calibre depends on python-cssutils (>= 0.9.7~); however:
  Package python-cssutils is not configured yet.
 calibre depends on python-encutils (>= 0.9.5); however:
  Package python-encutils is not configured yet.
dpkg: error processing calibre (--configure):
 dependency problems - leaving unconfigured
Setting up python-speechd (0.7-5ubuntu3) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2304, in <module>
    main()
  File "/usr/bin/pycentral", line 2298, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1501, in run
    self.options.exclude, byte_compile_default=True)
  File "/usr/bin/pycentral", line 1085, in install
    rt.byte_compile(linked_files, bc_option, exclude_regex, ignore_errors)
  File "/usr/bin/pycentral", line 231, in byte_compile
    shell=False, stdin=subprocess.PIPE)
  File "/usr/lib/python2.6/subprocess.py", line 623, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1141, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
dpkg: error processing python-speechd (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 gnome-codec-install
 python-configglue
 ubuntuone-client
 libsyncdaemon-1.0-1
 python-encutils
 python-cssutils
 telepathy-butterfly
 calibre
 python-speechd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by teamcoltra on 2010-11-08
I have tried removing python2.6 and python and reinstalling them -- no help.

---

