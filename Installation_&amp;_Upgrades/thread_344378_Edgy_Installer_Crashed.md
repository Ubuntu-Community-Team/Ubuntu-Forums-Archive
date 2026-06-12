---
title: "Edgy Installer Crashed"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by geovino on 2007-01-22
I tried again and for the second time the Edgy installer crashed at 78% 
Here's the info:


We're sorry; the installer crashed. Please file a new bug report at [https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug) (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/syslog and /var/log/partman:

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
  File "/usr/share/ubiquity/install.py", line 306, in run
    self.copy_all ()
  File "/usr/share/ubiquity/install.py", line 484, in copy_all
    shutil.copyfile(sourcepath, targetpath)
  File "shutil.py", line 49, in copyfile
    copyfileobj(fsrc, fdst)
  File " shutil.py", line 25, in copyfileobj
    fdst.write(buf)
IOError: [Errno 28] No space left on device

What causes this? I'm filing a bug report because it does nothing. I'm not signed up with launchpad.

Please pass this on to people or a moderator who care about this!

Thank you.

---

### Post by avkhatri on 2007-01-22
Try Re Downloading the CD, that might work.

---

### Post by geovino on 2007-01-22
After three times... it's not worth it anymore. 

There are better Linux distros out there.

---

### Post by geovino on 2007-01-24
I'll try Feisty when it comes out in April.

---

