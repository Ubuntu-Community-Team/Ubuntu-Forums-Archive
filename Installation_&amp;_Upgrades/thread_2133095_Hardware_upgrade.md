---
title: "Hardware upgrade"
date: 2013-04-07
forum: Installation &amp; Upgrades
---

### Post by katamari92 on 2013-04-07
I just 'upgraded' from amd integrated graphics in a laptop to another laptop (I just swapped the hard drive) with Intel integrated graphics core i7 2670qm. I use gnome 2 as my interface of choice and now i am not getting any of the cool effects and searching features. I see no drivers in the additional drivers just a blank screen. I don't know what to do. i've installed a bunch of stuff to get it working, nothing has worked.
one site i tried is: [http://ubuntuforums.org/showthread.php?t=1943652](http://ubuntuforums.org/showthread.php?t=1943652)
[COLOR=#000000][FONT=helvetica]Is there a way to tell ubuntu to recheck all drivers like it does during installation?[/FONT][/COLOR]

---

### Post by dino99 on 2013-04-07
as you have swapped the disk, it only knows about the previous config : aka "amd" graphic . On a standard installation, you usually have also xserver-xorg-video-intel driver installed; and now when you boot, it should be detected and loaded directly by the kernel. But as it seems not listed , then install synaptic to check that its well installed:

sudo apt-get install synaptic
sudo synaptic
sudo apt-get install --reinstall xserver-xorg-video-intel

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
(be patient, it can take a while, dont stop it yourself)

After rebooting, check ~/.xsession-errors (ctrl+h to unhide it) to find possible issues

---

### Post by katamari92 on 2013-04-07
I apologize if this is a long comment. The forum would not let me attach the file for you and i'm not sure if the spoiler code shrinks what is put into it
No dice still no drivers. Got any other tricks?
[COLOR=#DDDDDD][FONT=Verdana]


spoiler][/FONT][/COLOR]X Error of failed request:  BadRequest (invalid request code or no such operation)  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22
gnome-session[1500]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-shell: [DEBUG] Got bus address:  "unix:abstract=/tmp/dbus-WCLK2uX7Ob,guid=ce897e2cc5f687de17a4846200000029" 
unity-2d-shell: [DEBUG] Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-WCLK2uX7Ob,guid=ce897e2cc5f687de17a4846200000029" 
unity-2d-shell: [DEBUG] Registered DEC:  true 
unity-2d-panel: [DEBUG] Got bus address:  "unix:abstract=/tmp/dbus-WCLK2uX7Ob,guid=ce897e2cc5f687de17a4846200000029" 
unity-2d-panel: [DEBUG] Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-WCLK2uX7Ob,guid=ce897e2cc5f687de17a4846200000029" 
unity-2d-panel: [DEBUG] Registered DEC:  true 
unity-2d-panel: [DEBUG] Scanning panel plugin directory "/usr/lib/unity-2d/plugins/panel" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appindicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appname.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-indicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-legacytray.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-separator.so" 
unity-2d-panel: [DEBUG] Configured plugins list is: ("appname", "!legacytray", "indicator") 
unity-2d-shell: [DEBUG] static void WindowImageProvider::activateComposite(): Server supports the Composite extension (ver 0.4)
** Message: applet now removed from the notification area
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1c00004 (Onboard)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1c00004 (Onboard)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
** Message: using fallback from indicator to GtkStatusIcon
unity-2d-panel: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-panel: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x0
unity-2d-panel: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F10" 
unity-2d-panel: [DEBUG] Registered event listener change listener:  true 
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+S" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+T" 
** Message: moving back from GtkStatusIcon to indicator
unity-2d-shell: [WARNING] Object::connect: No such signal Lenses::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.14.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-shell: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/hud/Hud.qml:145: TypeError: Result of expression 'shellManager.hudShell' [null] is not an object.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] Registered event listener change listener:  true 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+A" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+F" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+M" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+V" 
unlinked 0 orphaned pipes
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1128f0) "" 
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Steam: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  135 (GLX)
Minor opcode of failed request:  19 (X_GLXQueryServerString)
Serial number of failed request:  34
xerror_handler: X failed, continuing
Steam: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  135 (GLX)
Minor opcode of failed request:  19 (X_GLXQueryServerString)
Serial number of failed request:  44
xerror_handler: X failed, continuing
Steam: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  135 (GLX)
Minor opcode of failed request:  14 (X_GLXGetVisualConfigs)
Serial number of failed request:  54
xerror_handler: X failed, continuing
glXChooseVisual failed[2130:2179:0407/052648:ERROR;object_proxy.cc(624)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[2130:2179:0407/052648:ERROR;object_proxy.cc(624)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[2130:2130:0407/052651:ERRORobject_proxy.cc(529)] Failed to call method: org.chromium.Mtpd.EnumerateStorages: object_path= /org/chromium/Mtpd: org.freedesktop.DBus.Error.ServiceUnknown: The name org.chromium.Mtpd was not provided by any .service files
[2130:2201:0407/052653:ERROR:connection.cc(730)] sqlite error 19, errno -2: PRIMARY KEY must be unique
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1128f0) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1128f0) "" 
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3e000b7 ([ubuntu] H)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3e000b7 ([ubuntu] H)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3e000b7 ([ubuntu] H)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.


