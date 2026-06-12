---
title: "Gutsy Installation Crashed When &quot;Scanning Security Updates Repository&quot;"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by edwin11 on 2007-10-31
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]Hi all,

i was doing a fresh install of 32-bit Gutsy when i hit the following problem. Basically, it would be stuck for more than an hour at the stage "Scanning Security Updates Repository", and then the following crash message appears:

```
We're sorry; the installer crashed. Please file a new bug report at https://launchpad.net/ubuntu/+source/ubiquity/+filebug (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/syslog and /var/log/partman:

Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 212, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 207, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 65, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 425, in run
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 776, in progress_loop
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1768, in <module>
    install.run()
  File "/usr/share/ubiquity/install.py", line 361, in run
    self.configure_apt()
  File "/usr/share/ubiquity/install.py", line 868, in configure_apt
    raise InstallStepError("AptSetup failed with code %d" % ret)
InstallStepError: AptSetup failed with code 2
```

i know i'm supposed to file a bug report, but just wondering if anyone else has encountered this, or if it's something i did wrongly, and how i can get around it?



Thanks in Advance,
Edwin[/COLOR][/SIZE][/FONT]

---

