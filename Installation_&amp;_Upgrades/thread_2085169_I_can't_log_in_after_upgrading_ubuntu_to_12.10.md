---
title: "I can't log in after upgrading ubuntu to 12.10"
date: 2012-11-17
forum: Installation &amp; Upgrades
---

### Post by Raafat1991 on 2012-11-17
Hi...after i'm upgaring ubuntu from 12.04 to 12.10 i become unable to log in with my account but with guest account i can , i'm sure my password i have entered is correct , 
Also i can log in with my account but via recover mode.  ?

So what is solution for that ?

---

### Post by Raafat1991 on 2012-11-18
Please guys help me , i have important files

---

### Post by ibjsb4 on 2012-11-18
Try resetting your password.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Raafat1991 on 2012-11-18
> **ibjsb4 said:**
> Try resetting your password.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)


I did that but no luck.


thank you for your interaction ....

---

### Post by Raafat1991 on 2012-11-18
I'm waiting guys

---

### Post by tommcd on 2012-11-18
> **Raafat1991 said:**
> I did that but no luck.

What *exactly* happens when you follow the directions from: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Can you post the output from *all* of the commands that are given in that tutorial???
The output from those commands to reset your password and any errors you may get when running those commands may help in diagnosing this problem.

If all else fails, you could boot from the Ubuntu live CD, mount the partition(s) that contain your files, and then copy them to a usb stick or something to recover them.

This of course assumes that you did not format the partition(s) that contain your files when you upgraded your Ubuntu install.

---

### Post by NikTh on 2012-11-18
Hi , 

see if .Xauthority is corrupted. Try this 
When you are in login screen , hit CTRL+ALT+F2 to redirect in console mode. Login from there with your username & password (can you? ) 

If yes , then give these commands
```
sudo service lightdm stop 
rm ~/.Xauthority
sudo service lightdm start
```

Thanks

---

### Post by Raafat1991 on 2012-11-18
> **NikTh said:**
> Hi , 

see if .Xauthority is corrupted. Try this 
When you are in login screen , hit CTRL+ALT+F2 to redirect in console mode. Login from there with your username & password (can you? ) 

If yes , then give these commands
```
sudo service lightdm stop 
rm ~/.Xauthority
sudo service lightdm start
```Thanks

Also no luck , i have entered and i issue those commands....thank you for your interaction .

Please read the next post.

---

### Post by Raafat1991 on 2012-11-18
Hi

What happens with me exactly the following :

when i'm in login screen i choose my account and i enter my password the result:

the screen switch to entirely black screen and after may 3 or 2 seconds i back to the first screen (login screen) , when  i duplicate my step the same result , but with guest account i can log in with no problem.

i tried to enter incorrect password ubuntu tells me your passwords is invalid , but when i enter my correct password the result as i told you in above.

So what is solution for that ?


thank you

---

### Post by Raafat1991 on 2012-11-18
> **tommcd said:**
> What *exactly* happens when you follow the directions from: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Can you post the output from *all* of the commands that are given in that tutorial???
The output from those commands to reset your password and any errors you may get when running those commands may help in diagnosing this problem.

If all else fails, you could boot from the Ubuntu live CD, mount the partition(s) that contain your files, and then copy them to a usb stick or something to recover them.

This of course assumes that you did not format the partition(s) that contain your files when you upgraded your Ubuntu install.

I will do what you told me if(as you said) all else fails , but i focus on solving this problem .

thank you very much.

---

### Post by NikTh on 2012-11-18
&#919;i ,
are you able to provide some logs here ? For debugging proposes. 

Give the results of bellow commands 
```
cat /var/log/Xorg.0.log
cat .xsession-errors
sudo cat /var/log/lightdm/lightdm.log
sudo cat /var/log/lightdm/x-0-greeter.log
```Click on "New Reply" and put the results inside [CODE] tags to be easier to read. [See here how]("http://i.stack.imgur.com/zADbK.png")
Thanks

---

### Post by Raafat1991 on 2012-11-19
Hi

