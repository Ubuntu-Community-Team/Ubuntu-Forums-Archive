---
title: "gnome-settings-daemon crashes on Ubuntu Server 8.10 beta"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by JasonWalton on 2008-10-21
Had a hard drive crash this weekend, so rebuilt my server with 8.10 beta.  I like to run a VNC server on this machine, mainly so I can use it to download files/torrents since this machine is the only one in the house that's always on.

Here's the (relevant) setup:

[LIST]
[*]Install Ubuntu Server 8.10 beta (with software RAID-1 this time :).
[*]sudo apt-get install gnome-core tightvncserver
[*]vncserver
[/LIST]

The problem is, gnome-settings-manager seems to die whenever it tries to start.  Going to "System->Preferences->Appearance" gets you the "Unable to start the settings manager 'gnome-settings-daemon'." message.  Trying to start it from the command line with debugging turned on gives some interesting output (especially the segfault), but nothing in there stands out to me as a smoking gun.  Any thoughts?

Here's the debug output:

```

$ gnome-settings-daemon --no-daemon --debug
Xlib:  extension "RANDR" missing on display ":1.0".
** (gnome-settings-daemon:28445): DEBUG: Successfully connected to D-Bus
** (gnome-settings-daemon:28445): DEBUG: Starting settings manager
** (gnome-settings-daemon:28445): DEBUG: Loading settings plugins from dir: /usr/lib/gnome-settings-daemon-2.0/
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/xsettings.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='X Settings' file='/usr/lib/gnome-settings-daemon-2.0/xsettings.gnome-settings-plugin' location='xsettings'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/xsettings for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/media-keys.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='Media keys' file='/usr/lib/gnome-settings-daemon-2.0/media-keys.gnome-settings-plugin' location='media-keys'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/media-keys for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/a11y-keyboard.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='Accessibility Keyboard' file='/usr/lib/gnome-settings-daemon-2.0/a11y-keyboard.gnome-settings-plugin' location='a1
1y-keyboard'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/a11y-keyboard for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/dummy.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='Dummy' file='/usr/lib/gnome-settings-daemon-2.0/dummy.gnome-settings-plugin' location='dummy'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/dummy for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/xrdb.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='X Resource Database' file='/usr/lib/gnome-settings-daemon-2.0/xrdb.gnome-settings-plugin' location='xrdb'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/xrdb for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/mouse.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='Mouse' file='/usr/lib/gnome-settings-daemon-2.0/mouse.gnome-settings-plugin' location='mouse'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/mouse for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/keyboard.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='Keyboard' file='/usr/lib/gnome-settings-daemon-2.0/keyboard.gnome-settings-plugin' location='keyboard'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/keyboard for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/sound.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='Sound' file='/usr/lib/gnome-settings-daemon-2.0/sound.gnome-settings-plugin' location='sound'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/sound for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/font.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='Font' file='/usr/lib/gnome-settings-daemon-2.0/font.gnome-settings-plugin' location='font'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/font for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/keybindings.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='Keybindings' file='/usr/lib/gnome-settings-daemon-2.0/keybindings.gnome-settings-plugin' location='keybindings'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/keybindings for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/screensaver.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='Screensaver' file='/usr/lib/gnome-settings-daemon-2.0/screensaver.gnome-settings-plugin' location='screensaver'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/screensaver for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/typing-break.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='Typing Break' file='/usr/lib/gnome-settings-daemon-2.0/typing-break.gnome-settings-plugin' location='typing-break'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/typing-break for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/background.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='Background' file='/usr/lib/gnome-settings-daemon-2.0/background.gnome-settings-plugin' location='background'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/background for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/clipboard.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='Clipboard' file='/usr/lib/gnome-settings-daemon-2.0/clipboard.gnome-settings-plugin' location='clipboard'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/clipboard for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/xrandr.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='XRandR' file='/usr/lib/gnome-settings-daemon-2.0/xrandr.gnome-settings-plugin' location='xrandr'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/xrandr for changes
** (gnome-settings-daemon:28445): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/housekeeping.gnome-settings-plugin
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsPluginInfo: name='Housekeeping' file='/usr/lib/gnome-settings-daemon-2.0/housekeeping.gnome-settings-plugin' location='housekeeping'
** (gnome-settings-daemon:28445): DEBUG: Monitoring dir /apps/gnome_settings_daemon/plugins/housekeeping for changes
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsModule 0x90f22c8 initialising
** (gnome-settings-daemon:28445): DEBUG: Loading /usr/lib/gnome-settings-daemon-2.0/libxrandr.so
** (gnome-settings-daemon:28445): DEBUG: Registering GsdXrandrPlugin
** (gnome-settings-daemon:28445): DEBUG: Creating object of type GsdXrandrPlugin
** (gnome-settings-daemon:28445): DEBUG: GsdXrandrPlugin initializing
** (gnome-settings-daemon:28445): DEBUG: Activating xrandr plugin
** (gnome-settings-daemon:28445): DEBUG: Starting xrandr manager

** (gnome-settings-daemon:28445): WARNING **: Unable to start xrandr manager: Failed to initialize XRandR extension
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsManager: emitting plugin-activated xrandr
** (gnome-settings-daemon:28445): DEBUG: Plugin xrandr: active
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsModule 0x90f2318 initialising
** (gnome-settings-daemon:28445): DEBUG: Loading /usr/lib/gnome-settings-daemon-2.0/libxsettings.so
** (gnome-settings-daemon:28445): DEBUG: Registering GnomeXSettingsPlugin
** (gnome-settings-daemon:28445): DEBUG: Creating object of type GnomeXSettingsPlugin
** (gnome-settings-daemon:28445): DEBUG: GnomeXSettingsPlugin initializing
** (gnome-settings-daemon:28445): DEBUG: Activating xsettings plugin
** (gnome-settings-daemon:28445): DEBUG: Starting xsettings manager
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsManager: emitting plugin-activated xsettings
** (gnome-settings-daemon:28445): DEBUG: Plugin xsettings: active
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsModule 0x9118478 initialising
** (gnome-settings-daemon:28445): DEBUG: Loading /usr/lib/gnome-settings-daemon-2.0/libsound.so
** (gnome-settings-daemon:28445): DEBUG: Registering GsdSoundPlugin
** (gnome-settings-daemon:28445): DEBUG: Creating object of type GsdSoundPlugin
** (gnome-settings-daemon:28445): DEBUG: GsdSoundPlugin initializing
** (gnome-settings-daemon:28445): DEBUG: Activating sound plugin
** (gnome-settings-daemon:28445): DEBUG: Starting sound manager
Could not start esd: Failed to execute child process "esd" (No such file or directory)
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsManager: emitting plugin-activated sound
** (gnome-settings-daemon:28445): DEBUG: Plugin sound: active
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsModule 0x91184c8 initialising
** (gnome-settings-daemon:28445): DEBUG: Loading /usr/lib/gnome-settings-daemon-2.0/libfont.so
** (gnome-settings-daemon:28445): DEBUG: Registering GsdFontPlugin
** (gnome-settings-daemon:28445): DEBUG: Creating object of type GsdFontPlugin
** (gnome-settings-daemon:28445): DEBUG: GsdFontPlugin initializing
** (gnome-settings-daemon:28445): DEBUG: Activating font plugin
** (gnome-settings-daemon:28445): DEBUG: Starting font manager
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsManager: emitting plugin-activated font
** (gnome-settings-daemon:28445): DEBUG: Plugin font: active
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsModule 0x9118518 initialising
** (gnome-settings-daemon:28445): DEBUG: Loading /usr/lib/gnome-settings-daemon-2.0/libbackground.so
** (gnome-settings-daemon:28445): DEBUG: Registering GsdBackgroundPlugin
** (gnome-settings-daemon:28445): DEBUG: Creating object of type GsdBackgroundPlugin
** (gnome-settings-daemon:28445): DEBUG: GsdBackgroundPlugin initializing
** (gnome-settings-daemon:28445): DEBUG: Activating background plugin
** (gnome-settings-daemon:28445): DEBUG: Starting background manager
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsManager: emitting plugin-activated background
** (gnome-settings-daemon:28445): DEBUG: Plugin background: active
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsModule 0x9118590 initialising
** (gnome-settings-daemon:28445): DEBUG: Loading /usr/lib/gnome-settings-daemon-2.0/libkeyboard.so
** (gnome-settings-daemon:28445): DEBUG: Registering GsdKeyboardPlugin
** (gnome-settings-daemon:28445): DEBUG: Creating object of type GsdKeyboardPlugin
** (gnome-settings-daemon:28445): DEBUG: GsdKeyboardPlugin initializing
** (gnome-settings-daemon:28445): DEBUG: Activating keyboard plugin
** (gnome-settings-daemon:28445): DEBUG: Starting keyboard manager

** (gnome-settings-daemon:28445): WARNING **: XKB extension not available

** (gnome-settings-daemon:28445): WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsManager: emitting plugin-activated keyboard
** (gnome-settings-daemon:28445): DEBUG: Plugin keyboard: active
** (gnome-settings-daemon:28445): DEBUG: GnomeSettingsModule 0x91184a0 initialising
** (gnome-settings-daemon:28445): DEBUG: Loading /usr/lib/gnome-settings-daemon-2.0/libmouse.so
** (gnome-settings-daemon:28445): DEBUG: Registering GsdMousePlugin
** (gnome-settings-daemon:28445): DEBUG: Creating object of type GsdMousePlugin
** (gnome-settings-daemon:28445): DEBUG: GsdMousePlugin initializing
** (gnome-settings-daemon:28445): DEBUG: Activating mouse plugin
** (gnome-settings-daemon:28445): DEBUG: Starting mouse manager
Xlib:  extension "XInputExtension" missing on display ":1.0".
Shutdown failed or nothing to shut down.
Segmentation fault

```

---

### Post by louieb on 2008-10-21
> gets you the "Unable to start the settings manager 'gnome-settings-daemon'." message.

I get that message occasionally when logging on. Thats been happening since I 1st started using Ubuntu over 2 years ago. If you check  [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu")  you'll find 70 bugs reported. Just search on **gnome-settings-daemon**. Might look through them and see if theres a work around. 

Also if you confirm the bug chances are it will go higher on the priority list to get fixed.

---

