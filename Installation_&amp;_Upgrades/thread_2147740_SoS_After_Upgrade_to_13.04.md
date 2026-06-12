---
title: "SoS After Upgrade to 13.04"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by SalamFromMaroc on 2013-05-22
```
hi everyone

i did have problem in my internet while i was upgrading to 13.04.so after this problem i was not able to turn on my computer.but after googling i did fix my ubuntu,but here s my recent problem

i have a mesage in my ubuntu say: an error occured ,please run package maneger from the right-click menu or apt-get in a terminal to see what is wrang.the error message was :'error.brokencount>0'.this usually means that your installed packages have unmet dependencies

also when i try open ubuntu software center wont star,and also software sources and management service wont star too.


also when i write software-center in terminal show me this error message

(software-center:2800): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:62:17: Theming engine 'unico' not found
2013-05-22 21:47:19,483 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 290, in __init__
    self.cache = get_pkg_info()
  File "/usr/share/software-center/softwarecenter/db/pkginfo.py", line 240, in get_pkg_info
    from softwarecenter.db.pkginfo_impl.aptcache import AptCache
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 30, in <module>
    from aptdaemon.client import AptClient
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 70, in <module>
    class MemoizedMixInMeta(MemoizedTransaction, GObject.GObjectMeta):
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 316, in __getattr__
    return getattr(self._introspection_module, name)
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 135, in __getattr__
    self.__name__, name))
AttributeError: 'gi.repository.GObject' object has no attribute 'GObjectMeta'

how can i resolve this errors   


thanks in advance.

```

---

### Post by ibjsb4 on 2013-05-23
Looks like the software center is out.  Install [synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") and user it to reinstall the software center, see if that helps.  If not, you can use synaptic for package installation until you get the problem fixed.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get install synaptic
```

---

### Post by SalamFromMaroc on 2013-05-23
```

sudo apt-get install synaptic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate

pls if any one can help me,i can t open ubuntu software center and .................
```

---

### Post by ibjsb4 on 2013-05-23
Ok, try this ..
```

sudo apt-get update && sudo apt-get dist-upgrade
```

If your wondering what these commands do, look [here]("https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands").

If you get any errors from those commands, please post them.

---

### Post by SalamFromMaroc on 2013-05-23
```
Fetched 181 kB in 1min 6s (2,714 B/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_raring_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_raring_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by ibjsb4 on 2013-05-23
Give this a try ..

[http://ubuntuforums.org/showthread.php?t=2131178&p=12583395&viewfull=1#post12583395](http://ubuntuforums.org/showthread.php?t=2131178&p=12583395&viewfull=1#post12583395)

---

