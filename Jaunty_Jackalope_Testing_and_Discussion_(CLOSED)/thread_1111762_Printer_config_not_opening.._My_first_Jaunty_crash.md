---
title: "Printer config not opening.. My first Jaunty crash dialog!"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sgtbug on 2009-03-31
Hi guys

Jaunty BETA has been just awesome. The thing that impressed me most was the OO.o performance.. superb!

So, I finally crashed my Printer config GUI. It won't open now. This happened after I installed cups-pdf package. I even removed it, but the problem persists. Any workarounds? the web based cups interface is opening btw..

I am using 2 network printers. An HP Laserjet 1020 and an old Epson FX-1170 (9-pin DMP)..

TY in advance..

Regards

---

### Post by sgtbug on 2009-03-31
This is the debug output..

```

Connected as user akhil
refresh
Created subscription 9
<monitor.Monitor instance at 0x22d4680>: printers and jobs lists provided
update_jobs
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 6760, in <module>
    focus_on_map)
  File "/usr/share/system-config-printer/system-config-printer.py", line 6708, in main
    print_test_page, focus_on_map)
  File "/usr/share/system-config-printer/system-config-printer.py", line 819, in __init__
    self.populateList()
  File "/usr/share/system-config-printer/system-config-printer.py", line 1270, in populateList
    self.printers = cupshelpers.getPrinters(self.cups)
  File "/var/lib/python-support/python2.6/cupshelpers/cupshelpers.py", line 419, in getPrinters
    printer = Printer(name, connection, **printer)
  File "/var/lib/python-support/python2.6/cupshelpers/cupshelpers.py", line 40, in __init__
    self.update (**kw)
  File "/var/lib/python-support/python2.6/cupshelpers/cupshelpers.py", line 88, in update
    self._expand_flags()
  File "/var/lib/python-support/python2.6/cupshelpers/cupshelpers.py", line 68, in _expand_flags
    locale.setlocale (locale.LC_CTYPE, current_ctype)
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
Exception AttributeError: "Printer instance has no attribute '_ppd'" in <bound method Printer.__del__ of <cupshelpers.Printer "epsonfx">> ignored

```

---

