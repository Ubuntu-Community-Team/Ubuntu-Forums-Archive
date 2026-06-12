---
title: "Invalid command in configuration login file(SOLVED)"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by Dutch on 2005-11-15
Hi All,

When i login I get this message:
"The configuration file contains an invalid commansd line for the login dialog.So running the defaulty command please fix tourere configuration"
This happened direct afterthe upgrade.And it shows in a square direct over the inlog box

xsesion erors are:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "paul"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/Paul:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/Paul:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/Paul:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/Paul:/tmp/.ICE-unix/7008
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
manager.c/562: setting[0]: bool: autobrowse = 1
manager.c/562: setting[1]: bool: autoburn = 1
manager.c/557: setting[2]: string: autoburn_audio_cd_command = serpentine
manager.c/557: setting[3]: string: autoburn_photo_cd_command = nautilus --no-desktop burn:
manager.c/557: setting[4]: string: autoburn_data_cd_command = nautilus --no-desktop burn:
manager.c/562: setting[5]: bool: autoipod = 0
manager.c/557: setting[6]: string: autoipod_command = 
manager.c/562: setting[7]: bool: automount_drives = 1
manager.c/562: setting[8]: bool: automount_media = 1
manager.c/562: setting[9]: bool: autophoto = 1
manager.c/557: setting[10]: string: autophoto_command = gnome-volume-manager-gthumb %h
manager.c/562: setting[11]: bool: autoplay_cda = 1
manager.c/557: setting[12]: string: autoplay_cda_command = sound-juicer -d %d
manager.c/562: setting[13]: bool: autoplay_dvd = 1
manager.c/557: setting[14]: string: autoplay_dvd_command = totem %d
manager.c/562: setting[15]: bool: autoplay_vcd = 1
manager.c/557: setting[16]: string: autoplay_vcd_command = totem %d
manager.c/562: setting[17]: bool: autoprinter = 0
manager.c/557: setting[18]: string: autoprinter_command = gnome-cups-add hal://%h
manager.c/562: setting[19]: bool: autorun = 0
manager.c/557: setting[20]: string: autorun_path = .autorun:autorun:autorun.sh
manager.c/557: setting[21]: string: eject_command = /usr/bin/eject
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(totem:7134): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:7134): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

** (totem:7134): CRITICAL **: totem_pl_parser_parse: assertion `strstr (url, "://") != NULL' failed

** (gnome-session:7008): WARNING **: Host name lookup failure on localhost.
adding hook target 'source'

(evolution-2.2:7130): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(evolution-2.2:7130): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

** (gnome-cups-icon:7140): WARNING **: IPP request failed with status 1280

** (gnome-cups-icon:7140): WARNING **: IPP request failed with status 1280

** (gnome-cups-icon:7140): WARNING **: IPP request failed with status 1280

** (gnome-cups-icon:7140): WARNING **: IPP request failed with status 1280

report junk?? Please fill the form below

report junk?? They're beautiful
error: No OLE2 signature

(nautilus:7128): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: kan gedeeld objektbestand niet openen: Onbekend bestand of map)
BBDB spinning up...

(evolution-2.2:7130): GnomeCanvas-CRITICAL **: gnome_canvas_request_redraw: assertion `GNOME_IS_CANVAS (canvas)' failed

(evolution-2.2:7130): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(evolution-2.2:7130): GnomeCanvas-CRITICAL **: gnome_canvas_request_redraw: assertion `GNOME_IS_CANVAS (canvas)' failed
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default

(evolution-2.2:7130): GnomeCanvas-CRITICAL **: gnome_canvas_request_redraw: assertion `GNOME_IS_CANVAS (canvas)' failed

(evolution-2.2:7130): GnomeCanvas-CRITICAL **: gnome_canvas_request_redraw: assertion `GNOME_IS_CANVAS (canvas)' failed

report junk?? females date site

(evolution-2.2:7130): gtkhtml-CRITICAL **: html_engine_is_selection_active: assertion `!html_engine_get_editable (e) || e->mark' failed

