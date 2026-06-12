---
title: "Ubiquity Fails to Launch-Ubuntu 12.04.1 Based Remaster"
date: 2012-10-15
forum: Installation &amp; Upgrades
---

### Post by Harsh Kumar Narula on 2012-10-15
Kindly Help ! Gui does not launch, even with -d option. Thanks-Harsh

---

### Post by Harsh Kumar Narula on 2012-10-15
Let me add some debug info as well.

**$ cat /var/log/debug gives:**

Invalid animation description
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 579, in <module>
    main(oem_config)
  File "/usr/lib/ubiquity/bin/ubiquity", line 566, in main
    install(query=options.query)
  File "/usr/lib/ubiquity/bin/ubiquity", line 245, in install
    wizard = ui.Wizard(distro)
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 246, in __init__
    self.locale = i18n.reset_locale(self)
  File "/usr/lib/ubiquity/ubiquity/i18n.py", line 32, in reset_locale
    di_locale = frontend.db.get('debian-installer/locale')
  File "/usr/lib/python2.7/dist-packages/debconf.py", line 60, in <lambda>
    lambda *args, **kw: self.command(command, *args, **kw))
  File "/usr/lib/python2.7/dist-packages/debconf.py", line 96, in command
    raise DebconfError(status, data)
DebconfError: (10, "debian-installer/locale doesn't exist")

Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 423, in excepthook
    self.crash_detail_label.set_text(tbtext)
AttributeError: Wizard instance has no attribute 'crash_detail_label'

Original exception was:
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 579, in <module>
    main(oem_config)
  File "/usr/lib/ubiquity/bin/ubiquity", line 566, in main
    install(query=options.query)
  File "/usr/lib/ubiquity/bin/ubiquity", line 245, in install
    wizard = ui.Wizard(distro)
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 246, in __init__
    self.locale = i18n.reset_locale(self)
  File "/usr/lib/ubiquity/ubiquity/i18n.py", line 32, in reset_locale
    di_locale = frontend.db.get('debian-installer/locale')
  File "/usr/lib/python2.7/dist-packages/debconf.py", line 60, in <lambda>
    lambda *args, **kw: self.command(command, *args, **kw))
  File "/usr/lib/python2.7/dist-packages/debconf.py", line 96, in command
    raise DebconfError(status, data)
debconf.DebconfError: (**10, "debian-installer/locale doesn't exist"**)

---

