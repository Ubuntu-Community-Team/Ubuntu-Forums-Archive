---
title: "Installation problem in 6.06"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by mutantbc on 2006-12-06
im attaching the error logs:


But now i have successfully installed ubuntu on my PC. :) just wanted to attached the error incase anyone have the same problem. Its a strange problem, it just hangs after 40% in progress:confused:. What I did, just restart the PC even though my harddisk will die when I do this while the installation is in progress :). Did a re-installing, but this time i lowered the resolution to 1024x480 32bit (before it was 1280xsomething).

---

### Post by aysiu on 2006-12-07
Well, the error says to file a bug report. Did you file one? ```
We're sorry; the installer crashed. Please file a bug report at https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/installer/syslog, /var/log/syslog, and /var/log/partman:


Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 264, in run
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 534, in progress_loop
    ret = dbfilter.run_command(auto_process=True)
  File "/usr/lib/python2.4/site-packages/ubiquity/filteredcommand.py", line 128, in run_command
    self.start(auto_process=auto_process)
  File "/usr/lib/python2.4/site-packages/ubiquity/filteredcommand.py", line 46, in start
    prep = self.prepare()
  File "/usr/lib/python2.4/site-packages/ubiquity/components/install.py", line 26, in prepare
    self.preseed('netcfg/get_hostname', hostname)
  File "/usr/lib/python2.4/site-packages/ubiquity/filteredcommand.py", line 246, in preseed
    self.db.register('debian-installer/dummy', name)
  File "/usr/lib/python2.4/site-packages/debconf.py", line 60, in <lambda>
    lambda *args, **kw: self.command(command, *args, **kw))
  File "/usr/lib/python2.4/site-packages/debconf.py", line 81, in command
    status = int(status)
ValueError: invalid literal for int(): 
```

---