(evolution-2.2:7130): gtkhtml-CRITICAL **: html_engine_is_selection_active: assertion `!html_engine_get_editable (e) || e->mark' failed

(evolution-2.2:7130): gtkhtml-CRITICAL **: html_engine_is_selection_active: assertion `!html_engine_get_editable (e) || e->mark' failed

(evolution-2.2:7130): gtkhtml-CRITICAL **: html_engine_is_selection_active: assertion `!html_engine_get_editable (e) || e->mark' failed
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default

(gnome-terminal:15640): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:15640): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
- using device default
- using device default
- using device default
- using device default
- using device default
- using device default

```

---

### Post by ubuntu_demon on 2005-11-15
This will configure all the packages that aren't configured properly yet :

$ sudo dpkg --configure -a

now reset 

if it didn't help. This will reconfigure all packages installed (takes a lot of time)
$ sudo dpkg-reconfigure -a

now reset

If you have still problems post your .xsession-errors again.

edit  :

the first command should be :
sudo dpkg **--**configure -a (instead of sudo dpkg -configure -a)

I guess you did already the second command. During postfix configuration configure it as local system only. configuring xserver-xorg you already did once (and I explained how to do it) so that shouldn't be a big problem.  I think for most (if not all) of the other questions you should just press enter.

---

### Post by Dutch on 2005-11-15
Oke thank u gave me the right first line through Gnome meeting.
With the second line I've got these warnings

```

Updating category type3..
Updating category gsfontderivative..
Updating category truetype..
Updating category cid..
Updating category cmap..
Updating category psprint..
Unregistering PostScript fonts...done.
(Re-)registering PostScript fonts...done.
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
 * Stopping HP Linux Printing and Imaging System                         [ ok ]
Creating/updating hplip user account...
 * Starting HP Linux Printing and Imaging System  

```

Is this something serious ?

---

### Post by ubuntu_demon on 2005-11-15
It's some kind of bug related to gstreamer. I haven't found much more useful information yet.

