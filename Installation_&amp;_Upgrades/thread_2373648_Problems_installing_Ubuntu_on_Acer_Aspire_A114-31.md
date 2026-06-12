---
title: "Problems installing Ubuntu on Acer Aspire A114-31"
date: 2017-10-08
forum: Installation &amp; Upgrades
---

### Post by n1ghtr08d on 2017-10-08
I really need some help installing Ubuntu on my new laptop PLEASE! I have a new Acer Aspire a114-31, 64gb emmc, 4gb ram, quad core Pentium processor.
Now, I'm no stranger to Ubuntu as I've ran and installed it many times on many PCs but this is my first time with a laptop using an emmc as opposed to a traditional hdd.
I've made a bootable USB using Rufus of the latest 16.04 and when I boot into the live system and attempt to install, the install always halts during the Grub2 installation part.
Here's what the log always reads:
```
Ubiquity 2.21.63.4
Gtk-Message: Failed to load module "overlay-scrollbar"
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:53: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GObject, GLib, Atk
/usr/lib/ubiquity/plugins/ubi-timezone.py:195: PyGIWarning: TimezoneMap was imported without specifying a version first. Use gi.require_version('TimezoneMap', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import TimezoneMap
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "overlay-scrollbar"
update_release_notes_label()
Could not translate page (prepare): 'NoneType' object has no attribute 'replace'
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
No such schema 'org.mate.SettingsDaemon.plugins.media-keys'
Ubiquity 2.21.63.4
Gtk-Message: Failed to load module "overlay-scrollbar"
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:53: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GObject, GLib, Atk
/usr/lib/ubiquity/plugins/ubi-timezone.py:195: PyGIWarning: TimezoneMap was imported without specifying a version first. Use gi.require_version('TimezoneMap', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import TimezoneMap
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "overlay-scrollbar"
update_release_notes_label()
Could not translate page (prepare): 'NoneType' object has no attribute 'replace'
/usr/lib/ubiquity/ubiquity/segmented_bar.py:34: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, PangoCairo

(ubiquity:4052): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4052): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4052): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4052): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4052): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:4052): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 858 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 916 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
No such schema 'org.mate.SettingsDaemon.plugins.media-keys'
Ubiquity 2.21.63.4
Gtk-Message: Failed to load module "overlay-scrollbar"
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:53: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GObject, GLib, Atk
/usr/lib/ubiquity/plugins/ubi-timezone.py:195: PyGIWarning: TimezoneMap was imported without specifying a version first. Use gi.require_version('TimezoneMap', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import TimezoneMap
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "overlay-scrollbar"
update_release_notes_label()
Could not translate page (prepare): 'NoneType' object has no attribute 'replace'
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 769 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/segmented_bar.py:34: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, PangoCairo

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 821 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 881 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 2876 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed

(ubiquity:9380): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 5659 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 2930 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/plugins/ubi-timezone.py:98: PyGIWarning: Soup was imported without specifying a version first. Use gi.require_version('Soup', '2.4') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GObject, GLib, Soup
/usr/lib/ubiquity/plugins/ubi-timezone.py:209: Warning: Source ID 9040 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/plugins/ubi-timezone.py:209: Warning: Source ID 9152 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:116: Warning: Source ID 9841 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_layout_timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:116: Warning: Source ID 11058 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_layout_timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:138: Warning: Source ID 9843 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_variant_timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 8790 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 8849 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:72: Warning: Source ID 11070 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_layout_timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:74: Warning: Source ID 11076 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_variant_timeout_id)
/usr/lib/ubiquity/plugins/ubi-usersetup.py:394: Warning: Source ID 11477 was not found when attempting to remove it
  GLib.source_remove(self.hostname_timeout_id)
/usr/lib/ubiquity/plugins/ubi-usersetup.py:394: Warning: Source ID 11492 was not found when attempting to remove it
  GLib.source_remove(self.hostname_timeout_id)
/usr/lib/ubiquity/plugins/ubi-usersetup.py:394: Warning: Source ID 11502 was not found when attempting to remove it
  GLib.source_remove(self.hostname_timeout_id)
/usr/lib/ubiquity/plugins/ubi-usersetup.py:394: Warning: Source ID 11525 was not found when attempting to remove it
  GLib.source_remove(self.hostname_timeout_id)
/usr/lib/ubiquity/plugins/ubi-usersetup.py:394: Warning: Source ID 11530 was not found when attempting to remove it
  GLib.source_remove(self.hostname_timeout_id)
Gtk-Message: Failed to load module "overlay-scrollbar"
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 11116 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 11230 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 12270 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 12331 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 12801 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 12870 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 14276 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 14365 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 15933 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 15989 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 21387 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 21445 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 24024 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 24079 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
update_release_notes_label()
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 24083 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 24161 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
```

I have tried to install several times and spent 2 whole days (today being the start of the 3rd day) but still fail at the same place.
I have read tons of stuff about UEFI and secure boot. I have turned secure boot on and off, same result.
I tried creating new EXT4, swap, and EFI partitions on the drive and still have no luck.
Can somebody please help me get Ubuntu dual booted on this machine. I need it to be dual boot as I use Windows for several other things that won't run on Linux.

Thanks

---

### Post by mörgæs on 2017-10-08
Welcome to the fora.

New hardware and old software are an unhappy marriage. First, how does it work in a live boot of 17.10 (beta)?

---

### Post by oldfred on 2017-10-08
Are you trying to dual boot, as 64GB is not a lot even for just Windows?

Post this:
sudo parted -l

Are you installing in UEFI or BIOS boot mode? With ESP - efi system partition you must boot install media in UEFI boot mode to install in UEFI mode.

---

### Post by tuxayo on 2018-04-28
Same problem with an Acer  A114-31-C4ZV
Tried Xubuntu 16.04.4
  - with and without full disk encryption
  - ubiquity (the installer) in stuck and in the details reported «general protection fault»

Debian gnome 9.4 live non free
  - without full disk encryption

DF Linux rev 1 [https://dflinux.frama.io/home/](https://dflinux.frama.io/home/)
  - with full disk encryption

Fedora 27 XFCE Live failed at grub installation

Will add more info as we try things.

---

