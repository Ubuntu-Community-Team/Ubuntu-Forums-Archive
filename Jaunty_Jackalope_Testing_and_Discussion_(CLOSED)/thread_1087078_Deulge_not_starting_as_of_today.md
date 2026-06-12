---
title: "Deulge not starting as of today?"
date: 2009-03-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-03-04
Did the big python update yesterday and now I can't start deluge! Shock! Horror!

First I get a swap sha for hashlib deprecation error. Once I swap that out, then I get a few, much nastier errors:

```
[ERROR   ] 21:52:08 ui:65 Unable to find the requested UI: gtk.  Please select a different UI with the '-u' option or alternatively use the '-s' option to select a different default UI.
Traceback (most recent call last):
  File "/usr/bin/deluge", line 8, in <module>
    load_entry_point('deluge==1.1.3', 'console_scripts', 'deluge')()
  File "/var/lib/python-support/python2.6/deluge/main.py", line 120, in start_ui
    UI(options, args, options.args)
  File "/var/lib/python-support/python2.6/deluge/ui/ui.py", line 66, in __init__
    sys.exit(0)
NameError: global name 'sys' is not defined
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 85, in apport_excepthook
    os.O_WRONLY|os.O_CREAT|os.O_EXCL), 'w')
OSError: [Errno 17] File exists: '/var/crash/_usr_bin_deluge.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/deluge", line 8, in <module>
    load_entry_point('deluge==1.1.3', 'console_scripts', 'deluge')()
  File "/var/lib/python-support/python2.6/deluge/main.py", line 120, in start_ui
    UI(options, args, options.args)
  File "/var/lib/python-support/python2.6/deluge/ui/ui.py", line 66, in __init__
    sys.exit(0)
NameError: global name 'sys' is not defined
```

I thought deluge was quite a popular application and I haven't seen any bug reports suggesting it's not working for other people... So what have I broken?

---

### Post by neppakyo on 2009-03-04
As with awn, deluge requires the older python libs, so there are now dependency problems.

Well, with me using jaunty. iirc, both require python < 2.6

---

