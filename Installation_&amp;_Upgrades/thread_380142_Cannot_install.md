---
title: "Cannot install"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by IceVapour on 2007-03-09
Hi all,

After finally getting Edgy to recognise my Ethernet connection, I have decided to move to Ubuntu, installing it on a new 500gb external HD.  

After MANY attempts to get it to install, it all seemed to be working, but at the end of the install, I got the following message:

*We're sorry; the installer crashed. Please file a new bug report at [https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug) (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/syslog and /var/log/partman:*


[I]Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 166, in ?
    main()
  File "/usr/bin/ubiquity", line 161, in main
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 57, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 305, in run
    self.process_step()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 856, in process_step
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 628, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s\n%s" %
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1404, in ?
    install.run()
  File "/usr/share/ubiquity/install.py", line 385, in run
    self.configure_bootloader()
  File "/usr/share/ubiquity/install.py", line 1163, in configure_bootloader
    raise InstallStepError(
InstallStepError: GrubInstaller failed with code 1[/I]

Can anyone help me with this?  I would love to use Ubuntu rather than XP (everything just works in Ubuntu!) but I cannot seem to make it happen.  

Any help would be hugely appriciated.

---

### Post by Kateikyoushi on 2007-03-09
Seems to me you ran into this bug. [LINK]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/71627")

Browsing through it the only advice I found was to go for the alternate install CD that worked for someone.

---

