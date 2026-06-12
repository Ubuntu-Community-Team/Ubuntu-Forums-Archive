---
title: "gnome-app-install is getting stuck"
date: 2009-08-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-08-20
It's getting stuck while doing this:
[URL="http://dl.getdropbox.com/u/285483/tmp/screenshot13.png"]http://dl.getdropbox.com/u/285483/tmp/screenshot13.png

[/URL]I've apt-get reinstall gnome-app-install but it didn't help.
This are the error messages on the console (lots of them)
```

AttributeError: 'NoneType' object has no attribute 'has_key'
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/AppInstall/Menu.py", line 243, in _visible_filter
    self.itemIsInstalled(item):
  File "/usr/lib/python2.6/dist-packages/AppInstall/Menu.py", line 419, in itemIsInstalled
    return (self.cache.has_key(item.pkgname) and
AttributeError: 'NoneType' object has no attribute 'has_key'
/usr/lib/python2.6/dist-packages/AppInstall/AppInstall.py:1248: GtkWarning: gtk_tree_model_sort_set_sort_column_id: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_sort_column_id(-1, sort_type)

```

Any ideas?

---

