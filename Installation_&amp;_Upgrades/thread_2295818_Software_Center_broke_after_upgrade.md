---
title: "Software Center broke after upgrade"
date: 2015-09-21
forum: Installation &amp; Upgrades
---

### Post by ebike on 2015-09-21
Hi All,

I have the following error when trying to run software center after a recent upgrade:

> ** (software-center:13666): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-dSDgs7HcLg: Connection refused
2015-09-22 07:48:41,620 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'http://proxy.trimble.co.nz:3128/'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 407, in __init__
    self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/historypane.py", line 79, in __init__
    self._get_emblems(self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/historypane.py", line 199, in _get_emblems
    pb = icons.load_icon(emblem, self.ICON_SIZE, 0)
gi._glib.GError: Error opening file: No such file or directory

Anyone have any idea's as to what is wrong? Looks like it has an issue with icon loading ...

---

