---
title: "Trouble installing Update Manager Core"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by wandman on 2013-05-04
Whilst trying to upgrade Ubuntu following the terminal commands at this tutorial: [http://www.liberiangeek.net/2010/04/how-to-upgrade-ubuntu-via-the-console-or-terminal/](http://www.liberiangeek.net/2010/04/how-to-upgrade-ubuntu-via-the-console-or-terminal/)

 I got stuck after the first command and get the following error...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
22 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python3-dbus (1.1.1-1ubuntu0.1) ...
Could not import runpy module
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 289, in <module>
    main()
  File "/usr/bin/py3compile", line 283, in main
    process.communicate()
  File "/usr/lib/python3.2/subprocess.py", line 809, in communicate
    self.stdin.close()
IOError: [Errno 32] Broken pipe
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, re, pwd, grp, os
EOFError: EOF read where not expected

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 289, in <module>
    main()
  File "/usr/bin/py3compile", line 283, in main
    process.communicate()
  File "/usr/lib/python3.2/subprocess.py", line 809, in communicate
    self.stdin.close()
IOError: [Errno 32] Broken pipe
dpkg: error processing python3-dbus (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python3-gi (3.4.0-1ubuntu0.1) ...
Could not import runpy module
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 289, in <module>
    main()
  File "/usr/bin/py3compile", line 283, in main
    process.communicate()
  File "/usr/lib/python3.2/subprocess.py", line 809, in communicate
    self.stdin.close()
IOError: [Errno 32] Broken pipe
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, re, pwd, grp, os
EOFError: EOF read where not expected

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 289, in <module>
    main()
  File "/usr/bin/py3compile", line 283, in main
    process.communicate()
  File "/usr/lib/python3.2/subprocess.py", line 809, in communicate
    self.stdin.close()
IOError: [Errno 32] Broken pipe
dpkg: error processing python3-gi (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ufw (0.33-0ubuntu2.1) ...
Could not import runpy module
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 289, in <module>
    main()
  File "/usr/bin/py3compile", line 283, in main
    process.communicate()
  File "/usr/lib/python3.2/subprocess.py", line 809, in communicate
    self.stdin.close()
IOError: [Errno 32] Broken pipe
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, re, pwd, grp, os
EOFError: EOF read where not expected

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 289, in <module>
    main()
  File "/usr/bin/py3compile", line 283, in main
    process.communicate()
  File "/usr/lib/python3.2/subprocess.py", line 809, in communicate
    self.stdin.close()
IOError: [Errno 32] Broken pipe
dpkg: error processing ufw (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python3-problem-report (2.6.1-0ubuntu10) ...
No apport report written because MaxReports has already been reached
                                                                    Could not import runpy module
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 289, in <module>
    main()
  File "/usr/bin/py3compile", line 283, in main
    process.communicate()
  File "/usr/lib/python3.2/subprocess.py", line 809, in communicate
    self.stdin.close()
IOError: [Errno 32] Broken pipe
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, re, pwd, grp, os
EOFError: EOF read where not expected

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 289, in <module>
    main()
  File "/usr/bin/py3compile", line 283, in main
    process.communicate()
  File "/usr/lib/python3.2/subprocess.py", line 809, in communicate
    self.stdin.close()
IOError: [Errno 32] Broken pipe
dpkg: error processing python3-problem-report (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-apport:
 python3-apport depends on python3-problem-report (>= 0.94); however:
  Package python3-problem-report is not configured yet.

dpkg: error processing python3-apport (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of apport:
 apport depends on python3-apport (>= 2.6.1-0ubuntu10); however:
  Package python3-apport is not configured yet.
 apport depends on python3-gi; however:
  Package python3-gi is not configured yet.

dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python3-apport (>= 2.6.1-0ubuntu10); however:
  Package python3-apport is not configured yet.
 apport-gtk depends on python3-gi; however:
  Package python3-gi is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gnome-orca:
 gnome-orca depends on python3-gi (>= 3.0.2); however:
  Package python3-gi is not configured yet.

dpkg: error processing gnome-orca (--configure):
 dependency problems - leaving unconfigured
Setting up python3-xdg (0.20-0ubuntu1) ...
No apport report written because MaxReports has already been reached
                                                                    Could not import runpy module
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 289, in <module>
    main()
  File "/usr/bin/py3compile", line 283, in main
    process.communicate()
  File "/usr/lib/python3.2/subprocess.py", line 809, in communicate
    self.stdin.close()
IOError: [Errno 32] Broken pipe
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, re, pwd, grp, os
EOFError: EOF read where not expected

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 289, in <module>
    main()
  File "/usr/bin/py3compile", line 283, in main
    process.communicate()
  File "/usr/lib/python3.2/subprocess.py", line 809, in communicate
    self.stdin.close()
IOError: [Errno 32] Broken pipe
dpkg: error processing python3-xdg (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of indicator-applet:
 indicator-applet depends on python3-xdg; however:
  Package python3-xdg is not configured yet.

dpkg: error processing indicator-applet (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-aptdaemon:
 python3-aptdaemon depends on python3-dbus; however:
  Package python3-dbus is not configured yet.
 python3-aptdaemon depends on python3-gi; however:
  Package python3-gi is not configured yet.

dpkg: error processing python3-aptdaemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-aptdaemon.gtk3widgets:
 python3-aptdaemon.gtk3widgets depends on python3-aptdaemon (= 0.45+bzr861-0ubuntu9.1.2); however:
  Package python3-aptdaemon is not configured yet.
 python3-aptdaemon.gtk3widgets depends on python3-gi; however:
  Package python3-gi is not configured yet.

dpkg: error processing python3-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python3-dbus; however:No apport report written because MaxReports has already been reached

  Package python3-dbus is not configured yet.
 update-manager depends on python3-gi; however:
  Package python3-gi is not configured yet.

dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
 ubuntu-release-upgrader-gtk depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-release-upgrader-gtk depends on python3-dbus; however:
  Package python3-dbus is not configured yet.
 ubuntu-release-upgrader-gtk depends on python3-gi; however:
  Package python3-gi is not configured yet.

dpkg: error processing ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Setting up unity-lens-photos (0.9-0ubuntu1) ...
Could not import runpy module
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 289, in <module>
    main()
  File "/usr/bin/py3compile", line 283, in main
    process.communicate()
  File "/usr/lib/python3.2/subprocess.py", line 809, in communicate
    self.stdin.close()
IOError: [Errno 32] Broken pipe
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, re, pwd, grp, os
EOFError: EOF read where not expected

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 289, in <module>
    main()
  File "/usr/bin/py3compile", line 283, in main
    process.communicate()
  File "/usr/lib/python3.2/subprocess.py", line 809, in communicate
    self.stdin.close()
IOError: [Errno 32] Broken pipe
dpkg: error processing unity-lens-photos (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of xdiagnose:
 xdiagnose depends on python3-gi (>= 3.2.0-3); however:
  Package python3-gi is not configured yet.
 xdiagnose depends on python3-apport; however:
  Package python3-apport is not configured yet.

dpkg: error processing xdiagnose (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on python3-aptdaemon (= 0.45+bzr861-0ubuntu9.1.2); however:
  Package python3-aptdaemon is not configured yet.
 aptdaemon depends on python3-gi; however:
  Package python3-gi is not configured yet.

No apport report written because MaxReports has already been reached
                                                                    dpkg: error processing aptdaemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-aptdaemon.pkcompat:
 python3-aptdaemon.pkcompat depends on python3-aptdaemon (= 0.45+bzr861-0ubuntu9.1.2); however:
  Package python3-aptdaemon is not configured yet.

dpkg: error processing python3-aptdaemon.pkcompat (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Setting up python3-distupgrade (1:0.190.6) ...
Could not import runpy module
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 289, in <module>
    main()
  File "/usr/bin/py3compile", line 283, in main
    process.communicate()
  File "/usr/lib/python3.2/subprocess.py", line 809, in communicate
    self.stdin.close()
IOError: [Errno 32] Broken pipe
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, re, pwd, grp, os
EOFError: EOF read where not expected

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 289, in <module>
    main()
  File "/usr/bin/py3compile", line 283, in main
    process.communicate()
  File "/usr/lib/python3.2/subprocess.py", line 809, in communicate
    self.stdin.close()
IOError: [Errno 32] Broken pipe
dpkg: error processing python3-distupgrade (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3-distupgrade; however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing python3-update-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3-distupgrade (= 1:0.190.6); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python3-update-manager (= 1:0.174.4); however:
  Package python3-update-manager is not configured yet.
 update-manager-core depends on ubuntu-release-upgrader-core; however:
  Package ubuntu-release-upgrader-core is not configured yet.

dpkg: error processing update-manager-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 python3-dbus
 python3-gi
 ufw
 python3-problem-report
 python3-apport
 apport
 apport-gtk
 gnome-orca
 python3-xdg
 indicator-applet
 python3-aptdaemon
 python3-aptdaemon.gtk3widgets
 update-manager
 ubuntu-release-upgrader-gtk
 unity-lens-photos
 xdiagnose
 aptdaemon
 python3-aptdaemon.pkcompat
 python3-distupgrade
 python3-update-manager
 ubuntu-release-upgrader-core
 update-manager-core
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any help would be much appreciated.

---

### Post by gordintoronto on 2013-05-05
First get your system completely up to date and error-free.

You are upgrading from what version to what version?

---

### Post by wandman on 2013-05-06
I'm trying to go from 12.10 to 13.04

I think I am up to date (I've installed all updates) as for error free... that is another story. One thing at a time though?

---

