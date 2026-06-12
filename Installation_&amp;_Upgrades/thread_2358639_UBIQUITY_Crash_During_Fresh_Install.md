---
title: "UBIQUITY Crash During Fresh Install"
date: 2017-04-15
forum: Installation &amp; Upgrades
---

### Post by umityayla on 2017-04-15
Guys, i'm trying to install a fresh ubuntu via an usb drive and i can say i'm a newbie to ubuntu.
My problem is; 
ubiquity crashes during installation, i've tried dozens of times changed so many stuff i don't remember but i need your help and yes i can use the live version and actually i'm typing this thread via live version..
Here's the output of /var/log/installer/debug file;

```
Ubiquity 17.04.9
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:53: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GObject, GLib, Atk
/usr/lib/ubiquity/plugins/ubi-timezone.py:195: PyGIWarning: TimezoneMap was imported without specifying a version first. Use gi.require_version('TimezoneMap', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import TimezoneMap

(process:4748): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:4770): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:4785): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:4797): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:4810): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:4828): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
update_release_notes_label()
Could not translate page (prepare): 'NoneType' object has no attribute 'replace'
update_release_notes_label()
/usr/lib/ubiquity/ubiquity/segmented_bar.py:34: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, PangoCairo

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 4218 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 4337 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4686): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(process:19866): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:19877): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:19891): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:19904): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:19947): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
/usr/lib/ubiquity/plugins/ubi-language.py:303: Warning: Source ID 178 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 10146 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:477: Warning: Source ID 170 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 10253 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/plugins/ubi-timezone.py:98: PyGIWarning: Soup was imported without specifying a version first. Use gi.require_version('Soup', '2.4') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GObject, GLib, Soup
/usr/lib/ubiquity/plugins/ubi-timezone.py:209: Warning: Source ID 15242 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:72: Warning: Source ID 17090 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_layout_timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:74: Warning: Source ID 17093 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_variant_timeout_id)
/usr/lib/ubiquity/plugins/ubi-usersetup.py:394: Warning: Source ID 17326 was not found when attempting to remove it
  GLib.source_remove(self.hostname_timeout_id)
/usr/lib/ubiquity/plugins/ubi-language.py:303: Warning: Source ID 178 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
Memory pressure relief: Total: res = 10256384/8175616/-2080768, res+swap = 0/0/0
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 15218 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 15298 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
Memory pressure relief: Total: res = 24739840/24399872/-339968, res+swap = 0/0/0
Memory pressure relief: Total: res = 22409216/21233664/-1175552, res+swap = 0/0/0
Memory pressure relief: Total: res = 20484096/20484096/0, res+swap = 0/0/0
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 17701 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 17790 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
Memory pressure relief: Total: res = 21274624/21184512/-90112, res+swap = 0/0/0
Memory pressure relief: Total: res = 21270528/21176320/-94208, res+swap = 0/0/0
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 18751 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 18824 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 20311 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 20400 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Memory pressure relief: Total: res = 21643264/21508096/-135168, res+swap = 0/0/0

(process:25657): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:25671): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:25679): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
Memory pressure relief: Total: res = 21508096/21008384/-499712, res+swap = 0/0/0

(process:25687): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:25699): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:25709): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
No such schema “org.mate.SettingsDaemon.plugins.media-keys”

(process:25719): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:25727): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:25735): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:25743): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:25751): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:25759): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
```

---

