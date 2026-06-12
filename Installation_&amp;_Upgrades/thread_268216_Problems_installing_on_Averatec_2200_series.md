---
title: "Problems installing on Averatec 2200 series"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by kernco on 2006-09-29
I'm trying to install Ubuntu on an Averatec 2260 laptop.  It has an AMD 64-bit processor, but I was having trouble with the 64-bit live CD, so I am installing with the 32-bit version.  The installer crashes when it tries to setup the boot loader with this error:
Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 741, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1029, in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and /var/log/syslog

Any ideas on what is wrong?  What other information do you need?

Thanks,
Colin Kern

---

### Post by K.Mandla on 2006-09-30
I suppose you could list the contents of /var/log/installer/syslog, but I'm guessing that would be more work than it's worth.

Any chance it's a faulty CD? And if you want to try the 64-bit version, go with the alternate (installation) CD, instead of the live/desktop one. It's generally acknowledged that the live CD's installer isn't 100 percent reliable.

---

