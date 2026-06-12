---
title: "Natty no login (except safe mode)"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by bigdawgte on 2011-05-13
Upgraded to Natty from Maverick.  I may have had some unknown video problem (ATI 780G/HD 3200 - may have crashed or corrupted)immediately before upgrade.  Anyway, I cannot get to Unity, Classic (reg or no effects) or KDE; only safe mode.  Here is output from my .xsession-errors file:


/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 31: //: Permission denied
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
keytouchd: Plugin directory '/home/cotie/.keytouch2/plugins' does not exist. This program will continue without loading the plugins in this directory.
gnome-session[2448]: atk-bridge-WARNING: AT_SPI_REGISTRY was not started at session startup.
gnome-session[2448]: atk-bridge-WARNING: IOR not set.
gnome-session[2448]: atk-bridge-WARNING: Could not locate registry

(metacity:2467): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(metacity:2467): atk-bridge-WARNING **: IOR not set.

(metacity:2467): atk-bridge-WARNING **: Could not locate registry

(nautilus:2472): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(nautilus:2472): atk-bridge-WARNING **: IOR not set.

(nautilus:2472): atk-bridge-WARNING **: Could not locate registry

(gnome-panel:2475): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(gnome-panel:2475): atk-bridge-WARNING **: IOR not set.

(gnome-panel:2475): atk-bridge-WARNING **: Could not locate registry

(gnome-settings-daemon:2456): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(gnome-settings-daemon:2456): atk-bridge-WARNING **: IOR not set.

(gnome-settings-daemon:2456): atk-bridge-WARNING **: Could not locate registry
Initializing nautilus-clamscan extension
Initializing nautilus-dropbox 0.6.7
Initializing nautilus-gdu extension
sys:1: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
sys:1: GtkWarning: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(exo-open:2586): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(exo-open:2586): atk-bridge-WARNING **: IOR not set.

(exo-open:2586): atk-bridge-WARNING **: Could not locate registry

(exo-helper-1:2590): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(exo-helper-1:2590): atk-bridge-WARNING **: IOR not set.

(exo-helper-1:2590): atk-bridge-WARNING **: Could not locate registry

(Thunar:2591): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(Thunar:2591): atk-bridge-WARNING **: IOR not set.

(Thunar:2591): atk-bridge-WARNING **: Could not locate registry

(transmission-gtk:2608): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(transmission-gtk:2608): atk-bridge-WARNING **: IOR not set.

(transmission-gtk:2608): atk-bridge-WARNING **: Could not locate registry

(gedit:2619): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(gedit:2619): atk-bridge-WARNING **: IOR not set.

(gedit:2619): atk-bridge-WARNING **: Could not locate registry

(gedit:2625): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(gedit:2625): atk-bridge-WARNING **: IOR not set.

(gedit:2625): atk-bridge-WARNING **: Could not locate registry



"/etc/profile: 31: //: Permission denied"  looked weird to me, I checked permissions, didn't find any problem  (it's 755).  Any ideas?

---

