---
title: "Ubiquity Installer Hangs at &quot;Where are you?&quot; (Time zone)"
date: 2014-12-07
forum: Installation &amp; Upgrades
---

### Post by xmbwd on 2014-12-07
I created a Live system .iso using Systemback, put it on a USB, and I'd like to install it on a separate partition.  I am trying to use the Ubiquity installer ("Install Release") to install the system once it is booted via the USB.  

Every time I do so, the installer hangs at the "Where are you?" page.  More specifically, it lets me select my location and the "Continue" button is made available.  But after clicking the "Continue" button, the little wheel spins for a while -- and stops.  At that point, the "Continue" button is no longer available, i.e., greyed out, and I can switch the location again -- but the installer is dead.  Below is the /var/log/syslog.

Does anyone know what is wrong here?  I have also tried to install using Systemback's internal installer, but the partition does not show up as available after the install (which does not hang).


```
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]: debconffilter_done: ubi-timezone (current: ubi-timezone)
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]: Step_before = stepLocation
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]: Exception in GTK frontend (invoking crash handler):
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]: Traceback (most recent call last):
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 778, in <lambda>
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]:     lambda: self.dbfilter.start(auto_process=True))
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]:   File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 103, in start
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]:     prep = self.prepare()
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]:   File "/usr/lib/ubiquity/plugins/ubi-console-setup.py", line 429, in prepare
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]:     self.db.fset('keyboard-configuration/layout', 'seen', 'false')
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]:   File "/usr/lib/python3/dist-packages/debconf.py", line 62, in <lambda>
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]:     lambda *args, **kw: self.command(command, *args, **kw))
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]:   File "/usr/lib/python3/dist-packages/debconf.py", line 98, in command
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]:     raise DebconfError(status, data)
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]: debconf.DebconfError: (10, "keyboard-configuration/layout doesn't exist")
Dec  7 12:30:45 mbwd-Q501LA ubiquity[10073]: 
Dec  7 12:31:50 mbwd-Q501LA /install.py: Exception during installation:
Dec  7 12:31:50 mbwd-Q501LA /install.py: Traceback (most recent call last):
Dec  7 12:31:50 mbwd-Q501LA /install.py:   File "/usr/share/ubiquity/install.py", line 749, in <module>
Dec  7 12:31:50 mbwd-Q501LA /install.py:     install.run()
Dec  7 12:31:50 mbwd-Q501LA /install.py:   File "/usr/share/ubiquity/install.py", line 135, in run
Dec  7 12:31:50 mbwd-Q501LA /install.py:     self.copy_all()
Dec  7 12:31:50 mbwd-Q501LA /install.py:   File "/usr/share/ubiquity/install.py", line 498, in copy_all
Dec  7 12:31:50 mbwd-Q501LA /install.py:     self.db.progress('SET', 10 + copy_progress)
Dec  7 12:31:50 mbwd-Q501LA /install.py:   File "/usr/lib/python3/dist-packages/debconf.py", line 62, in <lambda>
Dec  7 12:31:50 mbwd-Q501LA /install.py:     lambda *args, **kw: self.command(command, *args, **kw))
Dec  7 12:31:50 mbwd-Q501LA /install.py:   File "/usr/lib/python3/dist-packages/debconf.py", line 67, in command
Dec  7 12:31:50 mbwd-Q501LA /install.py:     self.write.flush()
Dec  7 12:31:50 mbwd-Q501LA /install.py: BrokenPipeError: [Errno 32] Broken pipe
```

---