** (nautilus:1846): WARNING **: Error calling current_status: Method "current_status" with signature "" on interface "com.ubuntuone.SyncDaemon.Status" doesn't exist




** (nautilus:1846): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application690076648") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application690076648") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application690076648") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application690076648") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application690076648") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application690076648") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application690076648") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application690076648") 
[2575:2575:0407/052723:ERROR:gl_surface_glx.cc(326)] glxQueryVersion failed
[2575:2575:0407/052723:ERROR:gl_surface_linux.cc(58)] GLSurfaceGLX::InitializeOneOff failed.
[2575:2575:0407/052723:ERROR11_util.cc(1824)] X error received: serial 12, error_code 1 (BadRequest), request_code 135, minor_code 19 (Unknown)
[2575:2575:0407/052723:ERROR11_util.cc(1824)] X error received: serial 13, error_code 1 (BadRequest), request_code 135, minor_code 19 (Unknown)
[2575:2575:0407/052723:ERROR11_util.cc(1824)] X error received: serial 14, error_code 1 (BadRequest), request_code 135, minor_code 14 (Unknown)
[2588:2588:0407/052723:ERROR:gl_surface_glx.cc(326)] glxQueryVersion failed
[2588:2588:0407/052723:ERROR:gl_surface_linux.cc(58)] GLSurfaceGLX::InitializeOneOff failed.
[2588:2588:0407/052724:ERROR11_util.cc(1824)] X error received: serial 12, error_code 1 (BadRequest), request_code 135, minor_code 19 (Unknown)
[2588:2588:0407/052724:ERROR11_util.cc(1824)] X error received: serial 13, error_code 1 (BadRequest), request_code 135, minor_code 19 (Unknown)
[2588:2588:0407/052724:ERROR11_util.cc(1824)] X error received: serial 14, error_code 1 (BadRequest), request_code 135, minor_code 14 (Unknown)
[2595:2595:0407/052724:ERROR:gl_surface_glx.cc(326)] glxQueryVersion failed
[2595:2595:0407/052724:ERROR:gl_surface_linux.cc(58)] GLSurfaceGLX::InitializeOneOff failed.
[2595:2595:0407/052724:ERROR11_util.cc(1824)] X error received: serial 12, error_code 1 (BadRequest), request_code 135, minor_code 19 (Unknown)
[2595:2595:0407/052724:ERROR11_util.cc(1824)] X error received: serial 13, error_code 1 (BadRequest), request_code 135, minor_code 19 (Unknown)
[2595:2595:0407/052724:ERROR11_util.cc(1824)] X error received: serial 14, error_code 1 (BadRequest), request_code 135, minor_code 14 (Unknown)
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1f69b0) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1ec860) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa162090) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1a7980) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa155120) "" 
unity-2d-shell: [WARNING] QSpiAccessible:: accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1aed28) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1128f0) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa143418) "" 
No bp log location saved, using default.
[000:000] Browser XEmbed support present: 1
[000:000] Browser toolkit is Gtk2.
[000:000] Using Gtk2 toolkit
[000:004] Starting client channel.
[000:004] Warning(clientchannel.cc:436): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[000:004] Warning(clientchannel.cc:411): Could not initiate GoogleTalkPlugin connection
[000:004] GoogleTalkPlugin not running. Starting new process...
[000:004] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:005] Warning(pluginutils.cc:251): Failed to get GoogleTalkPlugin path. Trying default.
[000:006] Started GoogleTalkPlugin, path=/opt/google/talkplugin/GoogleTalkPlugin
[000:006] Waiting for GoogleTalkPlugin to start...
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


