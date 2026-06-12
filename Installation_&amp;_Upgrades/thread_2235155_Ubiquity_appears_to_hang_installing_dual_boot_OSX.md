---
title: "Ubiquity appears to hang installing dual boot OSX"
date: 2014-07-19
forum: Installation &amp; Upgrades
---

### Post by sennett on 2014-07-19
I am trying to dual-boot OSX (10.9 Mavericks) and Ubuntu 14.04, and the Ubiquity installer has apparently hung for the last hour.

I resized my OSX partition using Disk Utility in OSX, and made a FAT partition there. Then in Ubuntu from the Live USB I ran the installer. Resized this partition a bit (screenshot) and confirmed. After that, nothing apart from the frozen UI, and the ubiquity process taking up most of a core.

There's a fatal error in the Ubiquity-dm log seemingly related to some X session not existing. Not entirely sure if this is relevant.

Ubiquity version 2.18.17.

[IMG]http://i.imgur.com/0YN6soD.png[/IMG]

[SIZE=5]Some log files[/SIZE]

[SIZE=4]/var/log/installer/debug[/SIZE]

```

	ubuntu@ubuntu:~$ tail -f /var/log/installer/debug 
	/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 332438 was not found when attempting to remove it
	  GLib.source_remove(self.rows_changed_id)
	/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 346649 was not found when attempting to remove it
	  GLib.source_remove(self.timeout_id)
	/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 346742 was not found when attempting to remove it
	  GLib.source_remove(self.rows_changed_id)
	/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 347267 was not found when attempting to remove it
	  GLib.source_remove(self.timeout_id)
	/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 347407 was not found when attempting to remove it
	  GLib.source_remove(self.rows_changed_id)

```
[SIZE=4]/var/log/installer/dm[/SIZE]
```

	ubuntu@ubuntu:~$ tail -f /var/log/installer/dm 
	(panel:2083): Gtk-CRITICAL **: gtk_widget_remove_accelerator: assertion 'GTK_IS_ACCEL_GROUP (accel_group)' failed
	ubiquity-dm: greeter exited with code 0
	nm-applet-Message: PID 1987 (we are 2105) sent signal 15, shutting down...

	(process:2086): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
	XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
	      after 21 requests (21 known processed) with 0 events remaining.
	(EE) Server terminated successfully (0). Closing log file.
	ubiquity-dm: set_locale
	ubiquity-dm: Exiting with code 0


```

---

### Post by sennett on 2014-07-19
There was something weird happening with the automatic partitioning.  I restarted, deleted the FAT partition created in OSX, manually partitioned the free space instead of accepting the defaults, and now everything is installing no problem.

---

