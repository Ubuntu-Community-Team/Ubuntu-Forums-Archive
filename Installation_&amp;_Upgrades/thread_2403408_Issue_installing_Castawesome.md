---
title: "Issue installing Castawesome"
date: 2018-10-11
forum: Installation &amp; Upgrades
---

### Post by toyson on 2018-10-11
Hello, i recently installed castawesome video broadcaster on my Xubuntu 16.04, but it gives an error (attached below) when i run it through terminal after which the application crashes.
Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GLib
Traceback (most recent call last):
  File "/usr/local/bin/castawesome", line 1172, in <module>
    sys.exit(main())
  File "/usr/local/bin/castawesome", line 1166, in main
    GUI()
  File "/usr/local/bin/castawesome", line 102, in __init__
    self.initialize_values()
  File "/usr/local/bin/castawesome", line 195, in initialize_values
    advanced_options = get_advanced_options()
  File "/usr/local/bin/castawesome", line 855, in get_advanced_options
    for line in subprocess.check_output(["avconv", "-formats"]).splitlines():
  File "/usr/lib/python3.5/subprocess.py", line 626, in check_output
    **kwargs).stdout
  File "/usr/lib/python3.5/subprocess.py", line 693, in run
    with Popen(*popenargs, **kwargs) as process:
  File "/usr/lib/python3.5/subprocess.py", line 947, in __init__
    restore_signals, start_new_session)
  File "/usr/lib/python3.5/subprocess.py", line 1551, in _execute_child
    raise child_exception_type(errno_num, err_msg)
FileNotFoundError: [Errno 2] No such file or directory: 'avconv'

---

