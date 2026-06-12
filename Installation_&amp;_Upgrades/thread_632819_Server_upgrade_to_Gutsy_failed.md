---
title: "Server upgrade to Gutsy failed"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by EnterDaMatrix on 2007-12-05
This is really really bad. I was worried about this happening, why else would I wait a few months to upgrade to gutsy on my server? I assumed that the Ubuntu devs would have fixed the upgrade bugs by now, WRONG.

I started the upgrade through SSH with:
```
sudo do-release-upgrade
```
Just like it says to in the Wiki.

It was going fine until:
```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Errors were encountered while processing:
 transmission
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/usr/share/apport/apport-gtk:40: Warning: invalid (NULL) pointer instance
  'apport-gtk.glade'))
/usr/share/apport/apport-gtk:40: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  'apport-gtk.glade'))
/usr/share/apport/apport-gtk:40: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  'apport-gtk.glade'))
/usr/share/apport/apport-gtk:40: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  'apport-gtk.glade'))
/usr/share/apport/apport-gtk:40: Warning: value "TRUE" of type `gboolean' is invalid or out of range for property `visible' of type `gboolean'
  'apport-gtk.glade'))
/usr/share/apport/apport-gtk:48: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  self.w('treeview_reportdetails').append_column(column)
/usr/share/apport/apport-gtk:48: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  self.w('treeview_reportdetails').append_column(column)
/usr/share/apport/apport-gtk:84: GtkWarning: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window
  response = d.run()
/usr/share/apport/apport-gtk:84: GtkWarning: gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: PangoWarning: pango_context_set_font_description: assertion `context != NULL' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: PangoWarning: pango_context_set_base_dir: assertion `context != NULL' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: PangoWarning: pango_context_set_language: assertion `context != NULL' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: PangoWarning: pango_layout_new: assertion `context != NULL' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: PangoWarning: pango_layout_set_text: assertion `layout != NULL' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: PangoWarning: pango_layout_set_attributes: assertion `layout != NULL' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: PangoWarning: pango_layout_set_alignment: assertion `layout != NULL' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: PangoWarning: pango_layout_set_ellipsize: assertion `PANGO_IS_LAYOUT (layout)' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: PangoWarning: pango_layout_set_single_paragraph_mode: assertion `PANGO_IS_LAYOUT (layout)' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: PangoWarning: pango_layout_set_width: assertion `layout != NULL' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: PangoWarning: pango_layout_get_extents: assertion `layout != NULL' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: GtkWarning: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: GtkWarning: gtk_icon_size_lookup_for_settings: assertion `GTK_IS_SETTINGS (settings)' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: GtkWarning: Invalid icon size 6

  response = d.run()
/usr/share/apport/apport-gtk:84: GtkWarning: gtk_icon_theme_load_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed
  response = d.run()
/usr/share/apport/apport-gtk:84: Warning: g_error_free: assertion `error != NULL' failed
  response = d.run()

Could not install the upgrades
The upgrade aborts now. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
installArchives() failed
dpkg: dependency problems prevent configuration of transmission:
 transmission depends on transmission-cli (>= 0.93.dfsg-2~gutsy1); however:
  Package transmission-cli is not installed.
 transmission depends on transmission-gtk (>= 0.93.dfsg-2~gutsy1); however:
  Package transmission-gtk is not installed.
dpkg: error processing transmission (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 transmission

```

Well what now? I depend on this server for lots, and if there is no simple fix (I have tried dpkg --configure -a), then I'll have to move to a good distro (Arch probably). HELP!

---

### Post by EnterDaMatrix on 2007-12-07
I installed arch. I hate to say it but it is so much better than Ubuntu. <30MB of total memory in use FTW!

---

