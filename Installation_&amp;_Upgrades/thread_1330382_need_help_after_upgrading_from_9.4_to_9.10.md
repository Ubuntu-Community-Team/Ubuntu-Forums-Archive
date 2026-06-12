---
title: "need help after upgrading from 9.4 to 9.10"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by unix1adm on 2009-11-18
All i can say is that this upgrade was messy and not as easy as one would hope. I still have issue with my wireless not working. I have to turn it off and on  then log out and back in every tim eI shut my Laptop down. My track pad wont work now. 

My main users id is hozed big time. I cannot login with it except under safe mode. Something with the xserver got messed up. Here s my log may be some can point me in the right direction. 

Ive been fighting with this for since last Friday. 

Well the file is to big so I am not sure how i can post it.

---

### Post by unix1adm on 2009-11-18
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
E: main.c: Daemon startup failed.
gnome-session[4349]: WARNING: Could not parse desktop file /home/cj454/.config/autostart/drapes.desktop: Key file does not have key 'Type'
gnome-session[4349]: WARNING: could not read /home/cj454/.config/autostart/drapes.desktop

(gnome-settings-daemon:4421): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:4421): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.

** (gnome-settings-daemon:4421): WARNING **: Connection failed, reconnecting...
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
Unable to find a synaptics device.
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
** (gnome-panel:4443): DEBUG: Adding applet 0.
** (gnome-panel:4443): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:4443): DEBUG: Adding applet 1.
** (gnome-panel:4443): DEBUG: Adding applet 2.

(gnome-panel:4443): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -12 and height 24
** (gnome-panel:4443): DEBUG: Adding applet 3.
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: /usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
** (gnome-panel:4443): DEBUG: Adding applet 4.
** (gnome-panel:4443): DEBUG: Adding applet 5.
** (gnome-panel:4443): DEBUG: Adding applet 6.
Failed to play sound: Not available
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
** (gnome-panel:4443): DEBUG: Adding applet 7.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
** (gnome-panel:4443): DEBUG: Adding applet 8.
** (gnome-panel:4443): DEBUG: Adding applet 9.

(polkit-gnome-authentication-agent-1:4480): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:4480): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

** (gnome-volume-control-applet:4455): WARNING **: Connection failed, reconnecting...
** (gnome-panel:4443): DEBUG: Adding applet 10.
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
** (gnome-panel:4443): DEBUG: Adding applet 11.
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
** (gnome-panel:4443): DEBUG: Adding applet 12.
** (gnome-panel:4443): DEBUG: Adding applet 13.
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: ** (gnome-panel:4443): DEBUG: Adding applet 14.
Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
** (gnome-panel:4443): DEBUG: Adding applet 15.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
Initializing trackerd...
Tracker-Message: Checking XDG_DATA_HOME is writable and exists
Tracker-Message:   XDG_DATA_HOME is '(null)'
Tracker-Message:   XDG_DATA_HOME set to '/home/cj454/.local/share'
Tracker-Message:   Path is OK
Tracker-Message: Setting IO priority
Tracker-Message: Setting up monitor for changes to config file:'/home/cj454/.config/tracker/tracker.cfg'
Connection failure: Connection refused
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
gnome-session[4349]: WARNING: Could not launch application '1090c95075aa3a80a2124454523542834600000055790027.desktop': Unable to start application: Failed to execute child process "fast-user-switch-applet" (No such file or directory)
gnome-session[4349]: WARNING: Could not launch application '108540a19679a9741512434363068193000000054250011.desktop': Unable to start application: Failed to execute child process "/usr/lib/evolution/2.26/evolution-alarm-notify" (No such file or directory)
gnome-session[4349]: WARNING: Could not launch application '1090c95075aa3a80a21244545219600800000055790002.desktop': Unable to start application: Failed to execute child process "Drapes" (No such file or directory)
Failed to init the UI: Unknown option --sm-config-prefix
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
gnome-session[4349]: WARNING: Could not launch application '1090c95075aa3a80a2124454523345297200000055790026.desktop': Unable to start application: Failed to execute child process "evolution-exchange-storage" (No such file or directory)

