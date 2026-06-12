---
title: "Software Center not in dropdown menu"
date: 2016-08-11
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2016-08-11
After updating from 14.04 to 16.04 the Software Center does not appear in the "Applications" drop down in Gnome Metacity or Gnome Compiz.  It does appear if I start in straightforward Ubuntu.  

I can also start it from the Terminal, using " software-center ".  However, after several attempts at getting it to appear on the drop down following several different suggestions, starting from Terminal gets the below:  It originally started an apparently newer version (don't have number).
----------------------------------
```
roger@roger-desktop:~$ software-center
/usr/bin/software-center:25: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GObject
/usr/share/software-center/softwarecenter/ui/gtk3/views/purchaseview.py:29: PyGIWarning: WebKit2 was imported without specifying a version first. Use gi.require_version('WebKit2', '4.0') before import to ensure that the right version gets loaded.
  from gi.repository import WebKit2 as webkit
2016-08-10 21:10:10,342 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/symbolic_icons.py:23: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GLib, PangoCairo
2016-08-10 21:10:10,476 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2016-08-10 21:10:14,717 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2016-08-10 21:10:15,379 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2016-08-10 21:10:15,397 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2016-08-10 21:10:15,481 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2016-08-10 21:10:15,921 - softwarecenter.db.update - WARNING - failed to load file /var/lib/apt-xapian-index/cataloged_times.p: unsupported pickle protocol: 3
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/videoplayer.py:29: PyGIWarning: Gst was imported without specifying a version first. Use gi.require_version('Gst', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gst
/usr/bin/software-center:184: Warning: Source ID 119 was not found when attempting to remove it
  Gtk.main()
/usr/bin/software-center:184: Warning: Source ID 78 was not found when attempting to remove it
  Gtk.main()
2016-08-10 21:10:19,086 - softwarecenter.db.update - WARNING - failed to load file /var/lib/apt-xapian-index/cataloged_times.p: unsupported pickle protocol: 3
2016-08-10 21:10:20,605 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
2016-08-10 21:10:20,653 - softwarecenter.db.application - WARNING - document no longer valid after db reopen
2016-08-10 21:10:20,680 - softwarecenter.db.application - WARNING - document no longer valid after db reopen
2016-08-10 21:10:20,713 - softwarecenter.db.application - WARNING - document no longer valid after db reopen
2016-08-10 21:10:20,747 - softwarecenter.db.application - WARNING - document no longer valid after db reopen
2016-08-10 21:10:20,784 - softwarecenter.db.application - WARNING - document no longer valid after db reopen
2016-08-10 21:10:20,795 - softwarecenter.db.application - WARNING - document no longer valid after db reopen
2016-08-10 21:10:20,796 - softwarecenter.db.application - WARNING - document no longer valid after db reopen
2016-08-10 21:10:20,798 - softwarecenter.db.application - WARNING - document no longer valid after db reopen
org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
No handlers could be found for logger "update-software-center-channels"
roger@roger-desktop:~$ 
```
VERSION 15.12 APPEARS
---------------------------------------------
SECOND TRY
```
roger@roger-desktop:~$ software-center
/usr/bin/software-center:25: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GObject
/usr/share/software-center/softwarecenter/ui/gtk3/views/purchaseview.py:29: PyGIWarning: WebKit2 was imported without specifying a version first. Use gi.require_version('WebKit2', '4.0') before import to ensure that the right version gets loaded.
  from gi.repository import WebKit2 as webkit
2016-08-10 21:20:37,604 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/symbolic_icons.py:23: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GLib, PangoCairo
2016-08-10 21:20:37,627 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2016-08-10 21:20:38,435 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2016-08-10 21:20:38,437 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2016-08-10 21:20:38,477 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2016-08-10 21:20:38,823 - softwarecenter.db.update - WARNING - failed to load file /var/lib/apt-xapian-index/cataloged_times.p: unsupported pickle protocol: 3
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/videoplayer.py:29: PyGIWarning: Gst was imported without specifying a version first. Use gi.require_version('Gst', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gst
/usr/bin/software-center:184: Warning: Source ID 76 was not found when attempting to remove it
  Gtk.main()
/usr/bin/software-center:184: Warning: Source ID 117 was not found when attempting to remove it
  Gtk.main()
2016-08-10 21:20:42,075 - softwarecenter.db.update - WARNING - failed to load file /var/lib/apt-xapian-index/cataloged_times.p: unsupported pickle protocol: 3
2016-08-10 21:20:43,114 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
No handlers could be found for logger "update-software-center-channels"
```
VERSION 15.12 APPEARS
----------------------------------------------
AND DIFFERENT AGAIN...
```
roger@roger-desktop:~$ software-center
/usr/bin/software-center:25: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GObject
/usr/share/software-center/softwarecenter/ui/gtk3/views/purchaseview.py:29: PyGIWarning: WebKit2 was imported without specifying a version first. Use gi.require_version('WebKit2', '4.0') before import to ensure that the right version gets loaded.
  from gi.repository import WebKit2 as webkit
2016-08-10 21:25:28,308 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/symbolic_icons.py:23: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GLib, PangoCairo
2016-08-10 21:25:28,350 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2016-08-10 21:25:28,829 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2016-08-10 21:25:28,830 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2016-08-10 21:25:28,870 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2016-08-10 21:25:29,201 - softwarecenter.db.update - WARNING - failed to load file /var/lib/apt-xapian-index/cataloged_times.p: unsupported pickle protocol: 3
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/videoplayer.py:29: PyGIWarning: Gst was imported without specifying a version first. Use gi.require_version('Gst', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gst
/usr/bin/software-center:184: Warning: Source ID 70 was not found when attempting to remove it
  Gtk.main()
/usr/bin/software-center:184: Warning: Source ID 110 was not found when attempting to remove it
  Gtk.main()
2016-08-10 21:25:32,079 - softwarecenter.db.update - WARNING - failed to load file /var/lib/apt-xapian-index/cataloged_times.p: unsupported pickle protocol: 3
2016-08-10 21:25:32,730 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
No handlers could be found for logger "update-software-center-channels"
```
VERSION 15.12 APPEARS
----------------------------------------------
And then what appears to be the older version (15.12) appears, where the same command used to get the one that starts in the straightforward Ubuntu log-in - looks very different. 

As long as the contents and functions are the same, I don't really care which version appears.

The question(s) are:
1) If the best answer is to simply add it to the drop down, how is this accomplished?
2) If there is another way to make it appear on the drop-down, please let me know how to do this. 
3) Do I simply need to reinstall Software Center?  If so, how?

Thanks!

---

### Post by wildmanne39 on 2016-08-12
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by RogerDavis on 2016-08-12
I'm confused - I thought I did use code tags, I can see them as you describe if I open the message to edit it.  Or did you fix if for me?

If you did fix it, thanks!  If not, what is wrong with the one above, so I can learn?  It's all one message, an original New Post.

Thanks!

---

### Post by wildmanne39 on 2016-08-12
You used quote tags with that much output it looks better in code tags and it is easily scrollable.
The only difference is the word code is in the tag I used and not quote.
It is no problem just like to teach people the proper way.

---

### Post by RogerDavis on 2016-08-14
The more I work on this, the more I think the problem is in Gnome.  How hard is it to uninstall and then reinstall Gnome in 16.06?  I don't see Gnome in the "new" Software Center that starts from the straight Ubuntu boot, but I do see it in the one that starts in Gnome.  But NEITHER one shows Gnome as installed !

Are there conflicts between Gnome and Ubuntu 16.04

Maybe I should remove Gnome and install Cinnamon?

---