edit :
might be : [http://bugzilla.ubuntu.com/show_bug.cgi?id=16972](http://bugzilla.ubuntu.com/show_bug.cgi?id=16972)
or :
[http://bugzilla.ubuntu.com/show_bug.cgi?id=12362](http://bugzilla.ubuntu.com/show_bug.cgi?id=12362)

---

### Post by ubuntu_demon on 2005-11-15
because I wrote the first line wrong we went with the second command. This takes really long. ( I suggested it because of the apt-hell he had during upgrading)

$ sudo dpkg-reconfigure -a

After this remove your .xsession-errors,reboot,login  and post your .xsession-errors

Then we can solve the resulting errors if necessary (on IM I suggested xubuntu-desktop because your pc is quite slow)

---

### Post by Dutch on 2005-11-16
[QUOTE=ubuntu_demon]because I wrote the first line wrong we went with the second command. This takes really long. ( I suggested it because of the apt-hell he had during upgrading)

$ sudo dpkg-reconfigure -a

After this remove your .xsession-errors,reboot,login  and post your .xsession-errors

Then we can solve the resulting errors if necessary (on IM I suggested xubuntu-desktop because your pc is quite slow)[/QUOTE]

Hi goodmorning , well if u want tu use the ```
 sudo dpkg-reconfigure -a
``` be noticed that it takes LONG. With my PC Celeron 500 Mhz (256Mb) it took at least 8 hours.So quit your day job :-)

Oke after I started up again I made the error file empty and asked again:
 ```
gedit ~/.xsession-errors
```
(u do have to clean it first else u see the old erors)

Result ? No erors for Xsession !

But (why a but ?) with starting up I've got the same massage:
"The configuration file contains an invalid commansd line for the login dialog.So running the defaulty command please fix tourere configuration"


If I give the command:
```
 sudo dpkg --configure -a
``` it comes back with an empty line.

---

### Post by ubuntu_demon on 2005-11-16
tourere configuration ?

first clean the .xsession-errors file then login again and then look for any errors. If any post them.

---

### Post by Dutch on 2005-11-16
After cleaning the file I asked again for the x.session errors.
With this result:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "paul"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/Paul:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/Paul:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/Paul:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/Paul:/tmp/.ICE-unix/10538
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
manager.c/562: setting[0]: bool: autobrowse = 1
manager.c/562: setting[1]: bool: autoburn = 1
manager.c/557: setting[2]: string: autoburn_audio_cd_command = serpentine
manager.c/557: setting[3]: string: autoburn_photo_cd_command = nautilus --no-desktop burn:
manager.c/557: setting[4]: string: autoburn_data_cd_command = nautilus --no-desktop burn:
manager.c/562: setting[5]: bool: autoipod = 0
manager.c/557: setting[6]: string: autoipod_command = 
manager.c/562: setting[7]: bool: automount_drives = 1
manager.c/562: setting[8]: bool: automount_media = 1
manager.c/562: setting[9]: bool: autophoto = 1
manager.c/557: setting[10]: string: autophoto_command = gnome-volume-manager-gthumb %h
manager.c/562: setting[11]: bool: autoplay_cda = 1
manager.c/557: setting[12]: string: autoplay_cda_command = sound-juicer -d %d
manager.c/562: setting[13]: bool: autoplay_dvd = 1
manager.c/557: setting[14]: string: autoplay_dvd_command = totem %d
manager.c/562: setting[15]: bool: autoplay_vcd = 1
manager.c/557: setting[16]: string: autoplay_vcd_command = totem %d
manager.c/562: setting[17]: bool: autoprinter = 0
manager.c/557: setting[18]: string: autoprinter_command = gnome-cups-add hal://%h
manager.c/562: setting[19]: bool: autorun = 0
manager.c/557: setting[20]: string: autorun_path = .autorun:autorun:autorun.sh
manager.c/557: setting[21]: string: eject_command = /usr/bin/eject
manager.c/2082: mount_all: mounting /dev/hdc
manager.c/1258: mounting /org/freedesktop/Hal/devices/volume_label_...
manager.c/696: executing command: /usr/bin/pmount-hal /org/freedesktop/Hal/devices/volume_label_
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Error: could not execute pmount
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

** (gnome-session:10538): WARNING **: Host name lookup failure on localhost.

(totem:10666): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:10666): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

** (totem:10666): CRITICAL **: totem_pl_parser_parse: assertion `strstr (url, "://") != NULL' failed
adding hook target 'source'

(evolution-2.2:10662): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(evolution-2.2:10662): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

** (nautilus:10655): WARNING **: No description found for mime type "x-special/socket" (file is ".gnome-system-monitor.paul"), please tell the gnome-vfs mailing list.

(gnome-terminal:10904): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:10904): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
selected locale: nl-NL
 ***** Registering: Clean Compreg! ****
observe: 
nothing here: null
DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 observe called
FILE: [xpconnect wrapped nsIFile]*** nsExtensionManager::_disableObsoleteExtensions - failure, catching exception so finalize window can close
*** loading the extensions datasource
*** ExtensionManager:_updateManifests: no access privileges to application directory, skipping.
 ***** Registering: Clean Compreg! ****
observe: 
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 *** loading the extensions datasource
*** ExtensionManager:_updateManifests: no access privileges to application directory, skipping.
selected locale: nl-NL
observe: 
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 
** (nautilus:10655): WARNING **: No description found for mime type "application/x-dbm" (file is "cert8.db"), please tell the gnome-vfs mailing list.
selected locale: nl-NL
observe: 
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 - using device default
- using device default

(evolution-2.2:10662): gtkhtml-CRITICAL **: html_engine_is_selection_active: assertion `!html_engine_get_editable (e) || e->mark' failed

(evolution-2.2:10662): gtkhtml-CRITICAL **: html_engine_is_selection_active: assertion `!html_engine_get_editable (e) || e->mark' failed

(evolution-2.2:10662): gtkhtml-CRITICAL **: html_engine_is_selection_active: assertion `!html_engine_get_editable (e) || e->mark' failed

