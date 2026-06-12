---
title: "Grub Install issue?"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by crevan on 2007-02-01
> We're sorry; the installer crashed. Please file a new bug report at [https://launchpad.net/distros/ubuntu...quity/+filebug](https://launchpad.net/distros/ubuntu...quity/+filebug) (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/syslog and /var/log/partman:

Traceback (most recent call last):
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
InstallStepError: GrubInstaller failed with code 1

I keep getting this error when I attempt to install Ubuntu. I **THINK** I have the problem figured out after having read a few threads around here.

Ive a few HDDs with partitions on them, such that its listed as hda1 et cetera. Ive always given the instruction to install to hda1 rather than the default hd0, which when I have allowed it to do so has given me Error: 17 (if the formatting is correct for the error code. I remember being 17.) 

Installing to hda1 gives me a fatal error. The one quoted above. As does, if I remember correctly, hda. Please, correct me if I'm wrong, but would using hd1 fix this? Or if not, how would I go about fixing the problem?

---

