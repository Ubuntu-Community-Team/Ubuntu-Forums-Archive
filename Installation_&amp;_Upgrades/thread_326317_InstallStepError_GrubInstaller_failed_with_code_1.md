---
title: "InstallStepError: GrubInstaller failed with code 1"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by boozker on 2006-12-27
I was installing ubuntu and i was so close. At 95% to be exact then this came up:

```
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

```

Can someone help. I was trying to install 6.10 and i Partitioned my drive as followed:

"/" = 3 GiB ext3
"/home" = 7.99 GiB ext3
swap = 400 MiB


It seemed to install all of the componets fine until that. I think its a problem with my laptop set up. As you all know there is no installer for an Intel Mac. There is however, installers for PCs, which work fine. Do you think it couldnt install it because it wasnt a .dmg?

---