(evolution-2.2:10662): gtkhtml-CRITICAL **: html_engine_is_selection_active: assertion `!html_engine_get_editable (e) || e->mark' failed

(evolution-2.2:10662): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(abiword:13833): GnomePrint-WARNING **: Could not create filter from description 'frgba': filter 'frgba' is unknown

(abiword:13833): GnomePrintCupsPlugin-WARNING **: iconv does not support ppd character encoding: ISOLatin1, trying CSISOLatin1

** (abiword:13833): WARNING **: Could not find child for option "PhysicalSize" with id "Custom"

** (abiword:13833): WARNING **: Could not set value of "PhysicalSize" to "Custom"

(abiword:13833): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(abiword:13833): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
BBDB spinning up...

** (abiword:13833): WARNING **: Could not find child for option "PhysicalSize" with id "Custom"

** (abiword:13833): WARNING **: Could not set value of "PhysicalSize" to "Custom"

(abiword:13833): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(abiword:13833): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (abiword:13833): WARNING **: Could not find child for option "PhysicalSize" with id "Custom"

** (abiword:13833): WARNING **: Could not set value of "PhysicalSize" to "Custom"

(abiword:13833): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(abiword:13833): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
- using device default
- using device default

(evolution-2.2:10662): gtkhtml-WARNING **: Onbekend bestand of map

(evolution-2.2:10662): gtkhtml-WARNING **: Onbekend bestand of map
restoring draft flag 'text/html'
restoring draft flag 'text/html'
Model not found, discarding config

(evolution-2.2:10662): GnomePrint-WARNING **: Could not create filter from description 'frgba': filter 'frgba' is unknown

(evolution-2.2:10662): GnomePrintCupsPlugin-WARNING **: iconv does not support ppd character encoding: ISOLatin1, trying CSISOLatin1

```

Mmm tonight I'm working so I'll speak to you tomorrow.

Thanks.

---

### Post by ubuntu_demon on 2005-11-17
still a lot of errors :(

We can try to solve all errors. But since you wanna try xfce4 / xubuntu-desktop any way I suggest that you try that one first and see whether you'll like it.

$sudo apt-get install xubuntu-desktop

now clear your .xsession-errors

log out

start a xfce4 session (from sessions in the login screen)

give us your .xsession-errors again (right after logging in)

If you don't like xfce4 we are going to solve the xsession-errors (when starting gnome) if you want. (we are going to search for them on ubuntuforums and google , maybe even on the wiki,bugzilla and lauchnpad)

---

### Post by jdgiotta on 2005-11-18
Did this ever get resolved?

I'm getting similar errors! *eek

---

### Post by ubuntu_demon on 2005-11-18
[QUOTE=jdgiotta]Did this ever get resolved?

I'm getting similar errors! *eek[/QUOTE]
We haven't solved the errors yet.

I recommend you try the same things I suggested except the 
"sudo dpkg-reconfigure -a" because that one took too much time and didn't help much. 

Also please start a new thread and PM me the url and keep watching this thread. Unless your .xsession-errors resembles the one of Dutch very closely. In that case please post your .xsession-errors here.

---

### Post by Dutch on 2005-11-19
Oke, I started Gnomeup and then choose for XFCE.
I've got this listing with problems after ```
gedit .xsession-errors
```

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "paul"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/Paul:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/Paul:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/Paul:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (xfwm4:7224): WARNING **: The display does not support the XComposite extension.

** (xfwm4:7224): WARNING **: Compositing manager disabled.
xscreensaver: 12:38:46: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:38:46: 0: for window 0x600001 (xscreensaver)
xscreensaver: 12:38:54: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:38:54: 0: for window 0x600001 (xscreensaver)
xscreensaver: 12:39:03: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:39:03: 0: for window 0x600001 (xscreensaver)

(totem:7232): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:7232): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

** (totem:7232): CRITICAL **: totem_pl_parser_parse: assertion `strstr (url, "://") != NULL' failed
adding hook target 'source'
evolution-alarm-notify-Message: Setting timeout for 40844 1132441200 1132400356
evolution-alarm-notify-Message:  Sun Nov 20 00:00:00 2005

evolution-alarm-notify-Message:  Sat Nov 19 12:39:16 2005

evolution-alarm-notify-Message: Loading file:///home/paul/.evolution/calendar/local/system
evolution-alarm-notify-Message: Loading contacts:///
evolution-alarm-notify-Message: Loading file:///home/paul/.evolution/tasks/local/system
evolution-alarm-notify-Message: alarm-notify.c:176: Could not get the list of sources to load
evolution-alarm-notify-Message: Loading alarms for today
evolution-alarm-notify-Message: Loading alarms for today
evolution-alarm-notify-Message: Loading alarms for today
env: firefox-bin: Onbekend bestand of map
xscreensaver: 12:39:20: 0: unrecognised ClientMessage "_NET_CURRENT_DESKTOP" received
xscreensaver: 12:39:20: 0: for window 0x40 (root)

(evolution-2.4:7238): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(gnome-terminal:7265): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:7265): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(xftaskbar4:7226): libxfcegui4-WARNING **: tray icon has requested a size of (1 x 1), resizing to (24 x 24)
xscreensaver: 12:39:30: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:39:30: 0: for window 0x600001 (xscreensaver)
xscreensaver: 12:39:30: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:39:30: 0: for window 0x600001 (xscreensaver)

