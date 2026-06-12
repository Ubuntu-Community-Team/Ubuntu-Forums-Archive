---
title: "gnome-settings-daemon"
date: 2008-12-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by klein on 2008-12-19
Hi gang,

I think I've got a broken gnome-settings-daemon.  It crashes every time I run it.  Any way to fix?

```

mtklein@agamemnon:~$ gnome-settings-daemon --debug --no-daemon
** (gnome-settings-daemon:23075): DEBUG: Successfully connected to D-Bus
** (gnome-settings-daemon:23075): DEBUG: Starting settings manager
** (gnome-settings-daemon:23075): DEBUG: Loading settings plugins from dir: /usr/lib/gnome-settings-daemon-2.0/
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/keyboard.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='Keyboard' file='/usr/lib/gnome-settings-daemon-2.0/keyboard.gnome-settings-plugin' location='keyboard'
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/mouse.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='Mouse' file='/usr/lib/gnome-settings-daemon-2.0/mouse.gnome-settings-plugin' location='mouse'
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/a11y-keyboard.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='Accessibility Keyboard' file='/usr/lib/gnome-settings-daemon-2.0/a11y-keyboard.gnome-settings-plugin' location='a11y-keyboard'
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/xrdb.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='X Resource Database' file='/usr/lib/gnome-settings-daemon-2.0/xrdb.gnome-settings-plugin' location='xrdb'
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/media-keys.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='Media keys' file='/usr/lib/gnome-settings-daemon-2.0/media-keys.gnome-settings-plugin' location='media-keys'
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/font.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='Font' file='/usr/lib/gnome-settings-daemon-2.0/font.gnome-settings-plugin' location='font'
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/typing-break.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='Typing Break' file='/usr/lib/gnome-settings-daemon-2.0/typing-break.gnome-settings-plugin' location='typing-break'
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/housekeeping.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='Housekeeping' file='/usr/lib/gnome-settings-daemon-2.0/housekeeping.gnome-settings-plugin' location='housekeeping'
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/clipboard.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='Clipboard' file='/usr/lib/gnome-settings-daemon-2.0/clipboard.gnome-settings-plugin' location='clipboard'
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/dummy.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='Dummy' file='/usr/lib/gnome-settings-daemon-2.0/dummy.gnome-settings-plugin' location='dummy'
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/xsettings.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='X Settings' file='/usr/lib/gnome-settings-daemon-2.0/xsettings.gnome-settings-plugin' location='xsettings'
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/background.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='Background' file='/usr/lib/gnome-settings-daemon-2.0/background.gnome-settings-plugin' location='background'
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/keybindings.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='Keybindings' file='/usr/lib/gnome-settings-daemon-2.0/keybindings.gnome-settings-plugin' location='keybindings'
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/screensaver.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='Screensaver' file='/usr/lib/gnome-settings-daemon-2.0/screensaver.gnome-settings-plugin' location='screensaver'
** (gnome-settings-daemon:23075): DEBUG: Loading plugin: /usr/lib/gnome-settings-daemon-2.0/xrandr.gnome-settings-plugin
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsPluginInfo: name='XRandR' file='/usr/lib/gnome-settings-daemon-2.0/xrandr.gnome-settings-plugin' location='xrandr'
** (gnome-settings-daemon:23075): DEBUG: GnomeSettingsModule 0x8e81278 initialising
** (gnome-settings-daemon:23075): DEBUG: Loading /usr/lib/gnome-settings-daemon-2.0/libxrandr.so
** (gnome-settings-daemon:23075): DEBUG: Registering GsdXrandrPlugin
** (gnome-settings-daemon:23075): DEBUG: Creating object of type GsdXrandrPlugin
** (gnome-settings-daemon:23075): DEBUG: GsdXrandrPlugin initializing
** (gnome-settings-daemon:23075): DEBUG: Activating xrandr plugin
** (gnome-settings-daemon:23075): DEBUG: Starting xrandr manager
desired is = /home/mtklein/.config/monitors.xml.desired
reading configuration...
done
error MATCHESSegmentation fault

```

---

### Post by klein on 2008-12-19
Whoops, looks like this is a known bug:

[https://bugs.launchpad.net/gnome-settings-daemon/+bug/309602]("https://bugs.launchpad.net/gnome-settings-daemon/+bug/309602")

---

### Post by danf_1979 on 2008-12-19
It happens here too. I was going to report it today, but nice to know it was known.

---

