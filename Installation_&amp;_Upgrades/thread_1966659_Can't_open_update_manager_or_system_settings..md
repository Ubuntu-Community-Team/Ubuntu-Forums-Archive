---
title: "Can't open update manager or system settings."
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Howie Williams on 2012-04-27
Upgraded from 11.10 to 12.04 had some problems re partial upgrade. So did sudo apt-get update sudo apt-get upgrade all seemed O.K. Checked version in terminal 12.04 fine.When I try to open update manager or system settings nothing happens apart from update manager window flashes up for a split second.

---

### Post by cortman on 2012-04-27
Run it from the terminal, i.e.,

```
gksu update-manager
```

Post anything that appears in the terminal window. These could be errors that would tell us what's wrong.

---

### Post by Howie Williams on 2012-04-27
Some recommended updates and tons of distro updates but can't check boxes.Not all updates can be installed.Partial upgrade or close.
Plus this in terminal after trying to check boxes:-

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:225:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:504:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:524:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:532:25: Unknown pseudo-class 'only-child'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:609:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:614:21: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:841:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:887:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:906:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:919:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1106:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1301:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1402:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1552:21: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1753:22: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1813:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1940:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2074:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2134:24: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2184:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2191:22: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2205:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2221:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:4:18: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:10:18: 'inherit' is not a valid color name

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:17:22: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:22:17: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:25:35: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:28:29: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:31:16: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:34:28: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:37:19: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:48:15: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:55:22: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:67:29: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:80:20: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:105:22: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:126:23: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:144:29: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:162:28: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:181:24: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:200:30: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:213:31: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:226:37: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:239:36: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:244:23: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:263:35: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:284:34: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:304:25: Unknown pseudo-class 'only-child'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:324:14: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:330:23: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:333:18: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:336:24: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:339:21: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:356:28: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:379:15: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:384:15: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:390:22: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:426:28: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:457:27: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:467:34: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:489:30: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:500:30: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:517:36: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:531:46: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:538:43: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:551:15: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:567:24: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:574:23: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:582:27: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:593:44: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:601:18: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:607:15: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:613:39: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:635:20: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:646:14: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:649:17: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:652:18: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:655:15: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:661:17: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:669:18: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:673:29: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:676:22: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:682:30: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:704:32: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:718:42: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:731:44: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:744:16: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:758:25: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:768:24: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:772:30: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:776:36: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:780:33: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:784:39: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:788:45: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:792:22: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:798:32: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:804:19: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:810:27: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:817:37: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:824:39: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:831:49: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:838:28: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:841:37: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:848:17: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:852:30: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:856:24: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:862:34: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:870:50: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:878:27: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:891:20: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:898:22: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:907:21: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:913:18: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:922:25: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:938:32: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:954:37: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:970:25: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:983:37: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:992:20: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:999:17: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1004:25: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1022:38: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1026:37: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1052:41: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1056:41: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1077:60: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1084:60: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1101:40: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1116:46: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1129:52: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1142:45: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1152:52: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1162:32: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1175:32: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1184:44: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1191:40: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1199:46: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1211:32: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1224:48: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1231:40: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1251:49: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1261:54: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1275:57: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1282:56: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1293:27: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1299:26: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gedit.css:12:33: 'transparent' is not a valid color name

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gedit.css:18:34: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gedit.css:23:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gedit.css:28:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: gedit.css:33:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: nautilus.css:8:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: nautilus.css:57:30: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: nautilus.css:80:32: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: nautilus.css:92:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: nautilus.css:114:32: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: nautilus.css:125:45: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: nautilus.css:148:39: Unknown pseudo-class 'backdrop'

(update-manager:2490): Gtk-WARNING **: Theme parsing error: unity-greeter.css:5:20: Junk at end of value

(update-manager:2490): Gtk-WARNING **: Theme parsing error: unity-greeter.css:35:20: Junk at end of value

(update-manager:2490): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:2490): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:2490): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:2490): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:2490): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:2490): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

---

### Post by cortman on 2012-04-27
Try

