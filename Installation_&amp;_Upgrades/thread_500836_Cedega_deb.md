---
title: "Cedega deb"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by sent17inel on 2007-07-14
I have a cedega deb file that keeps installing itself as root. I would like it to be in my "daniel" account so i wont have to always go to terminal and type sudo cedega to open it. Any ideas on how to do this?

---

### Post by sent17inel on 2007-07-14
This is what im gettting when i try to run cedega not as root. 


daniel@daniel-desktop:~$ cedega
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2751, in <module>
    Point2Play_gui_ref = Point2Play_gui( Point2Play.Point2Play( config_file) )
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 459, in __init__
    self.setup_pthread_checking()
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 826, in setup_pthread_checking
    self.Point2Play.write()
  File "/usr/lib/transgaming_cedega/Point2Play.py", line 1835, in write
    fp = file( filename, "w+" ) # Overwrite
IOError: [Errno 13] Permission denied: '/home/daniel/.cedegarc'
daniel@daniel-desktop:~$

---

