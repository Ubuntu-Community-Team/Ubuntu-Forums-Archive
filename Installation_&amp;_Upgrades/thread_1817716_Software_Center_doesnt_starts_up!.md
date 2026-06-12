---
title: "Software Center doesnt starts up!"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by SkyPoweR on 2011-08-03
I tried to run it throught the terminal to see the problem,

```

Traceback (most recent call last):
  File "/usr/bin/software-center", line 111, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 52, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 35, in <module>
    from softwarepane import SoftwarePane
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 49, in <module>
    from purchaseview import PurchaseView
  File "/usr/share/software-center/softwarecenter/view/purchaseview.py", line 27, in <module>
    import webkit
  File "/usr/lib/pymodules/python2.7/webkit/__init__.py", line 21, in <module>
    import webkit
ImportError: /usr/lib/x86_64-linux-gnu/libXt.so.6: undefined symbol: YrmStringToBindingQuarkList


```

Thanks.

---

