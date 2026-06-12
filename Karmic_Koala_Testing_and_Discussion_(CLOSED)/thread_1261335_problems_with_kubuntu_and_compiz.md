---
title: "problems with kubuntu and compiz"
date: 2009-09-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by KhaaL on 2009-09-08
I'm having trouble once i've installed compiz on kubuntu. at startup, KDE gets stuck on the splash screen at the first icon and dosent get past that unless i get into a tty and do a sudo killall compiz. Which logs should I check for a possible culprit? I installed compiz through the package compiz-kde

---

### Post by cariboo on 2009-09-08
KDE uses kwin instead of compiz.

---

### Post by KhaaL on 2009-09-08
I am well aware of that, but that surely dosen't make it incompatible with compiz, no?

Ok, found that .xsession-errors could be a source of information:

```

Xsession: X session started for khaal at Tue Sep  8 22:32:31 CEST 2009
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (core) - Warn: Plugin 'ccp' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

```
***it gets stuck at this point unless i do a killall compiz***

```

startkde: Starting up...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kcminit_startup.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_ksmserver.so
<unknown program name>(17539)/ KStartupInfo::createNewStartupId: creating:  "xeraphim;1252442021;436951;17539_TIME0" : "unnamed app"
kwin: unable to claim manager selection, another wm running? (try using --replace)
kdeinit4: preparing to launch /usr/lib/libkdeinit4_plasma-desktop.so
kephald starting up 
XRANDR error base:  174 
RRInput mask is set!! 
RandRScreen::loadSettings - adding mode:  323 1680 x 1050 
RandRScreen::loadSettings - adding mode:  324 1680 x 1050 
RandRScreen::loadSettings - adding mode:  325 1600 x 1024 
RandRScreen::loadSettings - adding mode:  326 1440 x 900 
RandRScreen::loadSettings - adding mode:  327 1400 x 1050 
RandRScreen::loadSettings - adding mode:  328 1400 x 1050 
RandRScreen::loadSettings - adding mode:  329 1360 x 768 
RandRScreen::loadSettings - adding mode:  330 1360 x 768 
RandRScreen::loadSettings - adding mode:  331 1280 x 1024 
RandRScreen::loadSettings - adding mode:  332 1280 x 1024 
RandRScreen::loadSettings - adding mode:  333 1280 x 960 
RandRScreen::loadSettings - adding mode:  334 1152 x 864 
RandRScreen::loadSettings - adding mode:  335 1152 x 864 
RandRScreen::loadSettings - adding mode:  336 1152 x 864 
RandRScreen::loadSettings - adding mode:  337 1152 x 864 
RandRScreen::loadSettings - adding mode:  338 1024 x 768 
RandRScreen::loadSettings - adding mode:  339 1024 x 768 
RandRScreen::loadSettings - adding mode:  340 1024 x 768 
RandRScreen::loadSettings - adding mode:  341 960 x 600 
RandRScreen::loadSettings - adding mode:  342 960 x 540 
RandRScreen::loadSettings - adding mode:  343 840 x 525 
RandRScreen::loadSettings - adding mode:  344 840 x 525 
RandRScreen::loadSettings - adding mode:  345 840 x 525 
RandRScreen::loadSettings - adding mode:  346 832 x 624 
RandRScreen::loadSettings - adding mode:  347 800 x 600 
RandRScreen::loadSettings - adding mode:  348 800 x 600 
RandRScreen::loadSettings - adding mode:  349 800 x 600 
RandRScreen::loadSettings - adding mode:  350 800 x 600 
RandRScreen::loadSettings - adding mode:  351 800 x 600 
RandRScreen::loadSettings - adding mode:  352 800 x 600 
RandRScreen::loadSettings - adding mode:  353 800 x 512 
RandRScreen::loadSettings - adding mode:  354 720 x 450 
RandRScreen::loadSettings - adding mode:  355 700 x 525 
RandRScreen::loadSettings - adding mode:  356 700 x 525 
RandRScreen::loadSettings - adding mode:  357 700 x 525 
RandRScreen::loadSettings - adding mode:  358 680 x 384 
RandRScreen::loadSettings - adding mode:  359 680 x 384 
RandRScreen::loadSettings - adding mode:  360 640 x 512 
RandRScreen::loadSettings - adding mode:  361 640 x 512 
RandRScreen::loadSettings - adding mode:  362 640 x 480 
RandRScreen::loadSettings - adding mode:  363 640 x 480 
RandRScreen::loadSettings - adding mode:  364 640 x 480 
RandRScreen::loadSettings - adding mode:  365 640 x 480 
RandRScreen::loadSettings - adding mode:  366 640 x 480 
RandRScreen::loadSettings - adding mode:  367 640 x 480 
RandRScreen::loadSettings - adding mode:  368 576 x 432 
RandRScreen::loadSettings - adding mode:  369 576 x 432 
RandRScreen::loadSettings - adding mode:  370 576 x 432 
RandRScreen::loadSettings - adding mode:  371 576 x 432 
RandRScreen::loadSettings - adding mode:  372 512 x 384 
RandRScreen::loadSettings - adding mode:  373 512 x 384 
RandRScreen::loadSettings - adding mode:  374 512 x 384 
RandRScreen::loadSettings - adding mode:  375 416 x 312 
RandRScreen::loadSettings - adding mode:  376 400 x 300 
RandRScreen::loadSettings - adding mode:  377 400 x 300 
RandRScreen::loadSettings - adding mode:  378 400 x 300 
RandRScreen::loadSettings - adding mode:  379 400 x 300 
RandRScreen::loadSettings - adding mode:  380 320 x 240 
RandRScreen::loadSettings - adding mode:  381 320 x 240 
RandRScreen::loadSettings - adding mode:  382 320 x 240 
RandRScreen::loadSettings - adding crtc:  321 
RandRScreen::loadSettings - adding output:  322 
Setting CRTC 321 on output "default" (previous 0 ) 
CRTC outputs: (322) 
Output name: "default" 
Output refresh rate: 50 
Output rect: QRect(0,0 1680x1050) 
Output rotation: 1 
XRandROutputs::init 
  added output  322 
adding an output 0 with geom:  QRect(0,0 1680x1050) 
output: "SCREEN-0" QRect(0,0 1680x1050) 459277 false false 
load xml 
connected: 1 
looking for current "SCREEN-0" 
known "*" has score: 0.125 
screen: 0 QRect(0,0 1680x1050) 
looking for a matching configuration... 
connected: 1 
looking for current "SCREEN-0" 
known "*" has score: 0.125 
found outputs, known: false 
activate external configuration!! 
registered the service: true 
screens registered on the bus: true 
outputs registered on the bus: true 
configurations registered on the bus: true 
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kglobalaccel.so
QLayout: Attempting to add QLayout "" to QWidget "", which already has a layout
Object::connect: No such signal PixmapListDialog::currentPixmapChanged( int ) in /build/buildd/plasma-widget-cwp-0.9.11~jaunty~ppa1/plasma-cwp.cpp:102
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
QPainter::begin: Cannot paint on a null pixmap
QPainter::setRenderHint: Painter must be active to set rendering hints
QPainter::begin: Cannot paint on a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPainter::end: Painter not active, aborted
QPainter::begin: Cannot paint on a null pixmap
QPainter::setRenderHint: Painter must be active to set rendering hints
QPainter::begin: Cannot paint on a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPainter::end: Painter not active, aborted
Invalid D-BUS interface name 'org.kde.plasma-desktop.PlasmaApp' found while parsing introspection
kdeinit4: preparing to launch /usr/lib/kde4/kio_desktop.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_trash.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_http.so
kdeinit4: preparing to launch /usr/bin/kwrited
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_desktop.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_desktop.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_desktop.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kaccess.so
<unknown program name>(17612)/ kdemain: Xlib XKB extension major= 1  minor= 0
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kxkb.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_krunner.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_nepomukserver.so
kdeinit4: preparing to launch /usr/bin/firefox
kdeinit4: preparing to launch /usr/bin/gnome-do
kdeinit4: preparing to launch /usr/bin/xbindkeys
kdeinit4: preparing to launch /usr/bin/skype
kdeinit4: preparing to launch /usr/lib/libkdeinit4_konsole.so
kdeinit4: preparing to launch /usr/bin/checkgmail
kdeinit4: preparing to launch /bin/sh
kdeinit4: preparing to launch /usr/bin/update-notifier-kde
kdeinit4: preparing to launch /usr/bin/printer-applet
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klipper.so
kdeinit4: preparing to launch /usr/bin/kblueplugd
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kmix.so
kdeinit4: preparing to launch /usr/bin/knetworkmanager
Checking for Xgl: kdeinit4: preparing to launch /usr/bin/knotify4
not present. 

Gdk-ERROR **: The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 33 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
aborting...
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1knetworkmanager(17666) NMDBusSettingsService::NMDBusSettingsService: registered "org.freedesktop.NetworkManagerUserSettings"
knetworkmanager(17666) NMDBusSettingsService::NMDBusSettingsService: Registered settings object  /org/freedesktop/NetworkManagerSettings

<unknown program name>(17621)/: Communication problem with  "krunner" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 

Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: <unknown program name>(17647)/: Communication problem with  "klipper" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 

Not present. 
Checking for nVidia: ALSA lib pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
present. 
Checking for FBConfig: kdeinit4: preparing to launch /usr/bin/systemsettings
present. 
Checking for Xgl: not present. 
QLayout: Attempting to add QLayout "" to InterfaceConnectionItem "", which already has a layout
# of devices at startup: 1
Traceback (most recent call last):
  File "/usr/bin/kblueplugd", line 35, in <module>
    distutils.spawn.spawn(kbtcmd)
  File "/usr/lib/python2.6/distutils/spawn.py", line 37, in spawn
    _spawn_posix(cmd, search_path, dry_run=dry_run)
  File "/usr/lib/python2.6/distutils/spawn.py", line 167, in _spawn_posix
    (cmd[0], exit_status)
distutils.errors.DistutilsExecError: command 'kbluetooth4' failed with exit status 255
AGENT registered ! 

(Do:17643): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

findServiceByDesktopPath:  not found
kdeinit4: preparing to launch /usr/bin/dolphin
<unknown program name>(17652)/: Communication problem with  "kmix" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 

kdeinit4: preparing to launch /usr/lib/kde4/kio_trash.so
Could not locate Tomboy on D-Bus. Perhaps it's not running?
Firefox.PlacesItemSource "Firefox Places" encountered an error in UpdateItems: Object reference not set to an instance of an object.
QPainter::begin: Cannot paint on a null pixmap
QPainter::setRenderHint: Painter must be active to set rendering hints
QPainter::end: Painter not active, aborted
kdeinit4: preparing to launch /usr/bin/dolphin
"/usr/bin/dolphin(17782)" Error in thread 140170065499984 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(17782)" Error in thread 140170065499984 : "QLocalSocket::connectToServer: Invalid name"
kdeinit4
kblueplugd
kwin
kdeinit4: preparing to launch /usr/lib/kde4/kio_trash.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM null
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM null
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../../src/pcm/pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kio_http_cache_cleaner.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/bin/gedit
```

after this it starts quite fine, after i made a script that runs compiz --replace and emerald --replace... its just that hitch at the splash screen thats bugging me.

---

### Post by buzzmandt on 2009-09-08
just to note,  i installed kubuntu on a friends computer.  It wouldn't run compiz at all, but kwin worked just fine.

---

### Post by KhaaL on 2009-09-09
I managed to fix this. Appearently in my ~./kde/env/ folder i had a compiz.sh file which messed up the initialization of KDE majory. for the curious, it contained:

```
 #!/bin/bash
 LIBGL_ALWAYS_INDIRECT=1
 compiz --replace --sm-disable --ignore-desktop-hints ccp --indirect-rendering &
 wait
 sleep 1
 kde4-window-decorator --replace&

```

cheers

---