(evolution-2.4:7238): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed
xscreensaver: 12:40:20: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 12:40:20: 0: for window 0x1c00189 (gaim / Gaim)
xscreensaver: 12:43:27: 0: unrecognised ClientMessage "_NET_CURRENT_DESKTOP" received
xscreensaver: 12:43:27: 0: for window 0x40 (root)
xscreensaver: 12:43:28: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 12:43:28: 0: for window 0x1c006d9 (gaim / Gaim)
xscreensaver: 12:47:00: 0: unrecognised ClientMessage "_NET_CURRENT_DESKTOP" received
xscreensaver: 12:47:00: 0: for window 0x40 (root)
xscreensaver: 12:47:02: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:47:02: 0: for window 0x600001 (xscreensaver)

(gnome-terminal:7265): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:7265): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
xscreensaver: 12:47:12: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:47:12: 0: for window 0x600001 (xscreensaver)

```

And I stil got the message with the login screen that there is an invalid command in the inlog.I get the message:
```

The configuration file contains an invalid command line for the login dialog, so running the default command please fix youre configuration 
```

And I'm NOT happy with this.
Anm invalid command in the inlog screen ? 
Does that mean that everybode can now login my system ?

---

### Post by ubuntu_demon on 2005-11-19
[QUOTE=Dutch]Oke, I started Gnomeup and then choose for XFCE.
I've got this listing with problems after ```
gedit .xsession-errors
```
[/QUOTE]

The way I wanted you to post your .xsession-errors was like this :
remove the .xsession-errors , log out of gnome,log into xfce4 and provide this .xsession-errors right after logging in 

But it doesn't matter anymore because I probably solved your problem. See below.

[QUOTE=Dutch]
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "paul"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/Paul:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/Paul:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/Paul:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (xfwm4:7224): WARNING **: The display does not support the XComposite extension.

** (xfwm4:7224): WARNING **: Compositing manager disabled.
xscreensaver: 12:38:46: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:38:46: 0: for window 0x600001 (xscreensaver)
xscreensaver: 12:38:54: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:38:54: 0: for window 0x600001 (xscreensaver)
xscreensaver: 12:39:03: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:39:03: 0: for window 0x600001 (xscreensaver)

(totem:7232): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:7232): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

** (totem:7232): CRITICAL **: totem_pl_parser_parse: assertion `strstr (url, "://") != NULL' failed
adding hook target 'source'
evolution-alarm-notify-Message: Setting timeout for 40844 1132441200 1132400356
evolution-alarm-notify-Message:  Sun Nov 20 00:00:00 2005

