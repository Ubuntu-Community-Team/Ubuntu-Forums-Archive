---
title: "Language problem after installing Japanese language support"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by shayli147 on 2014-04-25
hello to all

i have upgraded to ubuntu 14.04 64bit through a DVD after upgrading failed from inside the system. after 3 days i got the system working and adjusted to my needs. as part of adjusting the system i added Japanese language support from the system settings. after the installation- not only that it didn't completely add the language (i couldn't type it), it won't completely remove it.

for the rest of the time i have been struggling with 2 main problems:
* _keyboard shortcuts didn't work_ (switch languages, opening terminal...) - fixed that after [FONT=Ubuntu Mono][COLOR=#ff8c00]unity --reset-icons[/COLOR].
[/FONT]* _internet menus and some other menus changed into Japanese, including Synaptic_ - still conflicting with that, i keep getting errors inside terminal, Synaptic and Chromium settings are in complete Japanese. i entered into the the language settings inside Chromium, all the languages there where English (US, Canada...) but it wrote it in Japanese. tried to change the default language - nothing worked.
when searching the system language in system settings, Japanese is not marked at all but all the languages' names are written in Japanese letters ('English' is shown as [SIZE=1][COLOR=#000000][FONT=HiraKakuPro-W3]&#33521;&#35486; [/FONT][/COLOR][/SIZE]which is /eigo/ - the Japanese name for the English language).

**EDDITED:**
i did a normal sudo apt-get upgrade to my system the i got a line with perl and a warning. a search through the web and the results sent me to check locale and i found something weird.

                         
$ sudoedit /etc/default/locale - sent me into an edit window in terminal that showed the following:
```
LANG="en_US.UTF-8"
LC_NUMERIC="he_IL.UTF-8"
LC_TIME="he_IL.UTF-8"
LC_MONETARY="he_IL.UTF-8"
LC_PAPER="he_IL.UTF-8"
LC_NAME="he_IL.UTF-8"
LC_ADDRESS="he_IL.UTF-8"
LC_TELEPHONE="he_IL.UTF-8"
LC_MEASUREMENT="he_IL.UTF-8"
LC_IDENTIFICATION="he_IL.UTF-8"

```
but when i entered locale in terminal i got different results, and the ALL is empty(...?)
```
$ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=ja_JP.UTF-8
LANGUAGE=ja:en
LC_CTYPE="ja_JP.UTF-8"
LC_NUMERIC=he_IL.UTF-8
LC_TIME=he_IL.UTF-8
LC_COLLATE="ja_JP.UTF-8"
LC_MONETARY=he_IL.UTF-8
LC_MESSAGES="ja_JP.UTF-8"
LC_PAPER=he_IL.UTF-8
LC_NAME=he_IL.UTF-8
LC_ADDRESS=he_IL.UTF-8
LC_TELEPHONE=he_IL.UTF-8
LC_MEASUREMENT=he_IL.UTF-8
LC_IDENTIFICATION=he_IL.UTF-8
LC_ALL=

```

my question about this: how to fix this mess of languages in locale?

this was the topic before edditing.

```
i searched through many sites but non seemed to have my problem, so i searched a way to reset all back to default, but when following the following link:
[http://www.itworld.com/software/416001/reset-unity-desktop-ubuntu-1404](http://www.itworld.com/software/416001/reset-unity-desktop-ubuntu-1404)
the 3rd code doesn't quit. this is what i get:
[CODE]shayli147@shayli:~$ setsid unity
shayli147@shayli:~$ unity-panel-service stop/waiting
unity-panel-service start/running, process 5087
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell


(process:5086): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
WARN  2014-04-25 21:18:49 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.Shell' yet as we don't have a connection, waiting for it...
ERROR 2014-04-25 21:18:49 unity.debug.interface DebugDBusInterface.cpp:196 Unable to load entry point in libxpathselect: libxpathselect.so.1.4: cannot open shared object file: No such file or directory
WARN  2014-04-25 21:18:49 xim.controller XIMController.cpp:103 IBus natively supported.
WARN  2014-04-25 21:18:50 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2014-04-25 21:18:50 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2014-04-25 21:18:50 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
WARN  2014-04-25 21:18:50 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Session' yet as we don't have a connection, waiting for it...
WARN  2014-04-25 21:18:50 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.ScreenSaver' yet as we don't have a connection, waiting for it...
ERROR 2014-04-25 21:18:50 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'org.gnome.Shell'
ERROR 2014-04-25 21:18:50 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'com.canonical.Unity'

```

i specially wonder about the lines:
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
and all the lines that have the following : "Can't register object '(org/com things)' yet as we don't have a connection, waiting for it..."
[/CODE]
so 3 questions:
1. how to completely remove Japanese support?
2. how to reset all settings back to the default installation?
3. what could be the meaning of the lines i specified? do i miss anything on my computer? 

if any additional info is needed about my computer it is here:
note: i added RAM into it so instead of 1GB it has got 4GB.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01127549&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=3470114&query=pavilion%20a6120.is&tool=](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01127549&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=3470114&query=pavilion%20a6120.is&tool=)

---

### Post by shayli147 on 2014-04-25
found the problem,
i had an out-of-date nvidia driver, updated to the new one, restarted computer and all problems are gone

here is what i did if anyone will ever need:
sudo apt-get purge nvidia-304
sudo apt-get install nvidia-331[COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]then restarting.

---

