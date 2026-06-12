---
title: "Gutsy installation on acer laptop"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by ewlabonte on 2008-02-01
I'm trying to install gutsy on my acer aspire 5100 laptop. Even though the computer is 64 bit I'm using the x86 version because I don't want problems getting flash to work, etc. The live cd boots up great and for the first time I can get wireless working with the live cd. I think 2.6.22 includes the rt61 driver. I have blag linux installed on /dev/sda1, a home directory on /dev/sda2, swap on /dev/sda3 and I'm trying to install gutsy on /dev/sda4. The installation process proceeds fine until about 90% of the installation is complete. Then it stops, no error message or anything. Grub is not installed (no grub directory in the /boot directory) so, of course, it won't boot. It seems to be a problem with ubiquity because I get the following message from /var/log/installer/debug:

```
Ubiquity 1.6.8
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 212, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 207, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 65, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 425, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 776, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1768, in <module>
    install.run()
  File "/usr/share/ubiquity/install.py", line 388, in run
    self.configure_ma()
  File "/usr/share/ubiquity/install.py", line 1008, in configure_ma
    raise InstallStepError("MigrationAssistantApply failed with code %d" % ret)
InstallStepError: MigrationAssistantApply failed with code 2



Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 212, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 207, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 65, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 425, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 776, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1768, in <module>
    install.run()
  File "/usr/share/ubiquity/install.py", line 388, in run
    self.configure_ma()
  File "/usr/share/ubiquity/install.py", line 1008, in configure_ma
    raise InstallStepError("MigrationAssistantApply failed with code %d" % ret)
InstallStepError: MigrationAssistantApply failed with code 2


Ubiquity 1.6.8
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1122, in watch_debconf_fd_helper
    return callback(source, debconf_condition)
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 179, in process_input
    if not self.process_line():
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 112, in process_line
    return self.dbfilter.process_line()
  File "/usr/lib/ubiquity/ubiquity/debconffilter.py", line 363, in process_line
    self.reply(0, data)
  File "/usr/lib/ubiquity/ubiquity/debconffilter.py", line 139, in reply
    self.subin.write('%s\n' % ret)
IOError: [Errno 32] Broken pipe

Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1122, in watch_debconf_fd_helper
    return callback(source, debconf_condition)
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 179, in process_input
    if not self.process_line():
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 112, in process_line
    return self.dbfilter.process_line()
  File "/usr/lib/ubiquity/ubiquity/debconffilter.py", line 363, in process_line
    self.reply(0, data)
  File "/usr/lib/ubiquity/ubiquity/debconffilter.py", line 139, in reply
    self.subin.write('%s\n' % ret)
IOError: [Errno 32] Broken pipe
```


I'm downloading the alternate install cd, but this is a new laptop. It kind of sucks that the live cd install doesn't work :-(

---