```
sudo apt-get upgrade -d
```

Partial upgrades are usually very bad news...

---

### Post by Howie Williams on 2012-04-27
The following packages have been kept back:
  aisleriot akonadi-backend-mysql akonadi-server apt apt-transport-https
  apt-utils at-spi banshee banshee-extension-soundmenu baobab bind9-host
  brasero brasero-cdrkit brasero-common brltty brltty-x11 c2esp cheese
  cheese-common compiz compiz-core compiz-gnome compiz-plugins
  compiz-plugins-default compiz-plugins-main compiz-plugins-main-default
  compizconfig-backend-gconf cups cups-driver-gutenprint
  dconf-gsettings-backend deja-dup dnsmasq-base dnsutils empathy
  empathy-common eog espeak espeak-data evince evince-common evolution
  evolution-common evolution-data-server evolution-data-server-common
  evolution-indicator evolution-plugins evolution-webcal exiv2 ffmpeg
  file-roller foo2zjs foomatic-db-compressed-ppds fuse-utils
  gconf-defaults-service gconf-editor gconf2 gconf2-common gdm gedit
  gedit-common geoclue gettext gir1.2-appindicator-0.1
  gir1.2-appindicator3-0.1 gir1.2-gconf-2.0 gir1.2-gdkpixbuf-2.0
  gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0 gir1.2-gtksource-3.0
  gir1.2-soup-2.4 gir1.2-totem-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0
  glib-networking gnome-bluetooth gnome-control-center
  gnome-control-center-data gnome-desktop-data gnome-desktop3-data
  gnome-disk-utility gnome-media gnome-online-accounts gnome-orca
  gnome-power-manager gnome-search-tool gnome-session gnome-session-bin
  gnome-session-common gnome-settings-daemon gnome-sudoku gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-user-share gnomine
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
  gucharmap gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber gwibber-service
  hpijs hplip hplip-cups hplip-data ibus indicator-application
  indicator-appmenu indicator-datetime indicator-messages indicator-power
  indicator-session indicator-sound katepart kde-runtime kdelibs-bin
  kdelibs5-data kdelibs5-plugins kdepim-runtime kdepimlibs-kio-plugins
  kdoctools kexi kolourpaint4 krita kspread libakonadi-contact4
  libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4
  libakonadiprotocolinternals1 libalgorithm-diff-xs-perl libapparmor-perl
  libappindicator1 libappindicator3-1 libapt-pkg-perl libatk-adaptor
  libavcodec-extra-53 libavdevice53 libavfilter2 libavformat-extra-53
  libavutil-extra-51 libbrasero-media3-1 libcairo-perl libcamel-1.2-29
  libcanberra-gtk3-module libcap2-bin libclutter-1.0-0 libclutter-gst-1.0-0
  libclutter-gtk-1.0-0 libcompizconfig0 libcrypt-ssleay-perl libcups2 libcurl3
  libcurl3-gnutls libdecoration0 libebackend-1.2-1 libedata-book-1.2-11
  libedata-cal-1.2-13 libedataserverui-3.0-1 libenchant1c2a libespeak1
  libevince3-3 libevolution libfolks-telepathy25 libfolks25 libfuse2
  libgail-3-0 libgconf2-4 libgcr-3-1 libgdata13 libgdk-pixbuf2.0-0
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglib-perl libglib2.0-cil
  libgnome-desktop-3-2 libgnome-keyring0 libgnomeui-0 libgoa-1.0-0
  libgssapi-krb5-2 libgtk-3-0 libgtk-3-bin libgtk2-perl libgtk2.0-cil
  libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0
  libgtkmm-3.0-1 libgtksourceview-3.0-0 libgtksourceview-3.0-common
  libgucharmap-2-90-7 libgweather-3-0 libgwibber-gtk2 libgwibber2 libhpmud0
  libhtml-parser-perl libidl0 libindicate5 libio-pty-perl
  libio-socket-ssl-perl libjpeg8 libk5crypto3 libkabc4 libkatepartinterfaces4
  libkcal4 libkcalcore4 libkcalutils4 libkcmutils4 libkdcraw20 libkde3support4
  libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4
  libkfile4 libkhtml5 libkidletime4 libkimap4 libkio5 libkjsapi4 libkjsembed4
  libkldap4 libkmbox4 libkmediaplayer4 libkmime4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkpimidentities4 libkpimtextedit4
  libkpimutils4 libkprintutils4 libkpty4 libkrb5-3 libkrb5support0
  libkresources4 libkrosscore4 libkrossui4 libktexteditor4 libldap-2.4-2
  liblocale-gettext-perl liblockfile1 libmailtransport4 libmicroblog4
  libmission-control-plugins0 libmx-1.0-2 libnepomuk4 libnepomukquery4a
  libnepomukutils4 libnet-dbus-perl libnet-dns-perl libnet-ssleay-perl
  libnice10 libnm-gtk0 liboauth0 liboverlay-scrollbar3-0.2-0 libpango-perl
  libplasma3 libpoppler-qt4-3 libpostproc52 libpq5 libpstoedit0c2a libpurple0
  libqapt-runtime libqapt1 libqt4-dbus libqt4-declarative libqt4-designer
  libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-svg libqt4-xml libqt4-xmlpatterns libqtcore4
  libqtdee2 libqtgui4 libqtshiva0.1 libqtwebkit4 libreoffice-base-core
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-help-en-gb
  libreoffice-help-en-us libreoffice-impress libreoffice-l10n-en-gb
  libreoffice-l10n-en-za libreoffice-math libreoffice-writer librpc-xml-perl
  libsane libsane-hpaio libsdl1.2debian libsmbclient libsnmp15 libsolid4
  libsoprano4 libsoup2.4-1 libssl1.0.0 libstreamanalyzer0 libstreams0
  libsub-name-perl libswscale2 libsyncdaemon-1.0-1 libterm-readkey-perl
  libtext-charwidth-perl libtext-iconv-perl libthreadweaver4
  libtotem-plparser17 libunicode-string-perl libunity-2d-private0 libuuid-perl
  libv4l-0 libvcdinfo0 libvlc5 libvte-2.90-9 libvte-common libvte9
  libwebkitgtk-1.0-0 libwebkitgtk-3.0-0 libwildmidi1 libxfixes3
  libxml-libxml-perl libxml-parser-perl libxml-sax-perl libyelp0 lintian
  linux-generic linux-headers-generic linux-image-generic metacity min12xxw
  mysql-common nautilus nautilus-data nautilus-sendto-empathy nautilus-share
  network-manager network-manager-gnome ntfs-3g ntrack-module-libnl-0
  nvidia-current odbcinst1debian2 openssh-client openssl perl perl-base
  perl-modules plasma-scriptengine-javascript pnm2ppa poppler-utils
  ptouch-driver pulseaudio-module-gconf pulseaudio-module-gconf-dbg
  pulseaudio-utils pxljr python-appindicator python-apt python-dbus
  python-gnomekeyring python-gobject python-ibus python-indicate
  python-libproxy python-pycurl python-ubuntuone-client
  python-ubuntuone-control-panel python-uno python-vte qdbus qt-at-spi
  rastertosag-gdi samba-common samba-common-bin seahorse sessioninstaller
  shotwell smbclient software-center soprano-daemon sound-juicer splix
  synaptic telepathy-indicator telepathy-mission-control-5 thunderbird
  thunderbird-globalmenu thunderbird-gnome-support tomboy totem totem-common
  totem-mozilla totem-plugins transmission-common transmission-gtk
  ttf-kacst-one ttf-khmeros-core ttf-lao ttf-liberation ttf-opensymbol
  ttf-takao-pgothic ttf-thai-tlwg ttf-unfonts-core ubuntu-desktop
  ubuntu-minimal ubuntu-sso-client ubuntu-wallpapers ubuntuone-client
  ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-control-panel-gtk
  udisks unity unity-2d unity-2d-launcher unity-2d-panel unity-2d-places
  unity-2d-spread unity-common unity-greeter unity-lens-applications
  unity-lens-files unity-lens-music unity-scope-musicstores unity-services
  update-manager update-manager-core usb-creator-common usb-creator-gtk vino
  vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse wireless-crda
  wpasupplicant xdiagnose xorg xserver-xorg xserver-xorg-core
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware
  xserver-xorg-video-voodoo xz-utils yelp zeitgeist zeitgeist-core
