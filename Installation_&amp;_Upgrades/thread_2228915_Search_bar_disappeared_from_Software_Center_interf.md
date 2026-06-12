---
title: "Search bar disappeared from Software Center interface"
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by asb3 on 2014-06-10
The Search bar no longer appears in the Ubuntu Software Center window, making it very difficult to find software.

---

### Post by papibe on 2014-06-10
Hi asb3.

Try pressing Ctrl+F to see if the bar appears again.

Let us know if that works.
Regards.

---

### Post by asb3 on 2014-06-10
I tried Ctrl+f, and nothing happened.

---

### Post by papibe on 2014-06-10
Sorry to hear that.

Let's try open it from the terminal:
```
software-center
```
Regards.

---

### Post by asb3 on 2014-06-10
Still no search bar.
The following messages were written in to the terminal:
```

software-center&
[1] 22565
cavu{asb}82: 2014-06-10 11:00:51,319 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2014-06-10 11:00:51,815 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2014-06-10 11:00:51,816 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2014-06-10 11:00:51,820 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2014-06-10 11:00:51,819 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2014-06-10 11:00:51,843 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2014-06-10 11:00:52,117 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
2014-06-10 11:00:52,117 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
    0600)
DBInvalidArgError: (22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 74 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
2014-06-10 11:00:53,437 - softwarecenter.ui.gtk3.views.lobbyview - WARNING - skipping exhibit for: 'u'leadwerks\r\nleadwerks-indie'' not available
/usr/bin/software-center:184: Warning: Source ID 150 was not found when attempting to remove it
  Gtk.main()

(software-center:22565): Gtk-WARNING **: GtkEntry - did not receive focus-out-event. If you
connect a handler to this signal, it must return
FALSE so the entry gets the event as well
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 20 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
2014-06-10 11:00:59,595 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 266 was not found when attempting to remove it
  GLib.source_remove(self._timeout)

(software-center:22565): Gtk-CRITICAL **: gtk_widget_event: assertion 'WIDGET_REALIZED_FOR_EVENT (widget, event)' failed

(software-center:22565): Gtk-CRITICAL **: gtk_widget_event: assertion 'WIDGET_REALIZED_FOR_EVENT (widget, event)' failed

                                                                                                                                    
                                                                                                                                              

```

---

### Post by papibe on 2014-06-10
Have you tried resizing the window a little bit? making it a bit wider?

I tested that here, and the search bar actually disappears if you shrink the window (no place to draw it I guess). However, it appears again if you make it wider, or maximize it.

Let us know how it goes.
Regards.

---

### Post by asb3 on 2014-06-10
The search bar was present yesterday.  The interface looks very different than it did before.  Much more commercial.
Instead of just buttons to select "Installed", "Available", etc and a search bar, there is a large button advertising "Our star apps". Underneath that are two regions; on the left a list of categories (Accessories, Books and Magazines, etc) and on the right a region labeled "What's new".  Below the "Shat's new" is a region labelled "Recommended for you" that contains a button labelled "Turn on recommendations".  On the bottom is a region labelled "top rated" that contains more icons.

Nowhere is there a search widget.

I manage to bring up a search window by some series of mouse clicks that I can't reproduce.

Is there anyway to go back to the old interface, with a simple search widget instead of all the bells, whistles and ads

---

### Post by asb3 on 2014-06-10
Making the window wider works.
Thanks.

---

