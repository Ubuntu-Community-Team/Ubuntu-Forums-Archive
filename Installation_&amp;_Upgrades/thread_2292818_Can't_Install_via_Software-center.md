---
title: "Can't Install via Software-center"
date: 2015-08-31
forum: Installation &amp; Upgrades
---

### Post by astarmathsandphysics on 2015-08-31
I can install any software in software-center. In can uninstall things, and install/update/upgrade in the terminal.
I have reinstalled software center with no effect. When starting softwar-e-center in the terminal I get these messages

```
root@server:~# software-center
2015-08-31 11:55:38,986 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2015-08-31 11:55:40,498 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2015-08-31 11:55:41,441 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2015-08-31 11:55:41,462 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2015-08-31 11:55:41,623 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2015-08-31 11:55:42,673 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
2015-08-31 11:55:42,674 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
    0600)
DBInvalidArgError: (22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 67 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
No bp log location saved, using default.
[000:000] Cpu: 6.15.11, x8, 1595Mhz, 3952MB
[000:001] Computer model: Not available
[000:001] Browser XEmbed support present: 1
[000:001] Browser toolkit is Gtk2.
[000:106] Using Gtk2 toolkit
[000:152] Warning(optionsfile.cc:30): Load: Could not open file, err=2
[000:152] No bp log location saved, using default.
[000:155] Cpu: 6.15.11, x8, 1595Mhz, 3952MB
[000:156] Computer model: Not available
[000:156] Browser XEmbed support present: 1
[000:156] Browser toolkit is Gtk2.
[000:157] Using Gtk2 toolkit
No bp log location saved, using default.
[000:000] Cpu: 6.15.11, x8, 1595Mhz, 3952MB
[000:001] Computer model: Not available
[000:468] Warning(optionsfile.cc:30): Load: Could not open file, err=2
[000:468] No bp log location saved, using default.
[000:470] Cpu: 6.15.11, x8, 1595Mhz, 3952MB
[000:471] Computer model: Not available
2015-08-31 11:55:51,429 - softwarecenter.ui.gtk3.views.lobbyview - WARNING - skipping exhibit for: 'u'leadwerks\r\nleadwerks-indie'' not available
/usr/bin/software-center:184: Warning: Source ID 114 was not found when attempting to remove it
  Gtk.main()
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 165 was not found when attempting to remove it
  GLib.source_remove(self._timeout)
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 256 was not found when attempting to remove it
  GLib.source_remove(self._timeout)
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 287 was not found when attempting to remove it
  GLib.source_remove(self._timeout)
2015-08-31 11:56:32,503 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 20 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 341 was not found when attempting to remove it
  GLib.source_remove(self._timeout)
2015-08-31 11:56:39,421 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 370 was not found when attempting to remove it
  GLib.source_remove(self._timeout)
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 468 was not found when attempting to remove it
  GLib.source_remove(self._timeout)
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 499 was not found when attempting to remove it
  GLib.source_remove(self._timeout)
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 555 was not found when attempting to remove it
  GLib.source_remove(self._timeout)
root@server:~# 
```



I have google the error messages but can find no ansers..
What can I do?

---

### Post by dino99 on 2015-08-31
if your system is not using some bleeding/untrusted packages, then you hit a bug; otherwise use ppa-purge to set the system back to genuine packages.
Then run a 'sudo dpkg --configure -a'

---

### Post by Bucky Ball on 2015-08-31
Run these and post any and all errors, please.

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