the first :  

```
[    30.571] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    30.571] X Protocol Version 11, Revision 0
[    30.571] Build Operating System: Linux 3.2.0-30-generic x86_64 Ubuntu
[    30.571] Current Operating System: Linux python-OptiPlex-780 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64
[    30.571] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic root=UUID=0a46c63d-5418-4354-802f-29bf612beff2 ro recovery nomodeset
[    30.571] Build Date: 08 October 2012  03:34:01PM
[    30.571] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    30.571] Current version of pixman: 0.26.0
[    30.571]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    30.571] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.571] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 19 16:00:27 2012
[    30.581] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.581] (==) No Layout section.  Using the first Screen section.
[    30.581] (==) No screen section available. Using defaults.
[    30.581] (**) |-->Screen "Default Screen Section" (0)
[    30.581] (**) |   |-->Monitor "<default monitor>"
[    30.581] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    30.582] (==) Automatically adding devices
[    30.582] (==) Automatically enabling devices
[    30.582] (==) Automatically adding GPU devices
[    30.582] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.582]     Entry deleted from font path.
[    30.582] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    30.582]     Entry deleted from font path.
[    30.582] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    30.582]     Entry deleted from font path.
[    30.582] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    30.582]     Entry deleted from font path.
[    30.582] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    30.582]     Entry deleted from font path.
[    30.582] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    30.582]     Entry deleted from font path.
[    30.582] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    30.582] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    30.582] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    30.582] (II) Loader magic: 0x7fc836b18c40
[    30.582] (II) Module ABI versions:
[    30.582]     X.Org ANSI C Emulation: 0.4
[    30.582]     X.Org Video Driver: 13.0
[    30.582]     X.Org XInput driver : 18.0
[    30.582]     X.Org Server Extension : 7.0
[    30.582] (II) config/udev: Adding drm device (/dev/dri/card0)
[    30.583] (--) PCI:*(0:0:2:0) 8086:2e12:1028:0420 rev 3, Mem @ 0xf7c00000/4194304, 0xe0000000/268435456, I/O @ 0x0000ecb0/8
[    30.583] (--) PCI: (0:0:2:1) 8086:2e13:1028:0420 rev 3, Mem @ 0xf7b00000/1048576
[    30.583] (II) Open ACPI successful (/var/run/acpid.socket)
[    30.583] Initializing built-in extension Generic Event Extension
[    30.583] Initializing built-in extension SHAPE
[    30.583] Initializing built-in extension MIT-SHM
[    30.583] Initializing built-in extension XInputExtension
[    30.583] Initializing built-in extension XTEST
[    30.583] Initializing built-in extension BIG-REQUESTS
[    30.583] Initializing built-in extension SYNC
[    30.583] Initializing built-in extension XKEYBOARD
[    30.583] Initializing built-in extension XC-MISC
[    30.583] Initializing built-in extension SECURITY
[    30.583] Initializing built-in extension XINERAMA
[    30.583] Initializing built-in extension XFIXES
[    30.583] Initializing built-in extension RENDER
[    30.583] Initializing built-in extension RANDR
[    30.583] Initializing built-in extension COMPOSITE
[    30.583] Initializing built-in extension DAMAGE
[    30.583] Initializing built-in extension MIT-SCREEN-SAVER
[    30.583] Initializing built-in extension DOUBLE-BUFFER
[    30.583] Initializing built-in extension RECORD
[    30.583] Initializing built-in extension DPMS
[    30.583] Initializing built-in extension X-Resource
[    30.583] Initializing built-in extension XVideo
[    30.583] Initializing built-in extension XVideo-MotionCompensation
[    30.583] Initializing built-in extension XFree86-VidModeExtension
[    30.583] Initializing built-in extension XFree86-DGA
[    30.583] Initializing built-in extension XFree86-DRI
[    30.583] Initializing built-in extension DRI2
[    30.583] (II) LoadModule: "glx"
[    30.593] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    30.593] (II) Module glx: vendor="X.Org Foundation"
[    30.593]     compiled for 1.13.0, module version = 1.0.0
[    30.593]     ABI class: X.Org Server Extension, version 7.0
[    30.593] (==) AIGLX enabled
[    30.593] Loading extension GLX
[    30.593] (==) Matched intel as autoconfigured driver 0
[    30.593] (==) Matched intel as autoconfigured driver 1
[    30.593] (==) Matched vesa as autoconfigured driver 2
[    30.593] (==) Matched modesetting as autoconfigured driver 3
[    30.593] (==) Matched fbdev as autoconfigured driver 4
[    30.594] (==) Assigned the driver to the xf86ConfigLayout
[    30.594] (II) LoadModule: "intel"
[    30.594] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    30.594] (II) Module intel: vendor="X.Org Foundation"
[    30.594]     compiled for 1.13.0, module version = 2.20.9
[    30.594]     Module class: X.Org Video Driver
[    30.594]     ABI class: X.Org Video Driver, version 13.0
[    30.594] (II) LoadModule: "vesa"
[    30.594] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.594] (II) Module vesa: vendor="X.Org Foundation"
[    30.594]     compiled for 1.12.99.902, module version = 2.3.2
[    30.594]     Module class: X.Org Video Driver
[    30.594]     ABI class: X.Org Video Driver, version 13.0
[    30.594] (II) LoadModule: "modesetting"
[    30.594] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.594] (II) Module modesetting: vendor="X.Org Foundation"
[    30.594]     compiled for 1.13.0, module version = 0.5.0
[    30.594]     Module class: X.Org Video Driver
[    30.594]     ABI class: X.Org Video Driver, version 13.0
[    30.594] (II) LoadModule: "fbdev"
[    30.594] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.594] (II) Module fbdev: vendor="X.Org Foundation"
[    30.594]     compiled for 1.12.99.902, module version = 0.4.3
[    30.594]     Module class: X.Org Video Driver
[    30.594]     ABI class: X.Org Video Driver, version 13.0
[    30.594] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[    30.595] (II) VESA: driver for VESA chipsets: vesa
[    30.595] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.595] (II) FBDEV: driver for framebuffer: fbdev
[    30.595] (++) using VT number 7

[    30.596] (II) intel(0): using device path '/dev/dri/card0'
[    30.596] (WW) Falling back to old probe method for vesa
[    30.596] (WW) Falling back to old probe method for modesetting
[    30.596] (WW) Falling back to old probe method for fbdev
[    30.596] (II) Loading sub module "fbdevhw"
[    30.596] (II) LoadModule: "fbdevhw"
[    30.596] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.596] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.596]     compiled for 1.13.0, module version = 0.0.2
[    30.596]     ABI class: X.Org Video Driver, version 13.0
[    30.596] (EE) open /dev/fb0: No such file or directory
[    30.596] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.596] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    30.596] (==) intel(0): RGB weight 888
[    30.596] (==) intel(0): Default visual is TrueColor
[    30.596] (--) intel(0): Integrated Graphics Chipset: Intel(R) Q45/Q43
[    30.596] (**) intel(0): Relaxed fencing enabled
[    30.596] (**) intel(0): Wait on SwapBuffers? enabled
[    30.596] (**) intel(0): Triple buffering? enabled
[    30.596] (**) intel(0): Framebuffer tiled
[    30.596] (**) intel(0): Pixmaps tiled
[    30.596] (**) intel(0): 3D buffers tiled
[    30.596] (**) intel(0): SwapBuffers wait enabled
[    30.596] (==) intel(0): video overlay key set to 0x101fe
[    30.596] (EE) intel(0): failed to get resources: Invalid argument
[    30.596] (II) UnloadModule: "intel"
[    30.596] (EE) Screen(s) found, but none have a usable configuration.
[    30.596] 
Fatal server error:
[    30.596] no screens found
[    30.596] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    30.596] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    30.596] (EE) 
[    30.597] Server terminated with error (1). Closing log file.

```


