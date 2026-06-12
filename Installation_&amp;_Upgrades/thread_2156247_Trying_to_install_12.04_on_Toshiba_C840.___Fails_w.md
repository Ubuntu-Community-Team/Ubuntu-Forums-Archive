---
title: "Trying to install 12.04 on Toshiba C840.   Fails with critical errors"
date: 2013-06-21
forum: Installation &amp; Upgrades
---

### Post by dazz100 on 2013-06-21
Hi
I have installed Ubuntu on a variety of laptops and desktops.  I am trying to install Ubuntu 12.04 on an old Dell Latitude C840.  
The installation goes so far then reports and unrecoverable error.  Ubuntu then reverts to running the live CD.

The live CD runs OK.  Everything appears to work OK including graphics.  

I then ran Linux Rescue and manually set up two partitions.  One a 508MB swap and the remainder a ext4 partition.  
I ran fsck to check the disk.  No problems found.

When I try and boot from the HD after the failed install, I just get a flashing cursor on a black screen.  There is no indication that the HD has attempted a boot.

Google tells me others have successfully installed earlier versions of Ubuntu on similar Dell machines but no recent installs with 12.04.  

I recovered the installer logs that are below.  I don't understand the critical error messages and I don't know how to fix the problem.  An pointers would be much appreciated.

dm
```

X.Org X Server 1.13.0
Releas.e Date: 2012-09-05
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-34-generic i686 Ubuntu
Current Operating System: Linux ubuntu 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686
Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
Build Date: 19 January 2013  12:41:05PM
xorg-server 2:1.13.0-0ubuntu6.1~precise2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 20 19:33:12 2013
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
resize called 1400 1050
Activating service name='org.a11y.atspi.Registry'
Successfully activated service 'org.a11y.atspi.Registry'
SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry

** (at-spi2-registryd:2897): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (at-spi2-registryd:2897): WARNING **: Unable to register client with session manager

(panel:2876): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(panel:2876): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(panel:2876): Gtk-CRITICAL **: gtk_widget_realize: assertion `widget->priv->anchored || GTK_IS_INVISIBLE (widget)' failed

** (nm-applet:2877): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (gnome-settings-daemon:2875): WARNING **: Unable to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gnome-settings-daemon:2875): power-plugin-WARNING **: gnome-session is not available

(gnome-settings-daemon:2875): color-plugin-WARNING **: failed to connect to colord: Error calling StartServiceByName for org.freedesktop.ColorManager: GDBus.Error:org.freedesktop.DBus.Error.TimedOut: Activation of org.freedesktop.ColorManager timed out
** Message: applet now removed from the notification area
** Message: Starting applet secret agent because GNOME Shell disappeared

** (process:3095): WARNING **: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (nm-applet:2877): CRITICAL **: nm_secret_agent_register: assertion `priv->registered == FALSE' failed

(nm-applet:2877): libnotify-WARNING **: Failed to connect to proxy

** (nm-applet:2877): WARNING **: Failed to show notification: Timeout was reached

(panel:2876): Gtk-CRITICAL **: gtk_widget_set_accel_path: assertion `GTK_IS_ACCEL_GROUP (accel_group)' failed

(panel:2876): Gtk-CRITICAL **: gtk_widget_add_accelerator: assertion `GTK_IS_ACCEL_GROUP (accel_group)' failed

(panel:2876): Gtk-CRITICAL **: gtk_widget_set_accel_path: assertion `GTK_IS_ACCEL_GROUP (accel_group)' failed

(panel:2876): Gtk-CRITICAL **: gtk_widget_add_accelerator: assertion `GTK_IS_ACCEL_GROUP (accel_group)' failed
** Message: PID 1765 (we are 2877) sent signal 15, shutting down...
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 41 requests (41 known processed) with 0 events remaining.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
Server terminated successfully (0). Closing log file.

```


```

Ubiquity 2.10.24

** (ubiquity:2895): WARNING **: The connection is closed

(ubiquity:2895): Pango-WARNING **: error opening config file '/root/.pangorc': Permission denied

Error opening file for reading: Permission denied
update_release_notes_label()
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1327, in on_next_clicked
    self.dbfilter.ok_handler()
  File "/usr/lib/ubiquity/plugins/ubi-prepare.py", line 263, in ok_handler
    obj = bus.get_object(JOCKEY, JOCKEY_PATH)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1327, in on_next_clicked
    self.dbfilter.ok_handler()
  File "/usr/lib/ubiquity/plugins/ubi-prepare.py", line 263, in ok_handler
    obj = bus.get_object(JOCKEY, JOCKEY_PATH)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

---

### Post by ahallubuntu on 2013-06-21
~

---

### Post by dazz100 on 2013-06-21
Hi
Can you point to a source of an ISO download?  I did a search but only found spam sites.
I found Ubuntu Smartmontools but that package is not included on the Ubuntu image.
This HD had WinXP and worked OK.

---

### Post by ahallubuntu on 2013-06-21
~

---

### Post by mörgæs on 2013-06-22
There's no reason to suspect the hard drive, but Ubuntu is too heavy for a C840.
Try the alternate Lubuntu 13.04.

---

### Post by dazz100 on 2013-06-23
Hi

I hadn't thought of trying Lubuntu but it is a good idea.  The C840 has a nice display comparable to younger laptops but it is slow.  A swift version of Linux should fix that.


I have successfully installed Ubuntu on lesser laptops (eg.  IBM T42) with ease. The Dell C840 should be able to swallow Ubuntu but I will give Lubuntu a go.

---

### Post by dazz100 on 2013-06-24
Hi
I had ago at installing Lubuntu and had two failures.  

Firstly, the screen went blank with just a cursor flashing.  I managed to fix this by setting the <nomodeset> option in the F6 boot menu.
I am guessing the same option will fix the same problem with installing Ubuntu, but I didn't try it.

The other error was a fatal failure by Lubuntu to partition the swap file.  A few days ago, I was able to successfully partition the disk using Parted. This points to a failing hard drive.  I will do some more testing before buying a new HD.  A new HD will basically double the value of this very old laptop.

---

### Post by mörgæs on 2013-06-24
OK, now we have a reason to suspect :-)

With **badblocks** you can test the hard drive and see where the problem is. When that is done you can partition the drive in a way so the failing areas are not used. 

No need for buying new stuff yet.

---

### Post by dazz100 on 2013-06-27
Hi
OK   thanks for the advice. 
I am going to put this laptop aside while I sort out higher priority issues on other PCs/networks.
When I do, I will run a disk scan to check health and I will post the results here for the benefit of other that may face this problem.

---

### Post by dazz100 on 2013-06-30
Hi

I had another crack at this last night.
I managed to get to a point during installation when I was asked for a ID/password.  Nothing worked.
Google indicated that this is due to a faulty installation CD.

I burnt a new Lubuntu CD with a speed of 2x (rather than the default 24x).  I then did a scan of the CD (all OK) before attempting an install.
The install appeared to complete OK.

On reboot, I just got a black screen with a flashing white cursor.  To fix that I think I need to permanently set "nomodeset" in grub.  That is a far as I got.
At this stage there is no evidence pointing to a faulty hard drive.

The other issue I haven't yet tackled is the screen resolution. At present the display is surrounded by a thick black border.  The live CD doesn't allow me to specify a higher resolution to fill up the screen.

---

### Post by mörgæs on 2013-07-01
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. It will create a hardware overview which will help people to give advice on the problem (I will be offline for some time now).

Yes, a slowly burned CD is good, but if your BIOS supports it then booting from USB is the most reliable.

---