[001:103] Attempting to connect to GoogleTalkPlugin...
[001:103] Warning(clientchannel.cc:436): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[001:104] Warning(clientchannel.cc:411): Could not initiate GoogleTalkPlugin connection
[001:104] Waiting for GoogleTalkPlugin to start...
[002:106] Attempting to connect to GoogleTalkPlugin...
[002:107] Read port file, port=57552
[002:107] Initiated connection to GoogleTalkPlugin
[002:209] Socket connection established
[002:209] ScheduleOnlineCheck: Online check in 5000ms
[002:308] Got cookie response, socket is authorized
[002:308] AUTHORIZED; socket handshake complete
[002:310] F->C: ["fs",{"pr":"a"}]
[002:509] F->C: ["mf","mf3.17","3.17.0.0",2,{"audioCodecs":[[103,"ISAC",1,0,16000],[104,"ISAC",1,0,32000],[9,"G722",1,64000,16000],[102,"ILBC",1,13300,8000],[0,"PCMU",1,64000,8000],[8,"PCMA",1,64000,8000],[107,"CN",1,0,48000],[106,"CN",1,0,32000],[105,"CN",1,0,16000],[13,"CN",1,0,8000],[127,"red",1,0,8000],[126,"telephone-event",1,0,8000]],"audioRtpHdrExts":[{"id":1,"uri":"urn:ietfarams:rtp-hdrext:ssrc-audio-level"}],"camDeviceName":"Unknown Camera","caps":7,"cpuArchitecture":0,"cpuCacheSize":6291456,"cpuFamily":6,"cpuFlags":["sse2","ssse3","sse4_1","sse4_2","avx"],"cpuHasSSE2":true,"cpuModel":42,"cpuSpeed":2201,"cpuStepping":7,"cpuVendor":"GenuineIntel","cpus":8,"cpusPhysical":4,"cryptoSuites":["AES_CM_128_HMAC_SHA1_80","AES_CM_128_HMAC_SHA1_32"],"dataChannelVersion":1,"effectsVersion":9,"gpuDescription":"","gpuDeviceId":0,"gpuDeviceName":"","gpuDriver":"","gpuDriverVersion":"","gpuVendorId":0,"machineModel":"Not available","remotingAssistanceAllowed":0,"remotingVersion":1,"renderer":2,"rtcpMux":true,"screencast":2,"screencastLocalPreview":1,"supportsConcurrentSessions":true,"transports":["i","gice"],"videoCodecs":[[99,"H264-SVC",640,360,30],[97,"H264",640,360,30],[98,"H263",640,360,30]],"videoRtpHdrExts":[{"id":2,"uri":"urn:ietf:params:rtp-hdrext:toffset"}]}]
[002:609] F->C: ["getdevicestate","15","0",["__default_device","Built-in Audio Analog Stereo"],"0",["__default_device","Built-in Audio Analog Stereo"],"-1",[]]
[007:219] HandleOnlineCheck: Starting check
[007:219] HandleOnlineCheck: OK; current state: 3
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1a7980) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa162090) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1ec860) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1f69b0) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1fdda8) "" 


(jockey-gtk:2771): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed


(jockey-gtk:2771): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application570171121") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application570171121") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application570171121") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application570171121") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application570171121") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application570171121") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application570171121") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1209124405") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1990862807") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1990862807") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1990862807") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1990862807") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1990862807") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1990862807") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1990862807") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1990862807") 
unity-2d-panel: unity-2d-shell[WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462") 
: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application62801462") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application62801462") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application62801462") 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1128f0) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa143418) "" 
Window manager warning: unity-2d-shellReceived a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
: [WARNING] Wnck: Received a timestamp of 0; window activation may not function properly.


Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2600212 (Home)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa10d360) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa143418) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa10d360) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa10d360) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa10d360) "" 
[2130:2130:0407/053327:ERRORomnibox_view_gtk.cc(431)] Not implemented reached in virtual void OmniboxViewGtk::ApplyCaretVisibility()
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa162090) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1ec860) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1f69b0) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1fdda8) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa20c1d0) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1fdda8) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1f69b0) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa162090) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1a7980) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa1aed28) "" 
unity-2d-shell: [WARNING] QSpiAccessible::accessibleEvent not handled:  "7"  obj:  LauncherContextualMenu(0xa143418) "" 
unity-2d-shellWindow manager warning: : [WARNING] Wnck: Received a timestamp of 0; window activation may not function properly.


Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2600212 (Home)

Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.[COLOR=#DDDDDD][FONT=Verdana][/spoiler][/FONT][/COLOR]

---