the second:

```
(gnome-settings-daemon:2224): color-plugin-WARNING **: failed to get edid: unable to get EDID for output

(gnome-settings-daemon:2224): color-plugin-WARNING **: unable to get EDID for xrandr-VGA1: unable to get EDID for output
ERROR:dbus.proxies:Introspect error on :1.36:/org/gnome/Nanny: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.48" (uid=1000 pid=2272 comm="python /usr/bin/nanny-systray ") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply="0" destination=":1.36" (uid=0 pid=1996 comm="/usr/bin/python /usr/bin/twistd --uid root --gid r")
ERROR:dbus.proxies:Introspect error on :1.36:/org/gnome/Nanny: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.48" (uid=1000 pid=2272 comm="python /usr/bin/nanny-systray ") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply="0" destination=":1.36" (uid=0 pid=1996 comm="/usr/bin/python /usr/bin/twistd --uid root --gid r")
** Message: applet now removed from the notification area

** (nautilus:2276): WARNING **: Can not get _NET_WORKAREA

** (nautilus:2276): WARNING **: Can not determine workarea, guessing at layout
Window manager warning: Trying to re-add keybinding "toggle-recording".
failed to create drawable
** Message: Stopping registered applet secret agent because GNOME Shell is running
failed to create drawable
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area
gpg: /tmp/tmpsZ4GaG/trustdb.gpg: trustdb created

** (zeitgeist-datahub:2410): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/python/.wine/dosdevices/c:/windows/Installer/345a.msi" was not found, exec: wine, mime_type: application/x-msi

** (zeitgeist-datahub:2410): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/python/Desktop/Other/java.mp4" was not found, exec: gtk-gnash, mime_type: video/mp4

** (zeitgeist-datahub:2410): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/python/001.mp3" was not found, exec: gtk-gnash, mime_type: audio/mpeg

** (zeitgeist-datahub:2410): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/python/Desktop/Other/Image/Mac-Lion-Wallpapers/mac_osx_lion_wallpaper.jpg" was not found, exec: eog, mime_type: image/jpeg

** (zeitgeist-datahub:2410): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/python/Desktop/Other/NK-CHILD-2.jpg" was not found, exec: eog, mime_type: image/jpeg

** (zeitgeist-datahub:2410): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/python/Desktop/Other/Image/Enst.jpg" was not found, exec: eog, mime_type: image/jpeg

** (zeitgeist-datahub:2410): CRITICAL **: string_strip: assertion `self != NULL' failed

