---
title: "Ubuntu Software Center doesn't start anymore"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by fabalicious on 2010-10-24
If I select Ubuntu Software Center under Applications (Ubuntu 10.10), it seems like it's starting to open the application (processing for 5 seconds or so) but then aborts and nothing happens.

If I want to start if from the shell, I get the following error message:
[COLOR=Blue]
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/apt/aptcache.py", line 105, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 88, in __init__
    self.open(progress)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 130, in open
    self._list.read_main_list()
SystemError: E:Malformed line 62 in source list /etc/apt/sources.list (dist parse)
Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 316, in __init__
    self.view_switcher = ViewSwitcher(self.view_manager, datadir, self.db, self.cache, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 59, in __init__
    store = ViewSwitcherList(view_manager, datadir, db, cache, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 321, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 399, in _update_channel_list
    self._update_channel_list_installed_view()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 452, in _update_channel_list_installed_view
    if (pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/apt/aptcache.py", line 128, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'[/COLOR]

This used to work but has suddenly stopped doing so. Maybe some interference with another applications/settings? No idea what it could be though. Any suggestions are highly welcome. Cheers!

---

### Post by sikander3786 on 2010-10-24
Try updating from the terminal and again start software center.

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