(nautilus:4448): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
Tracker-Message: Loading defaults into GKeyFile...
Tracker-Message: Legacy config option 'IndexEvolutionEmails' found
Tracker-Message:   This option has been replaced by 'DisabledModules'
Tracker-Message:   Option 'DisabledModules' removed 'evolution'
Tracker-Message: Legacy config option 'IndexThunderbirdEmails' found
Tracker-Message:   This option is no longer supported and has no effect
Tracker-Message: Legacy config option 'SkipMountPoints' found
Tracker-Message:   Option 'IndexMountedDirectories' set to true
Tracker-Message: Setting up stopword list for language code:'en'
Tracker-Message: Setting up stemmer for language code:'en'
Tracker-Message: Checking directory exists:'/home/cj454/.local/share/tracker/data'
Tracker-Message: Checking directory exists:'/home/cj454/.cache/tracker'
Tracker-Message: Registering DBus service...
  Name:'org.freedesktop.Tracker'
Starting log:
  File:'/home/cj454/.local/share/tracker/trackerd.log'
*** ERROR ***
TI:15:29:28	TH:0x9d69168	FI:gpm-main.c	FN:main,250
 - Power Manager is already running in this session.
Traceback:
	gnome-power-manager [0x80649bb]
	gnome-power-manager [0x80574e2]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xb75b3b56]
	gnome-power-manager [0x804e971]
Initializing nautilus-gdu extension

** (nautilus:4448): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4448): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:4448): WARNING **: No marshaller for signature of signal 'ShareCreateError'
** (gnome-panel:4443): DEBUG: Adding applet 16.
** (gnome-panel:4443): DEBUG: Adding applet 17.
** (gnome-panel:4443): DEBUG: Adding applet 18.
** (gnome-panel:4443): DEBUG: Adding applet 19.

** (gnome-settings-daemon:4421): WARNING **: Connection failed, reconnecting...
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.

(nautilus:4553): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: schro_virt_frame_new_vert_downsample

** (gnome-volume-control-applet:4455): WARNING **: Connection failed, reconnecting...
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

** (gnome-settings-daemon:4421): WARNING **: Connection failed, reconnecting...

** (gnome-volume-control-applet:4455): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:4421): WARNING **: Connection failed, reconnecting...

** (gnome-volume-control-applet:4455): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:4421): WARNING **: Connection failed, reconnecting...

** (gnome-volume-control-applet:4455): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:4421): WARNING **: Connection failed, reconnecting...

** (gnome-volume-control-applet:4455): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:4421): WARNING **: Connection failed, reconnecting...

** (gnome-volume-control-applet:4455): WARNING **: Connection failed, reconnecting...
/usr/share/themes/infinity/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/infinity/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/infinity/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
evolution-alarm-notify-Message: Setting timeout for 30603 1258434000 1258403397
evolution-alarm-notify-Message:  Tue Nov 17 00:00:00 2009

evolution-alarm-notify-Message:  Mon Nov 16 15:29:57 2009


** (gnome-settings-daemon:4421): WARNING **: Connection failed, reconnecting...

