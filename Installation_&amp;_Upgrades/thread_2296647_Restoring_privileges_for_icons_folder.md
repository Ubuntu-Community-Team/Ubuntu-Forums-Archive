---
title: "Restoring privileges for icons folder"
date: 2015-09-27
forum: Installation &amp; Upgrades
---

### Post by barkerson on 2015-09-27
So after manually moving and merging files (through the terminal) for a compiled version of Krita I have now managed to screw up the folder/file privileges for icons, everything else seems to work without issues except for having no icons whatsoever. I'm not sure exactly how to change the permissions to make icons work either. Any good ideas on how to fix this?

---

### Post by v3.xx on 2015-09-28
And you have no error messages to work with?

---

### Post by barkerson on 2015-09-28
software center is the only program to refuse, it says:
```

(software-center:4413): Gtk-WARNING **: Error loading image 'file:///usr/share/themes/Ambiance/gtk-3.0/assets/entry.png': Unrecognized image file format

(software-center:4413): Gtk-WARNING **: Error loading image 'file:///usr/share/themes/Ambiance/gtk-3.0/assets/entry-disabled.png': Unrecognized image file format
2015-09-28 17:41:42,788 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'

(software-center:4413): Gtk-WARNING **: Error loading image 'file:///usr/share/themes/Ambiance/gtk-3.0/assets/button-active.png': Unrecognized image file format
2015-09-28 17:41:43,896 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 407, in __init__
    self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/historypane.py", line 79, in __init__
    self._get_emblems(self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/historypane.py", line 199, in _get_emblems
    pb = icons.load_icon(emblem, self.ICON_SIZE, 0)
GLib.Error: gdk-pixbuf-error-quark: Unrecognized image file format (3)

```
 guess this is what I should expect happen when using gksudo rsunc to move files, my luck

---

### Post by v3.xx on 2015-09-28
I do not use the software center and have not "gksudo rsync" anything, but do use "gksudo nemo" to move files.  Big difference though.

For me, this sums it up.

[http://ubuntuforums.org/showthread.php?t=2296524&p=13362940#post13362940](http://ubuntuforums.org/showthread.php?t=2296524&p=13362940#post13362940)

---

### Post by barkerson on 2015-09-28
nonono, it's not the update center itself I was having issues with, it's just that it's the only way I can seem to find anything about any errors, I usually use apt-get to install programs myself as I find that to be quicker that waiting for the UI to load up.
[These]("http://i.imgur.com/AYDc9t9.png") are the issues I have to deal with

---

### Post by v3.xx on 2015-09-28
Wow, that&#8217;s rather drab looking.

And I lack the krita (kde) skills to assist any farther, sorry.

Good luck :)

---

### Post by barkerson on 2015-09-29
welp, looks like installing Krita (old version) broke Krita but fixed ubuntu, looks like I'll just have to wait for Krita 2.9.7 to hit ubuntu sometime in the future, man does not being able to fully compress the project files suck

---

### Post by oldos2er on 2015-09-29
There's a PPA: [https://launchpad.net/~dimula73/+archive/ubuntu/krita](https://launchpad.net/~dimula73/+archive/ubuntu/krita)

---

### Post by barkerson on 2015-09-30
That's still 2.9.2 for me, adding ppa, apt-get update, apt-get upgrade, installing Krita still gives me version 2.9.2. Don't know what's up with that...

---

### Post by oldos2er on 2015-09-30
You probably need to run ```
sudo apt-get dist-upgrade
``` instead of just "upgrade."

---

### Post by barkerson on 2015-10-01
just wiping and recompiling worked fine to me, not sure why though

---