(zeitgeist-datahub:2410): Gtk-CRITICAL **: IA__gtk_recent_info_get_application_info: assertion `app_name != NULL' failed

** (zeitgeist-datahub:2410): WARNING **: recent-manager-provider.vala:107: (null) was not registered in RecentInfo item 0x1f61f70

** (zeitgeist-datahub:2410): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/python/Desktop/Other/thumbnail.aspx.jpeg" was not found, exec: eog, mime_type: image/jpeg

** (zeitgeist-datahub:2410): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/python/Desktop/Other/Image/Mac-Lion-Wallpapers/mac_os_x_lion_wallpaper_.jpg" was not found, exec: eog, mime_type: image/jpeg

** (nautilus:2276): WARNING **: Error calling current_status: Method "current_status" with signature "" on interface "com.ubuntuone.SyncDaemon.Status" doesn't exist


** (nautilus:2276): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x1e045f3 specified for 0x1e05306 (update-man).

(firefox:2563): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.32.3/./gobject/gsignal.c:3393: signal name `load_complete' is invalid for instance `0x7f85a634ff10'
Window manager warning: Window 0x1e07bca (update-man) sets an MWM hint indicating it isn't resizable, but sets min size 174 x 213 and max size 2147483647 x 2147483647; this doesn't make much sense.
Window manager warning: Window 0x1e07bca (update-man) sets an MWM hint indicating it isn't resizable, but sets min size 174 x 213 and max size 2147483647 x 2147483647; this doesn't make much sense.
Window manager warning: Window 0x1e07bca (update-man) sets an MWM hint indicating it isn't resizable, but sets min size 174 x 213 and max size 2147483647 x 2147483647; this doesn't make much sense.
Window manager warning: Window 0x1e07bca (update-man) sets an MWM hint indicating it isn't resizable, but sets min size 256 x 192 and max size 2147483647 x 2147483647; this doesn't make much sense.
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x2400003 (Distributi) with a timestamp of 0.  This shouldn't happen!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x2400003 (Distributi) with a timestamp of 0.  This shouldn't happen!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!
gnome-session[2170]: WARNING: Detected that screensaver has left the bus
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x2400003 (Distributi) with a timestamp of 0.  This shouldn't happen!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!
Window manager warning: Log level 8: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Window manager warning: Log level 8: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Window manager warning: Log level 8: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-settings-daemon:2224): color-plugin-WARNING **: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/cups_HP_Color_LaserJet_CP3525

