---
title: "Application Install"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by novavon on 2007-03-10
When gnome-app-install is type on the command line, I'm getting this kind of error and the program crashes. It crashes even when I run it through GUI (Applications -> Add/Remove Applications). The program still crashes after doing, "apt-get update" and "apt-get upgrade". I tried turning off the computer and restarting the xserver, but it would still crash.

I would appreciate any comment regarding issue.

```

Introspect error: The name org.freedesktop.AppInstall was not provided by any .service files
no listening object (The name org.freedesktop.AppInstall was not provided by any .service files) 

** (gnome-app-install:4971): WARNING **: return value of custom widget handler was not a GtkWidget
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 141, in ?
    sys.argv, mime_search=msi)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 230, in __init__
    self.updateCache(filter_to_restore)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 741, in updateCache
    progress, filter)
  File "/usr/lib/python2.4/site-packages/AppInstall/Menu.py", line 93, in __init__
    self.pickle = cPickle.load(open("%s/menu.p" % cachedir))
ValueError: insecure string pickle

```

---

### Post by Kateikyoushi on 2007-03-10
Does synaptic work ? System > Administration > Synaptic.

---

### Post by novavon on 2007-03-10
Yes, the Synaptic works, however the (System -> Administrator -> Update Manager) would crash once in a while as well.

---

### Post by Kateikyoushi on 2007-03-10
It seems like a python error which might just go away as you update it later. Meanwhile use synaptic and aptitude or apt-get for updating and installing, unless someone knows how to deal with this.

---

