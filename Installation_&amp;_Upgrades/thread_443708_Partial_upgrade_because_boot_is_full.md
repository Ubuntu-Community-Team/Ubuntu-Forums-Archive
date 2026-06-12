---
title: "Partial upgrade because /boot is full"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by JPLGuy on 2007-05-14
Hello,

I recently upgraded to 7.04. Everything seemed to go smoothly an without any problems. However,  since then, whenever I use the update manager, it prompts me to do a "partial upgrade." 
I go ahead with it, and it tries and fails to do the update, with an error message saying (essentially) "/boot is full, please free at least 41.9 MB of space" 

I used the Disk Usage Analyzer,  and sure enough its full. How do I expand the size of that folder? I have ~60 gigs free on the drive. I checked out the partition tool (gpart ?) and it doesn't specifically mention /boot as a partition.

I tried removing some of the oldest kernel files in there, but that just decreased the overall size of /boot, instead of freeing space.

I did try Googling this, not much luck.

Any ideas? Thanks!

J

---

### Post by taurus on 2007-05-14
Boot into recovery mode from GRUB menu and post the output of this command here.

```
df -h
du -h /boot
```

---

### Post by JPLGuy on 2007-05-14
The output of both commands are pasted below. The du -h output has been edited for reasons of privacy and professional security.  I cut out a much larger portion so it would fit in the 40,000 character limit of the board.

So now that I know /boot is hda3, I can use gparted on my Live CD to resize it, correct? I will need to move two partitions (including my main one), but that shouldn't cause any data loss I hope. Given that I really don't want to risk losing my data unncessarily, I will wait to see if this is what you recommend I do before I go ahead and do it. 

Thanks for your help!


================
 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              97G   65G   28G  71% /
varrun                253M  116K  252M   1% /var/run
varlock               253M  4.0K  253M   1% /var/lock
procbususb            253M  128K  252M   1% /proc/bus/usb
udev                  253M  128K  252M   1% /dev
devshm                253M     0  253M   0% /dev/shm
lrm                   253M   34M  219M  14% /lib/modules/2.6.20-15-386/volatile
/dev/mapper/hda3       96M   96M     0 100% /boot
/dev/mapper/hdb1      128G   82G   47G  64% /media/hdb1
============