0 upgraded, 0 newly installed, 0 to remove and 496 not upgraded.

---

### Post by cortman on 2012-04-27
Sorry, memory failed me there- I think I gave the wrong command. Do you get any errors from

```
sudo apt-get dist-upgrade
```

---

### Post by rdenatale on 2012-04-27
I'm having a similar problem, I think.

When I installed 11.10 IIRC it told me something about unity not being supported on my hardware.  I've been running gnome ever since, and if I try to login with an ubuntu session it fails.

Now when run the update manager it tells me about 12.04.  When I ask it to upgrade it downloads the update-manager but then appears to stop doing anything else.

I found this thread, and saw the advice to run the update manager in a shell.  Here's what I see when I do that:

rick@frodo:~$ gksu update-manager
authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg' 
extracting 'precise.tar.gz'
can't load DistUpgradeViewGtk (No module named vte)
can't load DistUpgradeViewGtk3 (could not import gobject (error was: ImportError('When using gi.repository you must not import static modules like "gobject". Please change all occurrences of "import gobject" to "from gi.repository import GObject".',)))
can't load DistUpgradeViewKDE (No module named PyQt4.QtCore)
Must be connected to a terminal.

What now?

---

### Post by cortman on 2012-04-27
> **rdenatale said:**
> I'm having a similar problem, I think.

