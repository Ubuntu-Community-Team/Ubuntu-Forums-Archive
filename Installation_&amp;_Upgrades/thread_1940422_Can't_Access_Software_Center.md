---
title: "Can't Access Software Center"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by clbaines on 2012-03-13
At the moment I cannot open the software center by clicking the icon. Get disk activity but the application does not open. 

I tried: sudo software-center   Still won't open. Error message is as follows:
2012-03-13 13:56:16,041 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
Traceback (most recent call last):
  File "/usr/bin/software-center", line 151, in <module>
    app = SoftwareCenterAppGtk3(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 221, in __init__
    self.db.open(use_axi = self._use_axi)
  File "/usr/share/software-center/softwarecenter/db/database.py", line 200, in open
    self._axi_values = parse_axi_values_file()
  File "/usr/share/software-center/softwarecenter/db/database.py", line 53, in parse_axi_values_file
    axi_values[key] = int(value)
ValueError: invalid literal for int() with base 10: '/var/cache/apt-xapian-index/index.2'

Anyone had this one?

---