du -h
308K	./.vlc/cache
360K	./.vlc
8.0K	./.gconf/desktop/gnome/accessibility/keyboard
12K	./.gconf/desktop/gnome/accessibility
8.0K	./.gconf/desktop/gnome/peripherals/keyboard/host-jbdesktop/0
12K	./.gconf/desktop/gnome/peripherals/keyboard/host-jbdesktop
16K	./.gconf/desktop/gnome/peripherals/keyboard
20K	./.gconf/desktop/gnome/peripherals
8.0K	./.gconf/desktop/gnome/interface
8.0K	./.gconf/desktop/gnome/screen/default/0
12K	./.gconf/desktop/gnome/screen/default
8.0K	./.gconf/desktop/gnome/screen/jbdesktop/0
12K	./.gconf/desktop/gnome/screen/jbdesktop
28K	./.gconf/desktop/gnome/screen
8.0K	./.gconf/desktop/gnome/background
8.0K	./.gconf/desktop/gnome/url-handlers/sip
12K	./.gconf/desktop/gnome/url-handlers
8.0K	./.gconf/desktop/gnome/volume_manager
8.0K	./.gconf/desktop/gnome/applications/window_manager
12K	./.gconf/desktop/gnome/applications
112K	./.gconf/desktop/gnome
116K	./.gconf/desktop
8.0K	./.gconf/apps/nautilus/preferences
16K	./.gconf/apps/nautilus
8.0K	./.gconf/apps/evolution/calendar/notify
8.0K	./.gconf/apps/evolution/calendar/memos
8.0K	./.gconf/apps/evolution/calendar/tasks
8.0K	./.gconf/apps/evolution/calendar/display
40K	./.gconf/apps/evolution/calendar
8.0K	./.gconf/apps/evolution/mail/composer
16K	./.gconf/apps/evolution/mail
12K	./.gconf/apps/evolution/general
8.0K	./.gconf/apps/evolution/tasks
8.0K	./.gconf/apps/evolution/memos
8.0K	./.gconf/apps/evolution/addressbook/display
16K	./.gconf/apps/evolution/addressbook
8.0K	./.gconf/apps/evolution/shell/view_defaults/folder_bar
16K	./.gconf/apps/evolution/shell/view_defaults
24K	./.gconf/apps/evolution/shell
132K	./.gconf/apps/evolution
8.0K	./.gconf/apps/panel/applets/clock_screen0/prefs
16K	./.gconf/apps/panel/applets/clock_screen0
8.0K	./.gconf/apps/panel/applets/trashapplet_screen0
8.0K	./.gconf/apps/panel/applets/workspace_switcher_screen0/prefs
16K	./.gconf/apps/panel/applets/workspace_switcher_screen0
8.0K	./.gconf/apps/panel/applets/window_list_screen0/prefs
16K	./.gconf/apps/panel/applets/window_list_screen0
8.0K	./.gconf/apps/panel/applets/show_desktop_button_screen0
8.0K	./.gconf/apps/panel/applets/notification_area_screen0
8.0K	./.gconf/apps/panel/applets/mixer_screen0
84K	./.gconf/apps/panel/applets
8.0K	./.gconf/apps/panel/objects/menu_bar_screen0
8.0K	./.gconf/apps/panel/objects/session_dialog_screen0
8.0K	./.gconf/apps/panel/objects/yelp_launcher_screen0
8.0K	./.gconf/apps/panel/objects/email_launcher_screen0
8.0K	./.gconf/apps/panel/objects/browser_launcher_screen0
8.0K	./.gconf/apps/panel/objects/object_0
52K	./.gconf/apps/panel/objects
8.0K	./.gconf/apps/panel/general
8.0K	./.gconf/apps/panel/toplevels/bottom_panel_screen0/background
16K	./.gconf/apps/panel/toplevels/bottom_panel_screen0
8.0K	./.gconf/apps/panel/toplevels/top_panel_screen0/background
16K	./.gconf/apps/panel/toplevels/top_panel_screen0
36K	./.gconf/apps/panel/toplevels
184K	./.gconf/apps/panel
8.0K	./.gconf/apps/metacity/general
8.0K	./.gconf/apps/metacity/global_keybindings
8.0K	./.gconf/apps/metacity/keybinding_commands
8.0K	./.gconf/apps/metacity/window_keybindings
36K	./.gconf/apps/metacity
8.0K	./.gconf/apps/totem
8.0K	./.gconf/apps/update-manager
8.0K	./.gconf/apps/file-roller/ui
8.0K	./.gconf/apps/file-roller/listing
8.0K	./.gconf/apps/file-roller/general
8.0K	./.gconf/apps/file-roller/dialogs/extract
8.0K	./.gconf/apps/file-roller/dialogs/batch-add
20K	./.gconf/apps/file-roller/dialogs
48K	./.gconf/apps/file-roller
8.0K	./.gconf/apps/gedit-2/preferences/ui/statusbar
8.0K	./.gconf/apps/gedit-2/preferences/ui/side_pane
8.0K	./.gconf/apps/gedit-2/preferences/ui/toolbar
28K	./.gconf/apps/gedit-2/preferences/ui
8.0K	./.gconf/apps/gedit-2/preferences/editor/font
8.0K	./.gconf/apps/gedit-2/preferences/editor/auto_indent
20K	./.gconf/apps/gedit-2/preferences/editor
52K	./.gconf/apps/gedit-2/preferences
56K	./.gconf/apps/gedit-2
8.0K	./.gconf/apps/eog/ui
8.0K	./.gconf/apps/eog/window
20K	./.gconf/apps/eog
8.0K	./.gconf/apps/gnome-terminal/profiles/Default
12K	./.gconf/apps/gnome-terminal/profiles
16K	./.gconf/apps/gnome-terminal
8.0K	./.gconf/apps/gnometris/options
12K	./.gconf/apps/gnometris
16K	./.gconf/apps/gnome-screensaver
8.0K	./.gconf/apps/rhythmbox/plugins/cd-recorder
8.0K	./.gconf/apps/rhythmbox/plugins/ipod
8.0K	./.gconf/apps/rhythmbox/plugins/generic-player
8.0K	./.gconf/apps/rhythmbox/plugins/audiocd
8.0K	./.gconf/apps/rhythmbox/plugins/daap
8.0K	./.gconf/apps/rhythmbox/plugins/visualizer
8.0K	./.gconf/apps/rhythmbox/plugins/mmkeys
8.0K	./.gconf/apps/rhythmbox/plugins/iradio
8.0K	./.gconf/apps/rhythmbox/plugins/power-manager
8.0K	./.gconf/apps/rhythmbox/plugins/artdisplay
84K	./.gconf/apps/rhythmbox/plugins
8.0K	./.gconf/apps/rhythmbox/ui
8.0K	./.gconf/apps/rhythmbox/state/podcast
8.0K	./.gconf/apps/rhythmbox/state/library
8.0K	./.gconf/apps/rhythmbox/state/iradio
32K	./.gconf/apps/rhythmbox/state
132K	./.gconf/apps/rhythmbox
8.0K	./.gconf/apps/f-spot/screensaver
12K	./.gconf/apps/f-spot
8.0K	./.gconf/apps/celestia/labels
8.0K	./.gconf/apps/celestia/render
8.0K	./.gconf/apps/celestia/orbits
32K	./.gconf/apps/celestia
8.0K	./.gconf/apps/procman/disktreenew
12K	./.gconf/apps/procman/proctree
28K	./.gconf/apps/procman
8.0K	./.gconf/apps/gnome-settings/gedit
8.0K	./.gconf/apps/gnome-settings/gnome-session-properties
8.0K	./.gconf/apps/gnome-settings/gnome-search-tool
8.0K	./.gconf/apps/gnome-settings/gnome-desktop-item-edit
36K	./.gconf/apps/gnome-settings
8.0K	./.gconf/apps/gcalctool
8.0K	./.gconf/apps/update-notifier
8.0K	./.gconf/apps/gnome-screenshot
8.0K	./.gconf/apps/gnome-search-tool/select
16K	./.gconf/apps/gnome-search-tool
8.0K	./.gconf/apps/gnome-volume-control/ui
12K	./.gconf/apps/gnome-volume-control
8.0K	./.gconf/apps/ekiga/protocols
8.0K	./.gconf/apps/ekiga/devices/video
8.0K	./.gconf/apps/ekiga/devices/audio
20K	./.gconf/apps/ekiga/devices
8.0K	./.gconf/apps/ekiga/general/nat
8.0K	./.gconf/apps/ekiga/general/sound_events
8.0K	./.gconf/apps/ekiga/general/user_interface/main_window
8.0K	./.gconf/apps/ekiga/general/user_interface/druid_window
8.0K	./.gconf/apps/ekiga/general/user_interface/preferences_window
28K	./.gconf/apps/ekiga/general/user_interface
8.0K	./.gconf/apps/ekiga/general/personal_data
60K	./.gconf/apps/ekiga/general
8.0K	./.gconf/apps/ekiga/codecs/video
12K	./.gconf/apps/ekiga/codecs
104K	./.gconf/apps/ekiga
8.0K	./.gconf/apps/multisync/main
12K	./.gconf/apps/multisync
8.0K	./.gconf/apps/GnomeBaker/Devices/Device01
12K	./.gconf/apps/GnomeBaker/Devices
8.0K	./.gconf/apps/GnomeBaker/UI
28K	./.gconf/apps/GnomeBaker
8.0K	./.gconf/apps/serpentine
8.0K	./.gconf/apps/compiz/plugins/fade/screen0/options
12K	./.gconf/apps/compiz/plugins/fade/screen0
16K	./.gconf/apps/compiz/plugins/fade
20K	./.gconf/apps/compiz/plugins
8.0K	./.gconf/apps/compiz/general/screen0/options
12K	./.gconf/apps/compiz/general/screen0
12K	./.gconf/apps/compiz/general/allscreens/options
16K	./.gconf/apps/compiz/general/allscreens
32K	./.gconf/apps/compiz/general
56K	./.gconf/apps/compiz
8.0K	./.gconf/apps/tomboy
8.0K	./.gconf/apps/baobab/ui
12K	./.gconf/apps/baobab
1.1M	./.gconf/apps
8.0K	./.gconf/system/gstreamer/0.10/default
12K	./.gconf/system/gstreamer/0.10
16K	./.gconf/system/gstreamer
20K	./.gconf/system
8.0K	./.gconf/GNOME/Spell
12K	./.gconf/GNOME
1.2M	./.gconf
64K	./.gconfd
52K	./.gnome2/accels
4.0K	./.gnome2/keyrings
8.0K	./.gnome2/share/fonts
8.0K	./.gnome2/share/cursor-fonts
20K	./.gnome2/share
8.0K	./.gnome2/panel2.d/default/launchers
12K	./.gnome2/panel2.d/default
16K	./.gnome2/panel2.d
4.0K	./.gnome2/nautilus-scripts
4.0K	./.gnome2/network-admin-locations
4.0K	./.gnome2/file-roller
8.0K	./.gnome2/vfolders/applications
12K	./.gnome2/vfolders
4.0K	./.gnome2/gnometris.d
1.5M	./.gnome2/rhythmbox/covers
2.6M	./.gnome2/rhythmbox
20K	./.gnome2/evince
44K	./.gnome2/f-spot
336K	./.gnome2/yelp.d
12K	./.gnome2/gnome-pilot.d
3.2M	./.gnome2
4.0K	./.gnome2_private
500K	./.gstreamer-0.10
136K	./.nautilus/metafiles
1012K	./.nautilus
12K	./.ssh
3.5G	./Desktop
8.0K	./.gnome/gnome-vfs
12K	./.gnome
1.1M	./.metacity/sessions
1.2M	./.metacity
4.0K	./.Trash
32K	./.xine
28M	./.thumbnails/normal
1.8M	./.thumbnails/fail/gnome-thumbnail-factory
1.8M	./.thumbnails/fail
4.0K	./.thumbnails/large
30M	./.thumbnails
4.0K	./.themes
4.0K	./.icons
8.0K	./.config/gtk-2.0
24K	./.config/menus
16K	./.config/autostart
52K	./.config
12K	./.mozilla/firefox/udmsdwhk.default/chrome
24K	./.mozilla/firefox/udmsdwhk.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/components
8.0K	./.mozilla/firefox/udmsdwhk.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/defaults/preferences
12K	./.mozilla/firefox/udmsdwhk.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/defaults
948K	./.mozilla/firefox/udmsdwhk.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/chrome
1004K	./.mozilla/firefox/udmsdwhk.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}
92K	./.mozilla/firefox/udmsdwhk.default/extensions/{19503e42-ca3c-4c27-b1e2-9cdb2170ee34}/components
644K	./.mozilla/firefox/udmsdwhk.default/extensions/{19503e42-ca3c-4c27-b1e2-9cdb2170ee34}/chrome
8.0K	./.mozilla/firefox/udmsdwhk.default/extensions/{19503e42-ca3c-4c27-b1e2-9cdb2170ee34}/defaults/preferences
12K	./.mozilla/firefox/udmsdwhk.default/extensions/{19503e42-ca3c-4c27-b1e2-9cdb2170ee34}/defaults
800K	./.mozilla/firefox/udmsdwhk.default/extensions/{19503e42-ca3c-4c27-b1e2-9cdb2170ee34}
32K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/mn-MN
32K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/ko-KR
40K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/ru-RU
32K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/en-GB
32K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/cs-CZ
32K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/fr-FR
32K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/pl-PL
32K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/nl-NL
32K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/de-DE
28K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/zh-TW
28K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/zh-CN
32K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/es-AR
32K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/it-IT
32K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/sk-SK
32K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/fi-FI
32K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4/ro-RO
516K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.4.4
520K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations
72K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/content/colorPicker
260K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/content
44K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/skin/classic
48K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/skin
32K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/locale/en-US
36K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/locale
348K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome
12K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/defaults/preferences
16K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/defaults
896K	./.mozilla/firefox/udmsdwhk.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}
16K	./.mozilla/firefox/udmsdwhk.default/extensions/{C0D0F6D1-9FC9-4b0a-B485-D5E13AF40D51}/META-INF
36K	./.mozilla/firefox/udmsdwhk.default/extensions/{C0D0F6D1-9FC9-4b0a-B485-D5E13AF40D51}/chrome
64K	./.mozilla/firefox/udmsdwhk.default/extensions/{C0D0F6D1-9FC9-4b0a-B485-D5E13AF40D51}
88K	./.mozilla/firefox/udmsdwhk.default/extensions/{3d7eb24f-2740-49df-8937-200b1cc08f8a}/chrome
8.0K	./.mozilla/firefox/udmsdwhk.default/extensions/{3d7eb24f-2740-49df-8937-200b1cc08f8a}/defaults/preferences
12K	./.mozilla/firefox/udmsdwhk.default/extensions/{3d7eb24f-2740-49df-8937-200b1cc08f8a}/defaults
112K	./.mozilla/firefox/udmsdwhk.default/extensions/{3d7eb24f-2740-49df-8937-200b1cc08f8a}
48K	./.mozilla/firefox/udmsdwhk.default/extensions/{0538E3E3-7E9B-4d49-8831-A227C80A7AD3}/components
912K	./.mozilla/firefox/udmsdwhk.default/extensions/{0538E3E3-7E9B-4d49-8831-A227C80A7AD3}/chrome
12K	./.mozilla/firefox/udmsdwhk.default/extensions/{0538E3E3-7E9B-4d49-8831-A227C80A7AD3}/defaults/preferences
236K	./.mozilla/firefox/udmsdwhk.default/extensions/{0538E3E3-7E9B-4d49-8831-A227C80A7AD3}/defaults
1.2M	./.mozilla/firefox/udmsdwhk.default/extensions/{0538E3E3-7E9B-4d49-8831-A227C80A7AD3}
2.1M	./.mozilla/firefox/udmsdwhk.default/extensions/{00df3690-c341-11da-a94d-0800200c9a66}/chrome
2.1M	./.mozilla/firefox/udmsdwhk.default/extensions/{00df3690-c341-11da-a94d-0800200c9a66}
6.2M	./.mozilla/firefox/udmsdwhk.default/extensions
344K	./.mozilla/firefox/udmsdwhk.default/bookmarkbackups
572K	./.mozilla/firefox/udmsdwhk.default/Cache
412K	./.mozilla/firefox/udmsdwhk.default/adblockplus
8.0K	./.mozilla/firefox/udmsdwhk.default/forecastfox/errors
188K	./.mozilla/firefox/udmsdwhk.default/forecastfox/icons
28K	./.mozilla/firefox/udmsdwhk.default/forecastfox/cache
240K	./.mozilla/firefox/udmsdwhk.default/forecastfox
16M	./.mozilla/firefox/udmsdwhk.default
16M	./.mozilla/firefox
20K	./.mozilla/default/g7h3uhvl.slt/chrome
30M	./.mozilla/default/g7h3uhvl.slt/Cache
4.0K	./.mozilla/default/g7h3uhvl.slt/Cache.Trash
30M	./.mozilla/default/g7h3uhvl.slt
30M	./.mozilla/default
46M	./.mozilla
8.0K	./.update-notifier
4.0K	./.wine/dosdevices
52K	./.wine/drive_c/windows/command
4.0K	./.wine/drive_c/windows/fonts
168K	./.wine/drive_c/windows/inf
4.0K	./.wine/drive_c/windows/system
4.0K	./.wine/drive_c/windows/system32/drivers
2.1M	./.wine/drive_c/windows/system32
548K	./.wine/drive_c/windows/temp/{EF434C52-D882-43DB-8777-EC7B10D8943C}
9.9M	./.wine/drive_c/windows/temp
4.0K	./.wine/drive_c/windows/profiles/jburkert/Local Settings/Temporary Internet Files
4.0K	./.wine/drive_c/windows/profiles/jburkert/Local Settings/History
4.0K	./.wine/drive_c/windows/profiles/jburkert/Local Settings/Application Data
16K	./.wine/drive_c/windows/profiles/jburkert/Local Settings
4.0K	./.wine/drive_c/windows/profiles/jburkert/Cookies
4.0K	./.wine/drive_c/windows/profiles/jburkert/Start Menu/Programs/StartUp
8.0K	./.wine/drive_c/windows/profiles/jburkert/Start Menu/Programs
12K	./.wine/drive_c/windows/profiles/jburkert/Start Menu
4.0K	./.wine/drive_c/windows/profiles/jburkert/Favorites
4.0K	./.wine/drive_c/windows/profiles/jburkert/Application Data
4.0K	./.wine/drive_c/windows/profiles/jburkert/Recent
4.0K	./.wine/drive_c/windows/profiles/jburkert/SendTo
4.0K	./.wine/drive_c/windows/profiles/jburkert/NetHood
4.0K	./.wine/drive_c/windows/profiles/jburkert/Templates
4.0K	./.wine/drive_c/windows/profiles/jburkert/PrintHood
64K	./.wine/drive_c/windows/profiles/jburkert
4.0K	./.wine/drive_c/windows/profiles/All Users/Start Menu/Programs/StartUp
8.0K	./.wine/drive_c/windows/profiles/All Users/Start Menu/Programs
12K	./.wine/drive_c/windows/profiles/All Users/Start Menu
4.0K	./.wine/drive_c/windows/profiles/All Users/Desktop
4.0K	./.wine/drive_c/windows/profiles/All Users/Favorites
4.0K	./.wine/drive_c/windows/profiles/All Users/Application Data
4.0K	./.wine/drive_c/windows/profiles/All Users/Templates
4.0K	./.wine/drive_c/windows/profiles/All Users/Documents
36K	./.wine/drive_c/windows/profiles/All Users
104K	./.wine/drive_c/windows/profiles
13M	./.wine/drive_c/windows
2.1M	./.wine/drive_c/Program Files/Common Files/InstallShield/Driver/9/Intel 32
2.1M	./.wine/drive_c/Program Files/Common Files/InstallShield/Driver/9
2.1M	./.wine/drive_c/Program Files/Common Files/InstallShield/Driver
2.1M	./.wine/drive_c/Program Files/Common Files/InstallShield
2.1M	./.wine/drive_c/Program Files/Common Files
2.1M	./.wine/drive_c/Program Files
15M	./.wine/drive_c
16M	./.wine
8.0K	./.update-manager

....

32G	.

---

### Post by taurus on 2007-05-14
Actually, the second command is for /boot, not your $HOME directory since /boot is the one at 100% capacity.

```
sudo du -h /boot
```

---

### Post by JPLGuy on 2007-05-14
Oh whoops...

Here ya go...

12K     /boot/lost+found
169K    /boot/grub
52M     /boot/.Trash-root
92M     /boot

Huh, I guess /boot/.Trash-root is huge...  I guess I could delete all the stuff in there... lots easier than partitioning... 

I moved .Trash-root to a backup location off /boot and reran the update manager. Voila! 

Thanks for the help!

---

### Post by psusi on 2007-05-14
Deleting old kernels from /boot DOES free up the space.  I ran into this problem while upgrading too.  I think there is a bug in the upgrade process that requires more free space in /boot than it should.  Free up more space and it should work.

---