(gnome-settings-daemon:2224): color-plugin-WARNING **: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/cups_HP_Color_LaserJet_CP3525_2

(gnome-settings-daemon:2224): color-plugin-WARNING **: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/cups_HP_LaserJet_CM1415fnw

(gnome-settings-daemon:2224): color-plugin-WARNING **: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/cups_LaserJet_1320_series
Window manager warning: Log level 8: g_object_unref: assertion `G_IS_OBJECT (object)' failed
PolicyKit daemon disconnected from the bus.
We are no longer a registered authentication agent.
PolicyKit daemon reconnected to bus.
Attempting to re-register as an authentication agent.
We are now a registered authentication agent.

(evolution-alarm-notify:2453): evolution-alarm-notify-WARNING **: alarm.c:260: Requested removal of nonexistent alarm!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x2400003 (Distributi) with a timestamp of 0.  This shouldn't happen!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x2400003 (Distributi) with a timestamp of 0.  This shouldn't happen!

(gnome-settings-daemon:2224): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gnome-shell-calendar-server:2318): Gdk-WARNING **: gnome-shell-calendar-server: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gdu-notification-daemon:2377): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(evolution-alarm-notify:2453): Gdk-WARNING **: evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nautilus:2276): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nm-applet:2273): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(process:2253): GLib-CRITICAL (recursed) **: g_queue_get_length: assertion `queue != NULL' failed
** (zeitgeist-datahub:2410): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
```

the third:

```
[+0.01s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.01s] DEBUG: Starting Light Display Manager 1.4.0, UID=0 PID=1538
[+0.01s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.01s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.03s] DEBUG: Registered seat module xlocal
[+0.03s] DEBUG: Registered seat module xremote
[+0.03s] DEBUG: Adding default seat
[+0.03s] DEBUG: Starting seat
[+0.03s] DEBUG: Starting new display for greeter
[+0.03s] DEBUG: Starting local X display
[+0.05s] DEBUG: X server :0 will replace Plymouth
[+0.08s] DEBUG: Using VT 7
[+0.08s] DEBUG: Activating VT 7
[+0.08s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.08s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.08s] DEBUG: Launching X Server
[+0.08s] DEBUG: Launching process 1613: /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.08s] DEBUG: Waiting for ready signal from X server :0
[+0.08s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.08s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+2.61s] DEBUG: Process 1613 terminated with signal 6
[+2.61s] DEBUG: X server stopped
[+2.61s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+2.61s] DEBUG: Releasing VT 7
[+2.61s] DEBUG: Stopping Plymouth, X server failed to start
[+2.62s] DEBUG: Display server stopped
[+2.62s] DEBUG: Stopping display
[+2.62s] DEBUG: Display stopped
[+2.62s] DEBUG: Stopping X local seat, failed to start a display
[+2.62s] DEBUG: Stopping seat
[+2.62s] DEBUG: Seat stopped
[+2.62s] DEBUG: Required seat has stopped
[+2.62s] DEBUG: Stopping display manager
[+2.62s] DEBUG: Display manager stopped
[+2.62s] DEBUG: Stopping daemon
[+2.63s] DEBUG: Exiting with return value 1

