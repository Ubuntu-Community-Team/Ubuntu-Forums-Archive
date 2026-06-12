---
title: "Can't open the compiz config settings manager in compiz fusion 0.7.2"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by whiteygford on 2008-03-09
```
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 57, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
    self.Context.Plugins.items ())
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
    self.PluginList = filter (lambda p: FilterPlugin (p[1]),
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
    return not p.Initialized and p.Enabled
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
```

Ive seen help on this error for older versions of compiz and it can be fixed with changing repositories, but I've been using compizfusion without trouble since I upgraded to ubuntu 7.10 and I haven't had trouble until compizfusion updated to 0.6.2

Any thoughts?

---