** (gnome-volume-control-applet:4455): WARNING **: Connection failed, reconnecting...
gnome-session[4349]: WARNING: Detected that screensaver has left the bus
gnome-session: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(nautilus:4448): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.23 of volume monitor org.gtk.Private.GduVolumeMonitor disconnected from the bus; removing drives/volumes/mounts
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Drapes: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Reading symbols from /usr/bin/compiz.real...(no debugging symbols found)...done.
Attaching to program: /usr/bin/compiz.real, process 4434
Reading symbols from /usr/lib/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXinerama.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libXcursor.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/libICE.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libxslt.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libstartup-notification-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/libGL.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGL.so.1
Reading symbols from /lib/tls/i686/cmov/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /lib/tls/i686/cmov/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /usr/lib/libX11.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libXrender.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /lib/libuuid.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libuuid.so.1
Reading symbols from /lib/libz.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libz.so.1
Reading symbols from /usr/lib/libxcb-aux.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-aux.so.0
Reading symbols from /usr/lib/libxcb-event.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-event.so.1
Reading symbols from /usr/lib/libxcb-atom.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-atom.so.1
Reading symbols from /usr/lib/libxcb.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb.so.1
Reading symbols from /usr/lib/libXxf86vm.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXxf86vm.so.1
Reading symbols from /usr/lib/libdrm.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdrm.so.2
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /lib/tls/i686/cmov/librt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/librt.so.1
Reading symbols from /usr/lib/compiz/libccp.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/libprotobuf.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libprotobuf.so.3
Reading symbols from /usr/lib/libstdc++.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /usr/lib/compizconfig/backends/libgconf.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libgconf.so
Reading symbols from /usr/lib/libgconf-2.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgconf-2.so.4
Reading symbols from /lib/libglib-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libglib-2.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libORBit-2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libORBit-2.so.0
Reading symbols from /usr/lib/libgthread-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgthread-2.0.so.0
Reading symbols from /usr/lib/libdbus-glib-1.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbus-glib-1.so.2
Reading symbols from /lib/libdbus-1.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/libdbus-1.so.3
Reading symbols from /usr/lib/libgobject-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /lib/libpcre.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/libpcre.so.3
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/compiz/libsession.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsession.so
Reading symbols from /usr/lib/compiz/libmousepoll.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmousepoll.so
Reading symbols from /usr/lib/compiz/libpng.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/compiz/libsvg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsvg.so
Reading symbols from /usr/lib/libdecoration.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/librsvg-2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libcairo.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/libgsf-1.so.114...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libfontconfig.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libfreetype.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libgio-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgio-2.0.so.0
Reading symbols from /usr/lib/libpixman-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpixman-1.so.0
Reading symbols from /usr/lib/libdirectfb-1.2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdirectfb-1.2.so.0
Reading symbols from /usr/lib/libfusion-1.2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfusion-1.2.so.0
Reading symbols from /usr/lib/libdirect-1.2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdirect-1.2.so.0
Reading symbols from /usr/lib/libxcb-render-util.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-render-util.so.0
Reading symbols from /usr/lib/libxcb-render.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-render.so.0
Reading symbols from /lib/libbz2.so.1.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /lib/libexpat.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libexpat.so.1
Reading symbols from /lib/tls/i686/cmov/libresolv.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libresolv.so.2
Reading symbols from /lib/libselinux.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libselinux.so.1
Reading symbols from /usr/lib/compiz/libimgjpeg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libglib.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libglib.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libregex.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libshowdesktop.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshowdesktop.so
Reading symbols from /usr/lib/compiz/libwallpaper.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwallpaper.so
Reading symbols from /usr/lib/compiz/libdecoration.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/compiz/libezoom.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libezoom.so
Reading symbols from /usr/lib/libGLU.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/compiz/libkdecompat.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libkdecompat.so
Reading symbols from /usr/lib/compiz/libtitleinfo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libtitleinfo.so
Reading symbols from /usr/lib/compiz/libmove.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libgnomecompat.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libgnomecompat.so
Reading symbols from /usr/lib/compiUndefined command: "-e".  Try "help".
z/libneg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libneg.so
Reading symbols from /usr/lib/compiz/libtext.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/compiz/libresize.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libshift.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libcube.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcube.so
Reading symbols from /usr/lib/compiz/libshowmouse.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshowmouse.so
Reading symbols from /usr/lib/compiz/libanimation.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/compiz/librotate.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/librotate.so
Reading symbols from /usr/lib/compiz/libswitcher.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libswitcher.so
0xb7efe430 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread 0xb7990700 (LWP 4434)):
#0  0xb7efe430 in __kernel_vsyscall ()
#1  0xb7be1513 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7b83d03 in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7c9cfad in system () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb74c83e1 in ?? () from /usr/lib/compiz/libcrashhandler.so
#5  <signal handler called>
#6  0x08055c2d in ?? ()
#7  0x08058bb4 in eventLoop ()
#8  0x08052c93 in main ()
(gdb) 
(gdb) 
(gdb) #0  0xb7efe430 in __kernel_vsyscall ()
#1  0xb7be1513 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7b83d03 in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7c9cfad in system () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb74c83e1 in ?? () from /usr/lib/compiz/libcrashhandler.so
#5  <signal handler called>
#6  0x08055c2d in ?? ()
#7  0x08058bb4 in eventLoop ()
#8  0x08052c93 in main ()
(gdb) A debugging session is active.

	Inferior 1 [process 4434] will be detached.

Quit anyway? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 4434

[CRASH_HANDLER]: "/tmp/compiz_crash-4434.out" created!

---

### Post by unix1adm on 2009-11-18
I dont see this file on my system so I am not sure what is happening

Quit anyway? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 4434

[CRASH_HANDLER]: "/**tmp/compiz_crash-4434.out" created!**

---

### Post by unix1adm on 2009-11-18
this is the lates tial fromt he .xsession-errors files

tail .xsession-errors
** Message: <info>  disconnected by the session bus.

polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Drapes: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Cannot open display: :0.0
Run 'gnome-panel --help' to see a full list of available command line options.

---