```

finally:

```
[+0.00s] DEBUG: unity-greeter.vala:438: Starting unity-greeter 12.10.4 UID=104 LANG=en_US.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:441: Setting cursor
[+0.00s] DEBUG: unity-greeter.vala:455: Loading command line options
[+0.00s] DEBUG: unity-greeter.vala:483: Setting GTK+ settings
[+0.04s] DEBUG: unity-greeter.vala:506: Creating Unity Greeter
[+0.04s] DEBUG: unity-greeter.vala:55: Creating background surface
[+0.04s] DEBUG: Connecting to display manager...
[+0.04s] DEBUG: Wrote 17 bytes to daemon
[+0.04s] DEBUG: Read 8 bytes from daemon
[+0.04s] DEBUG: Read 149 bytes from daemon
[+0.04s] DEBUG: Connected version=1.4.0 default-session=ubuntu show-manual-login=false hide-users=false has-guest-account=true show-remote-login=true
[+0.07s] DEBUG: menubar.vala:342: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.07s] CRITICAL: dbusmenu_client_get_root: assertion `DBUSMENU_IS_CLIENT(client)' failed
[+0.07s] CRITICAL: dbusmenu_menuitem_get_children: assertion `DBUSMENU_IS_MENUITEM(mi)' failed
[+0.07s] DEBUG: indicator-session.c:390 setting a11y to "System"
[+0.08s] DEBUG: indicator-session.c:425 setting icon to "system-shutdown-panel"
[+0.08s] DEBUG: menubar.vala:562: Adding indicator object 0x172d188 at position 0
[+0.08s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.08s] DEBUG: Checking against 2 possible times
[+0.09s] DEBUG: Guessing max time width: 62
[+0.09s] DEBUG: menubar.vala:562: Adding indicator object 0x1737798 at position 1
[+0.09s] WARNING: IndicatorObject class does not have an accessible description.
[+0.09s] WARNING: IndicatorObject class does not have an accessible description.
[+0.09s] DEBUG: menubar.vala:562: Adding indicator object 0x172be58 at position 2
[+0.09s] DEBUG: menubar.vala:360: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.10s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.10s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+0.10s] DEBUG: Loading user /org/freedesktop/Accounts/User1001
[+0.11s] DEBUG: Loading user /org/freedesktop/Accounts/User1003
[+0.13s] DEBUG: Loading user /org/freedesktop/Accounts/User1002
[+0.15s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0.15s] DEBUG: user-list.vala:950: Adding/updating user python (Python)
[+0.25s] DEBUG: user-list.vala:950: Adding/updating user bijk ()
[+0.26s] DEBUG: user-list.vala:950: Adding/updating user goso ()
[+0.26s] DEBUG: user-list.vala:950: Adding/updating user student ()
[+0.26s] DEBUG: user-list.vala:932: Adding guest account entry
[+0.30s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0.30s] DEBUG: Loaded session /usr/share/xsessions/gnome-classic.desktop (GNOME Classic, This session logs you into GNOME with the traditional panel)
[+0.30s] DEBUG: Loaded session /usr/share/xsessions/gnome.desktop (GNOME, This session logs you into GNOME)
[+0.30s] DEBUG: Loaded session /usr/share/xsessions/gnome-fallback.desktop (GNOME Classic (No effects), This session logs you into GNOME with the traditional panel without any graphical effect.)
[+0.30s] DEBUG: Loaded session /usr/share/lightdm/remote-sessions/freerdp.desktop (FreeRDP, Full Screen RDP session)
[+0.30s] DEBUG: Loaded session /usr/share/lightdm/remote-sessions/uccsconfigure.desktop (UCCS Configure, Setup a UCCS Account)
[+0.30s] DEBUG: Starting authentication for user python...
[+0.30s] DEBUG: Wrote 22 bytes to daemon
[+0.37s] DEBUG: Starting authentication for user python...
[+0.37s] DEBUG: Wrote 22 bytes to daemon
[+0.37s] DEBUG: main-window.vala:176: Screen is 1024x768 pixels
[+0.37s] DEBUG: main-window.vala:182: Monitor 0 is 1024x768 pixels at 0,0
[+0.37s] DEBUG: unity-greeter.vala:509: Showing greeter
[+0.37s] DEBUG: unity-greeter.vala:198: Showing main window
[+0.37s] DEBUG: New style for time label
[+0.38s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.38s] DEBUG: Checking against 2 possible times
[+0.38s] DEBUG: Guessing max time width: 62
[+0.38s] DEBUG: background.vala:470: Regenerating backgrounds
[+0.38s] DEBUG: background.vala:68: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1024x768
[+0.38s] DEBUG: New style for time label
[+0.38s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.38s] DEBUG: Checking against 2 possible times
[+0.38s] DEBUG: Guessing max time width: 62
[+0.38s] DEBUG: unity-greeter.vala:527: Starting main loop
[+0.38s] DEBUG: Read 8 bytes from daemon
[+0.38s] DEBUG: Read 36 bytes from daemon
[+0.38s] DEBUG: Ignoring prompt authentication with invalid sequence number 1
[+0.38s] DEBUG: Read 8 bytes from daemon
[+0.38s] DEBUG: Read 36 bytes from daemon
[+0.38s] DEBUG: Prompt user with 1 message(s)
[+0.41s] DEBUG: Setting keyboard layout to 'us'
[+0.51s] DEBUG: background.vala:68: Making background /home/python/Desktop/Other/Image/Mac-Lion-Wallpapers/mac_os_x_lion_wallpaper_.jpg at 1024x768
[+0.55s] DEBUG: Connected to Application Indicator Service.
[+0.55s] MESSAGE: Couldn't find primary device
[+0.55s] DEBUG: icon_policy is: 0 (present==0, charge==1, never==2)
[+0.55s] DEBUG: count_batteries found 0 batteries (0 are charging/discharging)
[+0.55s] DEBUG: should_be_visible: no
[+0.55s] DEBUG: menubar.vala:570: Removing indicator object 0x172bd78
[+0.55s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.55s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.55s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.55s] WARNING: menubar.vala:582: Indicator object 0x172bd78 not in menubar
[+0.55s] DEBUG: indicator-sound: new_volume_slider_widget
[+0.55s] DEBUG: indicator-sound: new_voip_slider_widget
[+0.60s] DEBUG: New style for time label
[+0.60s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.60s] DEBUG: Checking against 2 possible times
[+0.60s] DEBUG: Guessing max time width: 62
[+0.70s] DEBUG: unity-greeter.vala:181: starting system-ready sound
[+0.72s] DEBUG: background.vala:117: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+0.74s] DEBUG: Request current apps
[+0.76s] DEBUG: notify visible signal received
[+0.76s] CRITICAL: ido_calendar_menu_item_get_calendar: assertion `IDO_IS_CALENDAR_MENU_ITEM (item)' failed
[+0.76s] CRITICAL: gtk_calendar_get_date: assertion `GTK_IS_CALENDAR (calendar)' failed
[+0.76s] CRITICAL: gtk_calendar_select_month: assertion `GTK_IS_CALENDAR (calendar)' failed
[+0.76s] CRITICAL: gtk_calendar_select_day: assertion `GTK_IS_CALENDAR (calendar)' failed
[+0.77s] DEBUG: New calendar item
[+0.77s] DEBUG: Changing calendar property: calendar-marks
[+0.77s] DEBUG:     Marks: []
** Message: applet now removed from the notification area
[+0.86s] DEBUG: background.vala:117: Render of background /home/python/Desktop/Other/Image/Mac-Lion-Wallpapers/mac_os_x_lion_wallpaper_.jpg complete
[+0.87s] DEBUG: Building new application entry: :1.22  with icon: nm-device-wired at position 0
[+0.87s] DEBUG: menubar.vala:562: Adding indicator object 0x18ea860 at position 3
[+0.89s] DEBUG: Generating properties error for: 28
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 29
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 30
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 31
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 32
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 33
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 34
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 35
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 37
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 38
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 39
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 40
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 41
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 42
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 43
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 44
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+0.89s] DEBUG: Generating properties error for: 36
[+0.89s] DEBUG: Error getting properties on a new menuitem: Error getting properties for ID
[+6.73s] DEBUG: New style for time label
[+6.73s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+6.73s] DEBUG: Checking against 2 possible times
[+6.73s] DEBUG: Guessing max time width: 62
[+7.22s] DEBUG: notify visible signal received
[+7.23s] DEBUG: New style for time label
[+7.23s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+7.23s] DEBUG: Checking against 2 possible times
[+7.23s] DEBUG: Guessing max time width: 62
** Message: PID 2367 (we are 2367) sent signal 15, shutting down...

