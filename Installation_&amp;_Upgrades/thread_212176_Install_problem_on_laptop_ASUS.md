---
title: "Install problem on laptop ASUS"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by lubosm on 2006-07-09
I am trying to install on laptop ASUS A6U series and :

We're sorry; the installer crashed. Please file a bug report at
[https://launchpad.net/distros/ubuntu/+s](https://launchpad.net/distros/ubuntu/+s) … y/+filebug and a developer will
attend to the problem as soon as possible. To help the developers understand what went
wrong, include the following detail in your bug report, and attach the files
/var/log/installer/syslog, /var/log/syslog, and /var/log/partman:

Traceback (most recent call last):
File "/usr/bin/ubiquity", line 130, in ?
   install(sys.argv[1])
File "/usr/bin/ubiquity", line 55, in install
   ret = wizard.run()
File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
   self.process_step()
File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 741, in
process_step
   self.mountpoints_to_summary()
File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1029, in
mountpoints_to_summary
   self.progress_loop()
File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in
progress_loop
   raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and
/var/log/syslog


Any ideas to help me ?

---

