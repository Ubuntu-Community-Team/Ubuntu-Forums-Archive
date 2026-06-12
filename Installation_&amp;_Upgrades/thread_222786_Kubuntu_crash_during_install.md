---
title: "Kubuntu crash during install"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by igeldard on 2006-07-25
Hi,

I'm trying to install Kubuntu 6.06 from a live disk. My machine is currently running WinXP+SP2 but there's about 40G free space on my drive.

The live CD works fine, but when I tried the install, I got the following error message when attempting to edit the partitions manually ...

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/kde-ui.py", line 311, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/kde-ui.py", line 731, in process_step
    self.gparted_to_mountpoints()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/kde-ui.py", line 804, in gparted_to_mountpoints
    print >>self.qtparted_subp.stdin, "apply"
AttributeError: 'NoneType' object has no attribute 'stdin'

Any ideas?

Ian

---