(nm-applet:2367): libappindicator-WARNING **: Unable to send signal for NewStatus: The connection is closed

```


thank you.

---

### Post by NikTh on 2012-11-19
OK , 
lets try this 
From console mode (CTRL+ALT+F2) , login with username & password and try 
```
sudo service lightdm stop **#** if the result here is stop:Unknown instance , is OK **#**
sudo apt-get install --reinstall xserver-xorg xserver-xorg-video-intel gsettings-desktop-schemas
sudo dpkg-reconfigure xserver-xorg
```Then either reboot , or try this command
```
sudo service lightdm start
``` and try to login. 

Thanks

---

### Post by Raafat1991 on 2012-11-19
> **NikTh said:**
> OK , 
lets try this 
From console mode (CTRL+ALT+F2) , login with username & password and try 
```
sudo service lightdm stop **#** if the result here is stop:Unknown instance , is OK **#**
sudo apt-get install --reinstall xserver-xorg xserver-xorg-video-intell gsettings-desktop-schemas
sudo dpkg-reconfigure xserver-xorg
```Then either reboot , or try this command
```
sudo service lightdm start
``` and try to login. 

Thanks

With this command :

```
sudo apt-get install --reinstall xserver-xorg xserver-xorg-video-intell gsettings-desktop-schemas
```

Was the result:
```
E: Unable to locate package xserver-xorg-video-intell
E: Unable to locate package gsettings-desktop-schema