evolution-alarm-notify-Message:  Sat Nov 19 12:39:16 2005

evolution-alarm-notify-Message: Loading file:///home/paul/.evolution/calendar/local/system
evolution-alarm-notify-Message: Loading contacts:///
evolution-alarm-notify-Message: Loading file:///home/paul/.evolution/tasks/local/system
evolution-alarm-notify-Message: alarm-notify.c:176: Could not get the list of sources to load
evolution-alarm-notify-Message: Loading alarms for today
evolution-alarm-notify-Message: Loading alarms for today
evolution-alarm-notify-Message: Loading alarms for today
env: firefox-bin: Onbekend bestand of map
xscreensaver: 12:39:20: 0: unrecognised ClientMessage "_NET_CURRENT_DESKTOP" received
xscreensaver: 12:39:20: 0: for window 0x40 (root)

(evolution-2.4:7238): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(gnome-terminal:7265): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:7265): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(xftaskbar4:7226): libxfcegui4-WARNING **: tray icon has requested a size of (1 x 1), resizing to (24 x 24)
xscreensaver: 12:39:30: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:39:30: 0: for window 0x600001 (xscreensaver)
xscreensaver: 12:39:30: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:39:30: 0: for window 0x600001 (xscreensaver)

(evolution-2.4:7238): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed
xscreensaver: 12:40:20: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 12:40:20: 0: for window 0x1c00189 (gaim / Gaim)
xscreensaver: 12:43:27: 0: unrecognised ClientMessage "_NET_CURRENT_DESKTOP" received
xscreensaver: 12:43:27: 0: for window 0x40 (root)
xscreensaver: 12:43:28: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 12:43:28: 0: for window 0x1c006d9 (gaim / Gaim)
xscreensaver: 12:47:00: 0: unrecognised ClientMessage "_NET_CURRENT_DESKTOP" received
xscreensaver: 12:47:00: 0: for window 0x40 (root)
xscreensaver: 12:47:02: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:47:02: 0: for window 0x600001 (xscreensaver)

(gnome-terminal:7265): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:7265): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
xscreensaver: 12:47:12: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:47:12: 0: for window 0x600001 (xscreensaver)

```
[/QUOTE]

It's normal to have some .xsession-errors. There's debugging stuff and non-critical warnings there too. Posting it can help us find the problem. But this problem isn't related to your .xsession-errors see below.

[QUOTE=Dutch]
And I stil got the message with the login screen that there is an invalid command in the inlog.I get the message:

```

The configuration file contains an invalid command line for the login dialog, so running the default command please fix youre configuration 
```

And I'm NOT happy with this.
Anm invalid command in the inlog screen ? 
Does that mean that everybode can now login my system ?[/QUOTE]

I thought you got the error right after logging into gnome. But it's a gdm error. We are getting really good with miscommunicating :-P

No it doesn't mean everybody can now login into your system. It probably means there is some gdm configuration file (gdm.conf most likely) which didn't get overwritten with the breezy version (maybe because you editted it).

So I probably got the solution for you. Go to ctrl-alt-f1. And type this :

$ sudo /etc/init.d/gdm stop
$ sudo apt-get remove gdm --purge
$ sudo apt-get install gdm ubuntu-desktop xubuntu-desktop
$ sudo /etc/init.d/gdm start

It's a reasonable thing to do. As it makes sure you get the breezy gdm.conf properly set up. Also this helped other people solve the same login error (I searched the forums for "gdm login error").

---

### Post by Dutch on 2005-11-19
Alright Thanks.
I got now my old inlog screen back from the 5.04 but thats no problem 

The warning is gone with the inlogscreen.

Can u edit the lead of the post with SOLVED ?

Many thanks !

---

### Post by ubuntu_demon on 2005-11-19
done.

You can choose a different login screen in gnome here : system->administration->login screen setup

or here : $ sudo gdmsetup

---

