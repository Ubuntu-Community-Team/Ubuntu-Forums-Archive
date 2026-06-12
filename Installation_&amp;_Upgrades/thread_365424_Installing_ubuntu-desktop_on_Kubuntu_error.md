---
title: "Installing ubuntu-desktop on Kubuntu error"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by rami on 2007-02-19
I installed Gnome on Kubuntu (Edgy) using 

```
sudo aptitude install ubuntu-desktop
```

And now I get whenever I install a new program I get this error:

```
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 69, in ?
    generate_cache()
  File "/usr/sbin/update-app-install", line 49, in generate_cache
    menu.createMenuCache(options.cache_dir)
  File "/usr/lib/python2.4/site-packages/AppInstall/CoreMenu.py", line 28, in createMenuCache
    menu = xdg.Menu.parse(os.path.abspath(os.path.join(self.menudir, "applications.menu")))
  File "/var/lib/python-support/python2.4/xdg/Menu.py", line 524, in parse
    __genmenuNotOnlyAllocated(tmp["Root"])
  File "/var/lib/python-support/python2.4/xdg/Menu.py", line 856, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/var/lib/python-support/python2.4/xdg/Menu.py", line 862, in __genmenuNotOnlyAllocated
    menuentries = rule.do(tmp["cache"].getMenuEntries(menu.AppDirs), rule.Type, 1)
  File "<string>", line 6, in do
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc2 in position 5: ordinal not in range(128)
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-app-install
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gnome-app-install (0.2.21) ...
Caching application data...
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 69, in ?
    generate_cache()
  File "/usr/sbin/update-app-install", line 49, in generate_cache
    menu.createMenuCache(options.cache_dir)
  File "/usr/lib/python2.4/site-packages/AppInstall/CoreMenu.py", line 28, in createMenuCache
    menu = xdg.Menu.parse(os.path.abspath(os.path.join(self.menudir, "applications.menu")))
  File "/var/lib/python-support/python2.4/xdg/Menu.py", line 524, in parse
    __genmenuNotOnlyAllocated(tmp["Root"])
  File "/var/lib/python-support/python2.4/xdg/Menu.py", line 856, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/var/lib/python-support/python2.4/xdg/Menu.py", line 862, in __genmenuNotOnlyAllocated
    menuentries = rule.do(tmp["cache"].getMenuEntries(menu.AppDirs), rule.Type, 1)
  File "<string>", line 6, in do
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc2 in position 5: ordinal not in range(128)
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-app-install
 ubuntu-desktop

```

Where did I go wrong??

---

