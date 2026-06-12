---
title: "Instilation Problem"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by Phntm Black Ice on 2007-02-28
I downloaded the Xubuntu Live CD, checked the md5sum, burned to disk, inserted disk and restarted computer.  Started up the Live CD and started to install Xubuntu.  I partitioned existing hard drive so can keep winxp.  hda1 = winxp    hda2(1gb) = swap     hda3(36gb) = / (root).  It partitions fine I come to instillation part.  When get to last step before instillation I change install of grub from hda0 to hda3.  It gets to 94% installation when  I get the following errors.  Little pop up window gives me the following error:

Executing "grub-install"(hda3) failed.  This is a fatal error.


Then the following pops up:

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

RuntimeError: Install failed with exit code 1 Traceback (most recent call last):

  File "/usr/share/ubiquity/install.py", line 1404, in ?
    install.run()
  File "/usr/share/ubiquity/install.py", line 385, in run
    self.configure_bootloader()
  File "/usr/share/ubiquity/install.py", line 1163, in configure_bootloader
    raise InstallStepError(

InstallStepError: GrubInstaller failed with code 1

---

### Post by vividvew on 2007-02-28
I am not an experienced Ubuntu user but typicaly grub would execute grub-install (hda) not grub-install (hda3). The GUI shows you a few steps before here it will install grub. Not sure but I'm guessing this is related to your problem.

---

### Post by Phntm Black Ice on 2007-02-28
Huh ???  I am a newb with Linux.  Could you explain better, please.

---