When I installed 11.10 IIRC it told me something about unity not being supported on my hardware.  I've been running gnome ever since, and if I try to login with an ubuntu session it fails.

Now when run the update manager it tells me about 12.04.  When I ask it to upgrade it downloads the update-manager but then appears to stop doing anything else.

I found this thread, and saw the advice to run the update manager in a shell.  Here's what I see when I do that:

rick@frodo:~$ gksu update-manager
authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg' 
extracting 'precise.tar.gz'
can't load DistUpgradeViewGtk (No module named vte)
can't load DistUpgradeViewGtk3 (could not import gobject (error was: ImportError('When using gi.repository you must not import static modules like "gobject". Please change all occurrences of "import gobject" to "from gi.repository import GObject".',)))
can't load DistUpgradeViewKDE (No module named PyQt4.QtCore)
Must be connected to a terminal.

What now?

Looks odd. 
Your best bet may be a fresh installation, but at any rate, I'd recommend starting a new thread with your problem- keep things from getting confusing on this thread. Good luck!

---

### Post by Howie Williams on 2012-04-28
Upgrade stopped with error messsage "The software on this computer is up to date"> **cortman said:**
> Sorry, memory failed me there- I think I gave the wrong command. Do you get any errors from

```
sudo apt-get dist-upgrade
```

Seemed to run upgrade replacing missing files etc. Ran for approx. 30mins. Then terminal shut down and am now left with just the (Purple) ubuntu desk top with the cursor but no icons or launchpad dash.Also noticed as I move cursor from centre to left of screen it gets smaller.
Rebooted as nothing was happening. Booted O.K. could open Update-manager.Asked if I wanted run partial upgrade clicked yes. Distro upgrade window opened and started, then got crash report that ubuntu one shut down and also that ubuntu 12.04 had stopped working. Yet partial upgrade continued in terminal.
Upgrade stopped with message window with no entry sign "The software on this computer is up to date" "There are no upgrades available for your system. The upgrade will now be cancelled"
Sorry for editing all the time but seems best way to update you. O.K. yet another reboot and all looks fine except for 1 update. Under Distro Updates (Box checked) > store music lens for unity (can't check box). Presume this is for buying music from music stores? if so it's not a problem for me,but surly it should be able to be updated?
All seems fine now. Thank you cortman wherever you are!!!!

---