```

Is there difference when executing from terminal or CTRL+ALT+F2 ?

thank you very much.

---

### Post by NikTh on 2012-11-19
> **Raafat1991 said:**
> With this command :

```
sudo apt-get install --reinstall xserver-xorg xserver-xorg-video-intell gsettings-desktop-schemas
```Was the result:
```
E: Unable to locate package xserver-xorg-video-intell
E: Unable to locate package gsettings-desktop-schema

```Is there difference when executing from terminal or CTRL+ALT+F2 ?

thank you very much.

Hi , 
we have a typo here. Both you and me. 

The package is xserver-xorg-video-intel (with one l) 
and your typo is gsettings-desktop-schema you missing an s . The correct package name is
gsettings-desktop-schemas

Here is a trick , especially when you typing in console mode where no desktop environment exists. Use [Tab] key to autofill the names .
Example 
sudo apt-get install --reinstall xserver-xorg-video-i[Tab] 
or
sudo apt-get install --reinstall gsettings-desk[Tab] 

Thanks

---

### Post by greenwrangler on 2012-11-20
if you were using gnome-shell then you'd need to re-install it. It's not a part of the upgrade

sudo apt-get install gnome-shell

---

### Post by Raafat1991 on 2012-11-20
> **greenwrangler said:**
> if you were using gnome-shell then you'd need to re-install it. It's not a part of the upgrade

sudo apt-get install gnome-shell

What you said was my problem.

thank you ibjsb4  tommcd NikTh greenwrangler very much for your interaction with me.

i appreciate what you did for me.

---

