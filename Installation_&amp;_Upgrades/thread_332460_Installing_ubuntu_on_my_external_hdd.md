---
title: "Installing ubuntu on my external hdd"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by juwaidah1990 on 2007-01-06
I tried to install ubuntu on my external hdd but the installer crashed and I got this:

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
   self.copy_all()
 File "/usr/share/ubiquity/install.py", line 484, in copy_all
   shutil.copyfile(sourcepath, targetpath)
 File "shutil.py", line 49, in copyfile
   copyfileobj(fsrc, fdst)
 File "shutil.py", line 25, in copyfileobj
   fdst.write(buf)
IOError: [Errno 30] Read-only file system

What can I do? I really want ubuntu...

---

### Post by confused57 on 2007-01-07
Here's a howto install on an external hd:
[http://www.ubuntuforums.org/showthread.php?t=80811&highlight=external](http://www.ubuntuforums.org/showthread.php?t=80811&highlight=external)

You'll need the alternate cd(Dapper or Edgy) to be able to use this howto.

---

