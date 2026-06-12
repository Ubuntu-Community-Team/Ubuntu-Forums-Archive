---
title: "glslideshow has disappeared?"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by cfogelberg on 2010-05-24
Hello,

I am having real problems configuring and using glslideshow as my screensaver, and now it has disappeared completely from the list of screensavers in the gnome-screensaver-preferences app. If anyone can help me get it back and configure it that would be great!

I have a Dell XPS M1330 and have just installed Lucid (formatted my partitions and started from scratch).

After installing Lucid, I first of all created the file ~/.xscreensaver with the following text in it:

```
imageDirectory:	/common/core-data/screensaver-pics
```

This worked, but it panned and zoomed the pictures, so I edited /usr/share/applications/screensavers/glslideshow.desktop to be the following:

```
[Desktop Entry]
Name=GLSlideshow
Exec=/usr/lib/xscreensaver/glslideshow -root -zoom 100 -pan 0
TryExec=/usr/lib/xscreensaver/glslideshow
Comment=Loads a random sequence of images and smoothly scans and zooms around in each, fading from pan to pan. Written by Jamie Zawinski and Mike Oliphant.
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver
OnlyShowIn=GNOME;

```

This seems right to me, but now glslideshow does not even show up in gnome-screensaver-preferences. Grr. I have looked at other .desktop files, and their don't seem to be any obvious syntax errors in the above. Likewise, its permission and ownership are as for the other screensavers' .desktop files.

Further diagnostic information:
 * Operating System: Lucid 64 bit
 * Computer: Dell XPS M1330
 * gnome-screensaver Version: 2.30.0
 * gnome-screensaver-command --exit: No output
 * gnome-screensaver --no-daemon --debug: Generated the following output and then hung/waited:

```

[gs_debug_init] gs-debug.c:106 (13:41:05):	 Debugging enabled
[main] gnome-screensaver.c:87 (13:41:05):	 initializing gnome-screensaver 2.30.0
[init_session_id] gs-listener-dbus.c:2047 (13:41:05):	 Got session-id: /org/freedesktop/ConsoleKit/Session2
[gs_fade_init] gs-fade.c:906 (13:41:05):	 Fade type: 2
[set_status] gs-watcher-x11.c:345 (13:41:05):	 GSWatcher: not active, ignoring status changes
[gs_watcher_set_active] gs-watcher-x11.c:275 (13:41:05):	 turning watcher: ON
[listener_dbus_handle_system_message] gs-listener-dbus.c:1459 (13:41:05):	 obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameAcquired destination=:1.98
[listener_dbus_handle_system_message] gs-listener-dbus.c:1459 (13:41:05):	 obj_path=(null) interface=(null) method=(null) destination=:1.98
[listener_dbus_handle_system_message] gs-listener-dbus.c:1459 (13:41:05):	 obj_path=(null) interface=(null) method=(null) destination=:1.98
[listener_dbus_handle_system_message] gs-listener-dbus.c:1459 (13:41:05):	 obj_path=(null) interface=(null) method=(null) destination=:1.98
[listener_dbus_handle_system_message] gs-listener-dbus.c:1459 (13:41:05):	 obj_path=(null) interface=(null) method=(null) destination=:1.98
[on_bg_changed] gs-manager.c:954 (13:41:05):	 background changed

```

Have I made a syntax mistake, or do I need to get gnome-screensaver to refresh its list of screensavers somehow?

Thanks! :)
Christo

---

### Post by dino99 on 2010-05-24
xscreensaver-gl

---

### Post by cfogelberg on 2010-05-24
Hi Dino,

Thanks for your reply, but uh... Do you mean I should install that and it will magically reappear? If you have a fuller answer I would really appreciate it :)

Thanks,
Christo

---

### Post by cfogelberg on 2010-06-01
Hey all,

I discovered that the solution was: 
sudo apt-get install --reinstall gnome-screensaver

Cheers,
Christo

---

