---
title: "trouble installing MoinMoin Wiki"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by El_Matthews on 2007-07-06
Gents,

I installed MoinMoin like specified in the official Ubuntu documentation [https://help.ubuntu.com/7.04/server/C/moinmoin.html](https://help.ubuntu.com/7.04/server/C/moinmoin.html)

when launching the wiki I get the following errors:
```
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/MoinMoin/request.py", line 1376, in __init__
    RequestBase.__init__(self, properties)
  File "/var/lib/python-support/python2.5/MoinMoin/request.py", line 113, in __init__
    self._load_multi_cfg()
  File "/var/lib/python-support/python2.5/MoinMoin/request.py", line 261, in _load_multi_cfg
    self.cfg = multiconfig.getConfig(self.url)
  File "/var/lib/python-support/python2.5/MoinMoin/multiconfig.py", line 154, in getConfig
    config = _makeConfig(configName)
  File "/var/lib/python-support/python2.5/MoinMoin/multiconfig.py", line 93, in _makeConfig
    module, mtime = _importConfigModule(name)
  File "/var/lib/python-support/python2.5/MoinMoin/multiconfig.py", line 43, in _importConfigModule
    raise error.ConfigurationError(msg)
ConfigurationError: NameError: name 'Note' is not defined
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/MoinMoin/multiconfig.py", line 29, in _importConfigModule
    module = __import__(name, globals(), {})
  File "/etc/moin/mywiki.py", line 35, in <module>
    [Note]
NameError: name 'Note' is not defined

Additionally cgitb raised this exception:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/MoinMoin/failure.py", line 142, in handle
    handler = cgitb.Hook(file=request, display=request.cfg.show_traceback,
AttributeError: 'RequestCGI' object has no attribute 'cfg'
```

Any idea?

---

### Post by El_Matthews on 2007-07-17
Nobody ? At least a tip to start searching because now I have no clue where to start.

---

### Post by wunder08 on 2007-09-11
The Ubuntu documentation is missing a command to adapt some access rights.

Try the following:

#> cd /etc/moin
#> sudo chown www-data.www-data *

This makes moin able to access these config files...

---

