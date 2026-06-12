---
title: "Irregular automatic logouts of user and sometime hanging"
date: 2020-08-17
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2020-08-17
Within the past few day, my system started to behave oddly. Randomly, while using my system, it would automatically log me out or the screen appear a black with a white mouse pointer that responds sluggishly. 

Just within an hour, it occurred 4 times. I tried to press Ctrl+Alt+ (F1, F2, F3, F4, F5 or F6) but nothing happened. I could kind of "hear" my processes running behind the black screen.

My system has 5.4.0-42-generic #46~18.04.1-Ubuntu kernel and an Nvidia graphics card using NVidia driver metapackage from nvidia driver package 435 (proprietary), and GNOME Shell 3.28.4.

I have included the syslog during the occurrence of my issues below. Can you advice me what is the problem on my system and how i can fix it? Thanks.


_**Update:**_
I accidentally found a way to reproduce my issue. Every time I go into **Ubuntu Software** --> **Installed**  --> click the "Remove" button of an installed application, my system my wallpaer would change to another and freeze and would automatically log me out and I would loss my session. I have to login again to start a new session.

---

### Post by sunbear-c22 on 2020-08-17
_**syslog for the second occurrence.**_

```

Aug 18 01:53:23 Machine gnome-shell[22628]: message repeated 3 times: [ Ignoring excess values in shadow definition]
Aug 18 01:53:43 Machine gnome-shell[22628]: gdk_cairo_surface_create_from_pixbuf: assertion 'GDK_IS_PIXBUF (pixbuf)' failed
Aug 18 01:53:43 Machine org.gnome.Shell.desktop[22628]: **
Aug 18 01:53:43 Machine org.gnome.Shell.desktop[22628]: mutter:ERROR:core/window.c:5332:get_default_window_icon: assertion failed: (default_icon)
Aug 18 01:53:43 Machine org.gnome.Shell.desktop[22628]: == Stack trace for context 0x563d8f621330 ==
Aug 18 01:53:43 Machine systemd[1]: Starting Process error reports when automatic reporting is enabled...
Aug 18 01:53:54 Machine whoopsie-upload-all[25565]: ERROR: processing /var/crash/_usr_bin_gnome-shell.1000.crash: Compressed file ended before the end-of-stream marker was reached
Aug 18 01:53:54 Machine whoopsie-upload-all[25565]: /var/crash/_usr_lib_chromium-browser_chromium-browser.1000.crash already marked for upload, skipping
Aug 18 01:53:54 Machine whoopsie-upload-all[25565]: Collecting info for /var/crash/_usr_bin_gnome-shell.1000.crash...
Aug 18 01:53:54 Machine whoopsie-upload-all[25565]: All reports processed
Aug 18 01:53:54 Machine systemd[1]: Started Process error reports when automatic reporting is enabled.
Aug 18 01:54:26 Machine gnome-session-binary[22507]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 6
Aug 18 01:54:26 Machine gnome-session[22507]: gnome-session-binary[22507]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 6
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): CRT-0: disconnected
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0):
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-0: disconnected
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0):
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): connected
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): Internal TMDS
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): 340.0 MHz maximum pixel clock
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0):
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-2: disconnected
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0):
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-3: disconnected
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0):
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-4: disconnected
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0):
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): CRT-0: disconnected
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0):
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-0: disconnected
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0):
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): connected
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): Internal TMDS
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): 340.0 MHz maximum pixel clock
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0):
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-2: disconnected
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0):
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-3: disconnected
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0):
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-4: disconnected
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
Aug 18 01:54:26 Machine /usr/lib/gdm3/gdm-x-session[22495]: (--) NVIDIA(GPU-0):
Aug 18 01:54:26 Machine gsd-media-keys[22797]: g_variant_get_va: assertion 'value != NULL' failed
Aug 18 01:54:26 Machine gsd-media-keys[22797]: g_variant_unref: assertion 'value != NULL' failed
Aug 18 01:54:26 Machine dbus-daemon[22501]: [session uid=1000 pid=22501] Activating service name='org.gnome.ChromeGnomeShell' requested by ':1.103' (uid=1000 pid=27386 comm="/usr/bin/python3 /usr/bin/chrome-gnome-shell chrom" label="unconfined")
Aug 18 01:54:27 Machine dbus-daemon[22501]: [session uid=1000 pid=22501] Successfully activated service 'org.gnome.ChromeGnomeShell'
Aug 18 01:54:27 Machine org.gnome.Shell.desktop[27375]: current session already has an ibus-daemon.
Aug 18 01:54:27 Machine dbus-daemon[1477]: [system] Activating via systemd: service name='org.freedesktop.GeoClue2' unit='geoclue.service' requested by ':1.1472' (uid=1000 pid=27375 comm="/usr/bin/gnome-shell " label="unconfined")
Aug 18 01:54:27 Machine systemd[1]: Starting Location Lookup Service...
Aug 18 01:54:27 Machine dbus-daemon[1477]: [system] Successfully activated service 'org.freedesktop.GeoClue2'
Aug 18 01:54:27 Machine systemd[1]: Started Location Lookup Service.
Aug 18 01:54:27 Machine wpa_supplicant[1502]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface dbus_property=Stations getter failed
Aug 18 01:54:27 Machine gnome-shell[27375]: Telepathy is not available, chat integration will be disabled.
Aug 18 01:54:27 Machine gnome-shell[27375]: loading user theme: /usr/share//themes/Sierra-light/gnome-shell/gnome-shell.css
Aug 18 01:54:27 Machine gnome-shell[27375]: Some code accessed the property 'NetSpeed' on the module 'net_speed'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Aug 18 01:54:27 Machine gnome-shell[27375]: Some code accessed the property 'NetSpeedStatusIcon' on the module 'net_speed_status_icon'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Aug 18 01:54:27 Machine gnome-shell[27375]: Some code accessed the property 'LayoutMenuItem' on the module 'layout_menu_item'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Aug 18 01:54:27 Machine gnome-shell[27375]: JS WARNING: [/home/master/.local/share/gnome-shell/extensions/netspeed@hedayaty.gmail.com/net_speed_status_icon.js 157]: assignment to undeclared variable device
Aug 18 01:54:27 Machine gnome-shell[27375]: Device -> 
Aug 18 01:54:27 Machine gnome-shell[27375]: JS ERROR: Could not load extension ubuntu-dock@ubuntu.com.bak: Error: uuid "ubuntu-dock@ubuntu.com" from metadata.json does not match directory name "ubuntu-dock@ubuntu.com.bak"#012createExtensionObject@resource:///org/gnome/shell/misc/extensionUtils.js:135:15#012_loadExtension@resource:///org/gnome/shell/misc/extensionUtils.js:186:25#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012scanExtensions/<@resource:///org/gnome/shell/misc/extensionUtils.js:197:13#012collectFromDatadirs@resource:///org/gnome/shell/misc/fileUtils.js:27:17#012scanExtensions@resource:///org/gnome/shell/misc/extensionUtils.js:196:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_loadExtensions@resource:///org/gnome/shell/ui/extensionSystem.js:330:5#012enableAllExtensions@resource:///org/gnome/shell/ui/extensionSystem.js:338:9#012_sessionUpdated@resource:///org/gnome/shell/ui/extensionSystem.js:369:9#012init@resource:///org/gnome/shell/ui/extensionSystem.js:377:5#012_initializeUI@resource:///org/gnome/shell/ui/main.js:229:5#012start@resource:///org/gnome/shell/ui/main.js:133:5#012@<main>:1:31
Aug 18 01:54:27 Machine gnome-shell[27375]: Extension dash-to-dock@micxgx.gmail.com already installed in /home/master/.local/share/gnome-shell/extensions/dash-to-dock@micxgx.gmail.com. /usr/share/gnome-shell/extensions/dash-to-dock@micxgx.gmail.com will not be loaded
Aug 18 01:54:27 Machine gnome-shell[27375]: Extension drive-menu@gnome-shell-extensions.gcampax.github.com already installed in /home/master/.local/share/gnome-shell/extensions/drive-menu@gnome-shell-extensions.gcampax.github.com. /usr/share/gnome-shell/extensions/drive-menu@gnome-shell-extensions.gcampax.github.com will not be loaded
Aug 18 01:54:27 Machine gnome-shell[27375]: Extension user-theme@gnome-shell-extensions.gcampax.github.com already installed in /home/master/.local/share/gnome-shell/extensions/user-theme@gnome-shell-extensions.gcampax.github.com. /usr/share/gnome-shell/extensions/user-theme@gnome-shell-extensions.gcampax.github.com will not be loaded
Aug 18 01:54:27 Machine gnome-shell[27375]: Extension workspace-indicator@gnome-shell-extensions.gcampax.github.com already installed in /home/master/.local/share/gnome-shell/extensions/workspace-indicator@gnome-shell-extensions.gcampax.github.com. /usr/share/gnome-shell/extensions/workspace-indicator@gnome-shell-extensions.gcampax.github.com will not be loaded
Aug 18 01:54:27 Machine gnome-shell[27375]: gdk_cairo_surface_create_from_pixbuf: assertion 'GDK_IS_PIXBUF (pixbuf)' failed
Aug 18 01:54:27 Machine org.gnome.Shell.desktop[27375]: **
Aug 18 01:54:27 Machine org.gnome.Shell.desktop[27375]: mutter:ERROR:core/window.c:5332:get_default_window_icon: assertion failed: (default_icon)
Aug 18 01:54:27 Machine org.gnome.Shell.desktop[27375]: == Stack trace for context 0x5570e97814b0 ==
Aug 18 01:54:27 Machine systemd[1]: Starting Process error reports when automatic reporting is enabled...
Aug 18 01:54:39 Machine whoopsie-upload-all[27430]: ERROR: processing /var/crash/_usr_bin_gnome-shell.1000.crash: Compressed file ended before the end-of-stream marker was reached
Aug 18 01:54:39 Machine whoopsie-upload-all[27430]: /var/crash/_usr_lib_chromium-browser_chromium-browser.1000.crash already marked for upload, skipping
Aug 18 01:54:39 Machine whoopsie-upload-all[27430]: Collecting info for /var/crash/_usr_bin_gnome-shell.1000.crash...
Aug 18 01:54:39 Machine whoopsie-upload-all[27430]: All reports processed
Aug 18 01:54:39 Machine systemd[1]: Started Process error reports when automatic reporting is enabled.
Aug 18 01:54:45 Machine gnome-session[22507]: gnome-session-binary[22507]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 6
Aug 18 01:54:45 Machine gnome-session-binary[22507]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 6
Aug 18 01:54:45 Machine gnome-session-binary[22507]: Unrecoverable failure in required component org.gnome.Shell.desktop
Aug 18 01:54:45 Machine gnome-session[22507]: gnome-session-binary[22507]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
Aug 18 01:54:45 Machine gnome-session[22507]: gnome-session-binary[22507]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Aug 18 01:54:45 Machine gnome-session-binary[22507]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
Aug 18 01:54:45 Machine kernel: [ 4856.111324] rfkill: input handler enabled
Aug 18 01:54:45 Machine update-notifier[23888]: Unable to connect to the Notification Watcher: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Aug 18 01:54:45 Machine gnome-session-binary[22507]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Aug 18 01:54:45 Machine update-notifier[23888]: Unable to connect to the Notification Watcher: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Aug 18 01:54:45 Machine bluetoothd[1460]: Endpoint unregistered: sender=:1.1339 path=/MediaEndpoint/A2DPSource
Aug 18 01:54:45 Machine gsd-media-keys[22797]: g_variant_get_va: assertion 'value != NULL' failed
Aug 18 01:54:45 Machine bluetoothd[1460]: Endpoint unregistered: sender=:1.1339 path=/MediaEndpoint/A2DPSink
Aug 18 01:54:45 Machine gsd-media-keys[22797]: g_variant_unref: assertion 'value != NULL' failed
Aug 18 01:54:45 Machine gsd-media-keys[22797]: Failed to grab accelerators: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying (4)
Aug 18 01:54:45 Machine at-spi-bus-launcher[22604]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"
Aug 18 01:54:45 Machine at-spi-bus-launcher[22604]:       after 4859 requests (4859 known processed) with 0 events remaining.
Aug 18 01:54:45 Machine gsd-power[22746]: gsd-power: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 01:54:45 Machine gsd-xsettings[22759]: gsd-xsettings: Fatal IO error 104 (Connection reset by peer) on X server :1.
Aug 18 01:54:45 Machine gsd-wacom[22763]: gsd-wacom: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 01:54:45 Machine gsd-clipboard[22789]: gsd-clipboard: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 01:54:45 Machine gsd-keyboard[22804]: gsd-keyboard: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 01:54:45 Machine update-notifier[23888]: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 01:54:45 Machine nautilus-deskto[22846]: nautilus-desktop: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 01:54:45 Machine gsd-color[22785]: gsd-color: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 01:54:45 Machine gnome-system-mo[25159]: gnome-system-monitor: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 01:54:45 Machine chromium-browser.desktop[23165]: [23165:23165:0818/015445.779523:ERROR:chrome_browser_main_extra_parts_x11.cc(63)] X IO error received (X server probably went away)
Aug 18 01:54:45 Machine chromium-browser.desktop[23165]: [23197:23197:0818/015445.779697:ERROR:x11_util.cc(112)] X IO error received (X server probably went away)
Aug 18 01:54:45 Machine gsd-media-keys[22797]: gsd-media-keys: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 01:54:45 Machine gnome-terminal-[24476]: gnome-terminal-server: Fatal IO error 104 (Connection reset by peer) on X server :1.
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (**) Option "fd" "44"
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) event2  - Power Button: device removed
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (**) Option "fd" "47"
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) event3  - Video Bus: device removed
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (**) Option "fd" "48"
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) event1  - Power Button: device removed
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (**) Option "fd" "49"
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) event0  - Sleep Button: device removed
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (**) Option "fd" "50"
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) event5  - Genius Optical Mouse: device removed
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (**) Option "fd" "51"
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) event4  - CHICONY HP Basic USB Keyboard: device removed
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (**) Option "fd" "52"
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) event6  - Eee PC WMI hotkeys: device removed
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) UnloadModule: "libinput"
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) systemd-logind: releasing fd for 13:70
Aug 18 01:54:45 Machine systemd[22477]: gnome-terminal-server.service: Main process exited, code=exited, status=1/FAILURE
Aug 18 01:54:45 Machine systemd[22477]: gnome-terminal-server.service: Failed with result 'exit-code'.
Aug 18 01:54:45 Machine gsd-color[2101]: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/xrandr_Acer_Technologies_Acer_G277HL_T0YSG0024210_master_1000
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) UnloadModule: "libinput"
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) systemd-logind: releasing fd for 13:68
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) UnloadModule: "libinput"
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) systemd-logind: releasing fd for 13:69
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) UnloadModule: "libinput"
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) systemd-logind: releasing fd for 13:64
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) UnloadModule: "libinput"
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) systemd-logind: releasing fd for 13:65
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) UnloadModule: "libinput"
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) systemd-logind: releasing fd for 13:67
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) UnloadModule: "libinput"
Aug 18 01:54:45 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) systemd-logind: releasing fd for 13:66
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) NVIDIA(GPU-0): Deleting GPU-0
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[22495]: (II) Server terminated successfully (0). Closing log file.
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1942] error requesting auth for org.freedesktop.NetworkManager.enable-disable-network: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1945] error requesting auth for org.freedesktop.NetworkManager.sleep-wake: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1947] error requesting auth for org.freedesktop.NetworkManager.enable-disable-wifi: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1948] error requesting auth for org.freedesktop.NetworkManager.enable-disable-wwan: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1950] error requesting auth for org.freedesktop.NetworkManager.enable-disable-wimax: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1952] error requesting auth for org.freedesktop.NetworkManager.network-control: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1954] error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1956] error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1958] error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1960] error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1962] error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1964] error requesting auth for org.freedesktop.NetworkManager.settings.modify.global-dns: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1966] error requesting auth for org.freedesktop.NetworkManager.reload: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1968] error requesting auth for org.freedesktop.NetworkManager.checkpoint-rollback: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1971] error requesting auth for org.freedesktop.NetworkManager.enable-disable-statistics: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine NetworkManager[1501]: <warn>  [1597686886.1973] error requesting auth for org.freedesktop.NetworkManager.enable-disable-connectivity-check: Authorization check failed: Failed to open file &#8220;/proc/22751/status&#8221;: No such file or directory
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 13:68
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 13:64
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 13:69
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 13:65
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 13:70
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 13:66
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 226:0
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): CRT-0: disconnected
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0):
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-0: disconnected
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0):
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): connected
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): Internal TMDS
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): 340.0 MHz maximum pixel clock
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0):
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-2: disconnected
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0):
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-3: disconnected
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0):
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-4: disconnected
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0):
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) NVIDIA(0): Setting mode "DFP-1:nvidia-auto-select"
Aug 18 01:54:46 Machine acpid: client 22497[0:0] has disconnected
Aug 18 01:54:46 Machine acpid: client connected from 1824[0:0]
Aug 18 01:54:46 Machine acpid: 1 client rule loaded
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event2  - Power Button: is tagged by udev as: Keyboard
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event2  - Power Button: device is a keyboard
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event1  - Power Button: is tagged by udev as: Keyboard
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event1  - Power Button: device is a keyboard
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event0  - Sleep Button: is tagged by udev as: Keyboard
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event0  - Sleep Button: device is a keyboard
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event5  - Genius Optical Mouse: is tagged by udev as: Mouse
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event5  - Genius Optical Mouse: device is a pointer
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event4  - CHICONY HP Basic USB Keyboard: is tagged by udev as: Keyboard
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event4  - CHICONY HP Basic USB Keyboard: device is a keyboard
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event6  - Eee PC WMI hotkeys: is tagged by udev as: Keyboard
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event6  - Eee PC WMI hotkeys: device is a keyboard
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 13:67
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event3  - Video Bus: is tagged by udev as: Keyboard
Aug 18 01:54:46 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event3  - Video Bus: device is a keyboard
Aug 18 01:54:46 Machine systemd[1]: Stopping User Manager for UID 1000...
Aug 18 01:54:46 Machine systemd[22477]: Stopping flatpak document portal service...
Aug 18 01:54:46 Machine systemd[22477]: Stopped target Default.
Aug 18 01:54:46 Machine systemd[22477]: Stopping Virtual filesystem service - disk device monitor...
Aug 18 01:54:46 Machine systemd[22477]: Stopping sandboxed app permission store...
Aug 18 01:54:46 Machine systemd[22477]: Stopping Evolution address book service...
Aug 18 01:54:46 Machine systemd[22477]: Stopping Accessibility services bus...
Aug 18 01:54:46 Machine systemd[22477]: Stopping Evolution source registry...
Aug 18 01:54:46 Machine systemd[22477]: Stopping Virtual filesystem service - Media Transfer Protocol monitor...
Aug 18 01:54:46 Machine systemd[22477]: Stopping Virtual filesystem service - GNOME Online Accounts monitor...
Aug 18 01:54:46 Machine systemd[22477]: Stopping Evolution calendar service...
Aug 18 01:54:46 Machine systemd[22477]: Stopping Virtual filesystem service...
Aug 18 01:54:46 Machine systemd[22477]: Stopping Virtual filesystem metadata service...
Aug 18 01:54:46 Machine systemd[22477]: Stopping D-Bus User Message Bus...
Aug 18 01:54:46 Machine systemd[22477]: Stopping Virtual filesystem service - digital camera monitor...
Aug 18 01:54:46 Machine systemd[22477]: Stopping Virtual filesystem service - Apple File Conduit monitor...
Aug 18 01:54:46 Machine systemd[22477]: Stopped sandboxed app permission store.
Aug 18 01:54:46 Machine systemd[22477]: Stopped Virtual filesystem service - digital camera monitor.
Aug 18 01:54:46 Machine systemd[22477]: Stopped Virtual filesystem service - GNOME Online Accounts monitor.
Aug 18 01:54:46 Machine systemd[22477]: Stopped Virtual filesystem service - Media Transfer Protocol monitor.
Aug 18 01:54:46 Machine systemd[22477]: Stopped Virtual filesystem service.
Aug 18 01:54:46 Machine systemd[22477]: Stopped Virtual filesystem service - disk device monitor.
Aug 18 01:54:46 Machine systemd[22477]: Stopped Virtual filesystem metadata service.
Aug 18 01:54:46 Machine systemd[22477]: Stopped flatpak document portal service.
Aug 18 01:54:46 Machine systemd[22477]: Stopped Virtual filesystem service - Apple File Conduit monitor.
Aug 18 01:54:46 Machine systemd[22477]: Stopped Evolution address book service.
Aug 18 01:54:46 Machine systemd[22477]: Stopped Accessibility services bus.
Aug 18 01:54:46 Machine systemd[22477]: Stopped D-Bus User Message Bus.
Aug 18 01:54:46 Machine systemd[22477]: Stopped Evolution source registry.
Aug 18 01:54:46 Machine systemd[22477]: Stopped Evolution calendar service.
Aug 18 01:54:46 Machine systemd[22477]: Stopped target Basic System.
Aug 18 01:54:46 Machine systemd[22477]: Stopped target Paths.
Aug 18 01:54:46 Machine systemd[22477]: Stopped Pending report trigger for Ubuntu Report.
Aug 18 01:54:46 Machine systemd[22477]: Stopped target Sockets.
Aug 18 01:54:46 Machine systemd[22477]: Closed GnuPG cryptographic agent and passphrase cache.
Aug 18 01:54:46 Machine systemd[22477]: Closed GnuPG network certificate management daemon.
Aug 18 01:54:46 Machine systemd[22477]: Closed GnuPG cryptographic agent and passphrase cache (access for web browsers).
Aug 18 01:54:46 Machine systemd[22477]: Closed GnuPG cryptographic agent (ssh-agent emulation).
Aug 18 01:54:46 Machine systemd[22477]: Closed GnuPG cryptographic agent and passphrase cache (restricted).
Aug 18 01:54:46 Machine systemd[22477]: Closed REST API socket for snapd user session agent.
Aug 18 01:54:46 Machine systemd[22477]: Stopped target Timers.
Aug 18 01:54:46 Machine systemd[22477]: Closed D-Bus User Message Bus Socket.
Aug 18 01:54:46 Machine systemd[22477]: Reached target Shutdown.
Aug 18 01:54:46 Machine systemd[22477]: Starting Exit the Session...
Aug 18 01:54:46 Machine systemd[22477]: Received SIGRTMIN+24 from PID 29301 (kill).
Aug 18 01:54:46 Machine systemd[1]: Stopped User Manager for UID 1000.
Aug 18 01:54:46 Machine systemd[1]: Removed slice User Slice of master.
Aug 18 01:54:46 Machine gnome-shell[1926]: Ignoring length property that isn't a number at line 1950, col 24
Aug 18 01:54:46 Machine gnome-shell[1926]: Ignoring excess values in shadow definition
Aug 18 01:54:46 Machine gnome-shell[1926]: Ignoring excess values in shadow definition

```

---

### Post by sunbear-c22 on 2020-08-17
[U][B]syslog for the third occurrence.

[/B][/U]```

Aug 18 02:01:00 Machine gnome-shell[29461]: gdk_cairo_surface_create_from_pixbuf: assertion 'GDK_IS_PIXBUF (pixbuf)' failed
Aug 18 02:01:00 Machine org.gnome.Shell.desktop[29461]: **
Aug 18 02:01:00 Machine org.gnome.Shell.desktop[29461]: mutter:ERROR:core/window.c:5332:get_default_window_icon: assertion failed: (default_icon)
Aug 18 02:01:00 Machine org.gnome.Shell.desktop[29461]: == Stack trace for context 0x557b20bfb330 ==
Aug 18 02:01:00 Machine kernel: [ 5231.121421] kauditd_printk_skb: 6 callbacks suppressed
Aug 18 02:01:00 Machine kernel: [ 5231.121422] audit: type=1400 audit(1597687260.773:136): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/usr/share/nvidia/nvidia-application-profiles-435.21-rc" pid=30070 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Aug 18 02:01:00 Machine kernel: [ 5231.124018] audit: type=1400 audit(1597687260.777:137): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/proc/30070/comm" pid=30070 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Aug 18 02:01:00 Machine kernel: [ 5231.126516] audit: type=1400 audit(1597687260.777:138): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/usr/share/nvidia/nvidia-application-profiles-435.21-rc" pid=30070 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Aug 18 02:01:00 Machine kernel: [ 5231.128462] audit: type=1400 audit(1597687260.781:139): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/proc/30070/comm" pid=30070 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Aug 18 02:01:00 Machine systemd[1]: Starting Process error reports when automatic reporting is enabled...
Aug 18 02:01:00 Machine kernel: [ 5231.134346] audit: type=1400 audit(1597687260.785:140): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/proc/modules" pid=30070 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Aug 18 02:01:00 Machine kernel: [ 5231.134391] audit: type=1400 audit(1597687260.785:141): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/proc/driver/nvidia/params" pid=30070 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Aug 18 02:01:00 Machine kernel: [ 5231.134410] audit: type=1400 audit(1597687260.785:142): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/dev/nvidiactl" pid=30070 comm="soffice.bin" requested_mask="wr" denied_mask="wr" fsuid=1000 ouid=0
Aug 18 02:01:00 Machine kernel: [ 5231.134429] audit: type=1400 audit(1597687260.785:143): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/sys/devices/system/memory/block_size_bytes" pid=30070 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Aug 18 02:01:00 Machine kernel: [ 5231.134487] audit: type=1400 audit(1597687260.785:144): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/proc/modules" pid=30070 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Aug 18 02:01:00 Machine kernel: [ 5231.134516] audit: type=1400 audit(1597687260.785:145): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/proc/driver/nvidia/params" pid=30070 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Aug 18 02:01:00 Machine soffice.bin[30068]: Could not load a pixbuf from icon theme.#012This may indicate that pixbuf loaders or the mime database could not be found.
Aug 18 02:01:12 Machine whoopsie-upload-all[30076]: ERROR: processing /var/crash/_usr_bin_gnome-shell.1000.crash: Compressed file ended before the end-of-stream marker was reached
Aug 18 02:01:12 Machine whoopsie-upload-all[30076]: /var/crash/_usr_lib_chromium-browser_chromium-browser.1000.crash already marked for upload, skipping
Aug 18 02:01:12 Machine whoopsie-upload-all[30076]: Collecting info for /var/crash/_usr_bin_gnome-shell.1000.crash...
Aug 18 02:01:12 Machine whoopsie-upload-all[30076]: All reports processed
Aug 18 02:01:12 Machine systemd[1]: Started Process error reports when automatic reporting is enabled.
Aug 18 02:01:28 Machine gnome-session[29340]: gnome-session-binary[29340]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 6
Aug 18 02:01:28 Machine gnome-session-binary[29340]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 6
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): CRT-0: disconnected
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-0: disconnected
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): connected
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): Internal TMDS
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): 340.0 MHz maximum pixel clock
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-2: disconnected
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-3: disconnected
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-4: disconnected
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): CRT-0: disconnected
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-0: disconnected
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): connected
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): Internal TMDS
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): 340.0 MHz maximum pixel clock
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-2: disconnected
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-3: disconnected
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-4: disconnected
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
Aug 18 02:01:28 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:01:28 Machine gsd-media-keys[29638]: g_variant_get_va: assertion 'value != NULL' failed
Aug 18 02:01:28 Machine gsd-media-keys[29638]: g_variant_unref: assertion 'value != NULL' failed
Aug 18 02:01:29 Machine org.gnome.Shell.desktop[31886]: current session already has an ibus-daemon.
Aug 18 02:01:29 Machine dbus-daemon[1477]: [system] Activating via systemd: service name='org.freedesktop.GeoClue2' unit='geoclue.service' requested by ':1.1518' (uid=1000 pid=31886 comm="/usr/bin/gnome-shell " label="unconfined")
Aug 18 02:01:29 Machine systemd[1]: Starting Location Lookup Service...
Aug 18 02:01:29 Machine dbus-daemon[1477]: [system] Successfully activated service 'org.freedesktop.GeoClue2'
Aug 18 02:01:29 Machine systemd[1]: Started Location Lookup Service.
Aug 18 02:01:29 Machine wpa_supplicant[1502]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface dbus_property=Stations getter failed
Aug 18 02:01:29 Machine gnome-shell[31886]: Telepathy is not available, chat integration will be disabled.
Aug 18 02:01:29 Machine gnome-shell[31886]: loading user theme: /usr/share//themes/Sierra-light/gnome-shell/gnome-shell.css
Aug 18 02:01:29 Machine gnome-shell[31886]: Some code accessed the property 'NetSpeed' on the module 'net_speed'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Aug 18 02:01:29 Machine gnome-shell[31886]: Some code accessed the property 'NetSpeedStatusIcon' on the module 'net_speed_status_icon'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Aug 18 02:01:29 Machine gnome-shell[31886]: Some code accessed the property 'LayoutMenuItem' on the module 'layout_menu_item'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Aug 18 02:01:29 Machine gnome-shell[31886]: JS WARNING: [/home/master/.local/share/gnome-shell/extensions/netspeed@hedayaty.gmail.com/net_speed_status_icon.js 157]: assignment to undeclared variable device
Aug 18 02:01:29 Machine gnome-shell[31886]: Device -> 
Aug 18 02:01:29 Machine gnome-shell[31886]: JS ERROR: Could not load extension ubuntu-dock@ubuntu.com.bak: Error: uuid "ubuntu-dock@ubuntu.com" from metadata.json does not match directory name "ubuntu-dock@ubuntu.com.bak"#012createExtensionObject@resource:///org/gnome/shell/misc/extensionUtils.js:135:15#012_loadExtension@resource:///org/gnome/shell/misc/extensionUtils.js:186:25#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012scanExtensions/<@resource:///org/gnome/shell/misc/extensionUtils.js:197:13#012collectFromDatadirs@resource:///org/gnome/shell/misc/fileUtils.js:27:17#012scanExtensions@resource:///org/gnome/shell/misc/extensionUtils.js:196:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_loadExtensions@resource:///org/gnome/shell/ui/extensionSystem.js:330:5#012enableAllExtensions@resource:///org/gnome/shell/ui/extensionSystem.js:338:9#012_sessionUpdated@resource:///org/gnome/shell/ui/extensionSystem.js:369:9#012init@resource:///org/gnome/shell/ui/extensionSystem.js:377:5#012_initializeUI@resource:///org/gnome/shell/ui/main.js:229:5#012start@resource:///org/gnome/shell/ui/main.js:133:5#012@<main>:1:31
Aug 18 02:01:29 Machine gnome-shell[31886]: Extension dash-to-dock@micxgx.gmail.com already installed in /home/master/.local/share/gnome-shell/extensions/dash-to-dock@micxgx.gmail.com. /usr/share/gnome-shell/extensions/dash-to-dock@micxgx.gmail.com will not be loaded
Aug 18 02:01:29 Machine gnome-shell[31886]: Extension drive-menu@gnome-shell-extensions.gcampax.github.com already installed in /home/master/.local/share/gnome-shell/extensions/drive-menu@gnome-shell-extensions.gcampax.github.com. /usr/share/gnome-shell/extensions/drive-menu@gnome-shell-extensions.gcampax.github.com will not be loaded
Aug 18 02:01:29 Machine gnome-shell[31886]: Extension user-theme@gnome-shell-extensions.gcampax.github.com already installed in /home/master/.local/share/gnome-shell/extensions/user-theme@gnome-shell-extensions.gcampax.github.com. /usr/share/gnome-shell/extensions/user-theme@gnome-shell-extensions.gcampax.github.com will not be loaded
Aug 18 02:01:29 Machine gnome-shell[31886]: Extension workspace-indicator@gnome-shell-extensions.gcampax.github.com already installed in /home/master/.local/share/gnome-shell/extensions/workspace-indicator@gnome-shell-extensions.gcampax.github.com. /usr/share/gnome-shell/extensions/workspace-indicator@gnome-shell-extensions.gcampax.github.com will not be loaded
Aug 18 02:01:29 Machine bluetoothd[1460]: Failed to set mode: Blocked through rfkill (0x12)
Aug 18 02:01:29 Machine gnome-shell[31886]: Ignoring excess values in shadow definition
Aug 18 02:01:29 Machine gnome-shell[31886]: message repeated 7 times: [ Ignoring excess values in shadow definition]
Aug 18 02:01:30 Machine gnome-shell[31886]: Some code accessed the property 'getUniqueBusNameSync' on the module 'util'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Aug 18 02:01:30 Machine gnome-shell[31886]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.79/StatusNotifierItem
Aug 18 02:01:30 Machine gnome-shell[31886]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.75/org/ayatana/NotificationItem/software_update_available
Aug 18 02:01:30 Machine gnome-shell[31886]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.75/org/ayatana/NotificationItem/livepatch
Aug 18 02:01:30 Machine gnome-shell[31886]: Error setting property 'Powered' on interface org.bluez.Adapter1: GDBus.Error:org.bluez.Error.Blocked: Blocked through rfkill (g-io-error-quark, 36)
Aug 18 02:01:30 Machine gnome-shell[31886]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
Aug 18 02:01:30 Machine gnome-shell[31886]: Ignoring excess values in shadow definition
Aug 18 02:01:30 Machine gnome-shell[31886]: message repeated 7 times: [ Ignoring excess values in shadow definition]
Aug 18 02:01:31 Machine gnome-shell[31886]: GNOME Shell started at Tue Aug 18 2020 02:01:29 GMT+0800
Aug 18 02:01:37 Machine gnome-shell[31886]: Some code accessed the property 'refreshPropertyOnProxy' on the module 'util'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Aug 18 02:01:42 Machine gnome-shell[31886]: Ignoring excess values in shadow definition
Aug 18 02:01:43 Machine gnome-shell[31886]: message repeated 3 times: [ Ignoring excess values in shadow definition]

```

---

### Post by sunbear-c22 on 2020-08-17
[U][B]syslog for the forth occurrence.
[/B][/U]
```

Aug 18 02:02:15 Machine gnome-shell[31886]: gdk_cairo_surface_create_from_pixbuf: assertion 'GDK_IS_PIXBUF (pixbuf)' failed
Aug 18 02:02:15 Machine org.gnome.Shell.desktop[31886]: **
Aug 18 02:02:15 Machine org.gnome.Shell.desktop[31886]: mutter:ERROR:core/window.c:5332:get_default_window_icon: assertion failed: (default_icon)
Aug 18 02:02:15 Machine org.gnome.Shell.desktop[31886]: == Stack trace for context 0x5634093db4b0 ==
Aug 18 02:02:15 Machine systemd[1]: Starting Process error reports when automatic reporting is enabled...
Aug 18 02:02:27 Machine whoopsie-upload-all[31938]: ERROR: processing /var/crash/_usr_bin_gnome-shell.1000.crash: Compressed file ended before the end-of-stream marker was reached
Aug 18 02:02:27 Machine whoopsie-upload-all[31938]: /var/crash/_usr_lib_chromium-browser_chromium-browser.1000.crash already marked for upload, skipping
Aug 18 02:02:27 Machine whoopsie-upload-all[31938]: Collecting info for /var/crash/_usr_bin_gnome-shell.1000.crash...
Aug 18 02:02:27 Machine whoopsie-upload-all[31938]: All reports processed
Aug 18 02:02:27 Machine systemd[1]: Started Process error reports when automatic reporting is enabled.
Aug 18 02:02:43 Machine systemd[1]: Started Run anacron jobs.
Aug 18 02:02:43 Machine anacron[1371]: Anacron 2.3 started on 2020-08-18
Aug 18 02:02:43 Machine anacron[1371]: Normal exit (0 jobs run)
Aug 18 02:02:44 Machine gnome-session[29340]: gnome-session-binary[29340]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 6
Aug 18 02:02:44 Machine gnome-session-binary[29340]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 6
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): CRT-0: disconnected
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-0: disconnected
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): connected
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): Internal TMDS
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): 340.0 MHz maximum pixel clock
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-2: disconnected
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-3: disconnected
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-4: disconnected
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): CRT-0: disconnected
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-0: disconnected
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): connected
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): Internal TMDS
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): 340.0 MHz maximum pixel clock
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-2: disconnected
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-3: disconnected
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-4: disconnected
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
Aug 18 02:02:44 Machine /usr/lib/gdm3/gdm-x-session[29328]: (--) NVIDIA(GPU-0):
Aug 18 02:02:44 Machine gsd-media-keys[29638]: g_variant_get_va: assertion 'value != NULL' failed
Aug 18 02:02:44 Machine gsd-media-keys[29638]: g_variant_unref: assertion 'value != NULL' failed
Aug 18 02:02:45 Machine org.gnome.Shell.desktop[1373]: current session already has an ibus-daemon.
Aug 18 02:02:45 Machine dbus-daemon[1477]: [system] Activating via systemd: service name='org.freedesktop.GeoClue2' unit='geoclue.service' requested by ':1.1521' (uid=1000 pid=1373 comm="/usr/bin/gnome-shell " label="unconfined")
Aug 18 02:02:45 Machine systemd[1]: Starting Location Lookup Service...
Aug 18 02:02:45 Machine dbus-daemon[1477]: [system] Successfully activated service 'org.freedesktop.GeoClue2'
Aug 18 02:02:45 Machine systemd[1]: Started Location Lookup Service.
Aug 18 02:02:45 Machine wpa_supplicant[1502]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface dbus_property=Stations getter failed
Aug 18 02:02:45 Machine gnome-shell[1373]: Telepathy is not available, chat integration will be disabled.
Aug 18 02:02:45 Machine gnome-shell[1373]: loading user theme: /usr/share//themes/Sierra-light/gnome-shell/gnome-shell.css
Aug 18 02:02:45 Machine gnome-shell[1373]: Some code accessed the property 'NetSpeed' on the module 'net_speed'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Aug 18 02:02:45 Machine gnome-shell[1373]: Some code accessed the property 'NetSpeedStatusIcon' on the module 'net_speed_status_icon'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Aug 18 02:02:45 Machine gnome-shell[1373]: Some code accessed the property 'LayoutMenuItem' on the module 'layout_menu_item'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Aug 18 02:02:45 Machine gnome-shell[1373]: JS WARNING: [/home/master/.local/share/gnome-shell/extensions/netspeed@hedayaty.gmail.com/net_speed_status_icon.js 157]: assignment to undeclared variable device
Aug 18 02:02:45 Machine gnome-shell[1373]: Device -> 
Aug 18 02:02:45 Machine gnome-shell[1373]: JS ERROR: Could not load extension ubuntu-dock@ubuntu.com.bak: Error: uuid "ubuntu-dock@ubuntu.com" from metadata.json does not match directory name "ubuntu-dock@ubuntu.com.bak"#012createExtensionObject@resource:///org/gnome/shell/misc/extensionUtils.js:135:15#012_loadExtension@resource:///org/gnome/shell/misc/extensionUtils.js:186:25#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012scanExtensions/<@resource:///org/gnome/shell/misc/extensionUtils.js:197:13#012collectFromDatadirs@resource:///org/gnome/shell/misc/fileUtils.js:27:17#012scanExtensions@resource:///org/gnome/shell/misc/extensionUtils.js:196:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_loadExtensions@resource:///org/gnome/shell/ui/extensionSystem.js:330:5#012enableAllExtensions@resource:///org/gnome/shell/ui/extensionSystem.js:338:9#012_sessionUpdated@resource:///org/gnome/shell/ui/extensionSystem.js:369:9#012init@resource:///org/gnome/shell/ui/extensionSystem.js:377:5#012_initializeUI@resource:///org/gnome/shell/ui/main.js:229:5#012start@resource:///org/gnome/shell/ui/main.js:133:5#012@<main>:1:31
Aug 18 02:02:45 Machine gnome-shell[1373]: Extension dash-to-dock@micxgx.gmail.com already installed in /home/master/.local/share/gnome-shell/extensions/dash-to-dock@micxgx.gmail.com. /usr/share/gnome-shell/extensions/dash-to-dock@micxgx.gmail.com will not be loaded
Aug 18 02:02:45 Machine gnome-shell[1373]: Extension drive-menu@gnome-shell-extensions.gcampax.github.com already installed in /home/master/.local/share/gnome-shell/extensions/drive-menu@gnome-shell-extensions.gcampax.github.com. /usr/share/gnome-shell/extensions/drive-menu@gnome-shell-extensions.gcampax.github.com will not be loaded
Aug 18 02:02:45 Machine gnome-shell[1373]: Extension user-theme@gnome-shell-extensions.gcampax.github.com already installed in /home/master/.local/share/gnome-shell/extensions/user-theme@gnome-shell-extensions.gcampax.github.com. /usr/share/gnome-shell/extensions/user-theme@gnome-shell-extensions.gcampax.github.com will not be loaded
Aug 18 02:02:45 Machine gnome-shell[1373]: Extension workspace-indicator@gnome-shell-extensions.gcampax.github.com already installed in /home/master/.local/share/gnome-shell/extensions/workspace-indicator@gnome-shell-extensions.gcampax.github.com. /usr/share/gnome-shell/extensions/workspace-indicator@gnome-shell-extensions.gcampax.github.com will not be loaded
Aug 18 02:02:45 Machine gnome-shell[1373]: gdk_cairo_surface_create_from_pixbuf: assertion 'GDK_IS_PIXBUF (pixbuf)' failed
Aug 18 02:02:45 Machine org.gnome.Shell.desktop[1373]: **
Aug 18 02:02:45 Machine org.gnome.Shell.desktop[1373]: mutter:ERROR:core/window.c:5332:get_default_window_icon: assertion failed: (default_icon)
Aug 18 02:02:45 Machine org.gnome.Shell.desktop[1373]: == Stack trace for context 0x55d7677994b0 ==
Aug 18 02:02:45 Machine systemd[1]: Starting Process error reports when automatic reporting is enabled...
Aug 18 02:02:57 Machine whoopsie-upload-all[1413]: ERROR: processing /var/crash/_usr_bin_gnome-shell.1000.crash: Compressed file ended before the end-of-stream marker was reached
Aug 18 02:02:57 Machine whoopsie-upload-all[1413]: /var/crash/_usr_lib_chromium-browser_chromium-browser.1000.crash already marked for upload, skipping
Aug 18 02:02:57 Machine whoopsie-upload-all[1413]: Collecting info for /var/crash/_usr_bin_gnome-shell.1000.crash...
Aug 18 02:02:57 Machine whoopsie-upload-all[1413]: All reports processed
Aug 18 02:02:57 Machine systemd[1]: Started Process error reports when automatic reporting is enabled.
Aug 18 02:03:03 Machine gnome-session[29340]: gnome-session-binary[29340]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 6
Aug 18 02:03:03 Machine gnome-session[29340]: gnome-session-binary[29340]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
Aug 18 02:03:03 Machine gnome-session[29340]: gnome-session-binary[29340]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Aug 18 02:03:03 Machine gnome-session-binary[29340]: Unrecoverable failure in required component org.gnome.Shell.desktop
Aug 18 02:03:03 Machine gnome-session-binary[29340]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 6
Aug 18 02:03:03 Machine gnome-session-binary[29340]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
Aug 18 02:03:03 Machine gnome-session-binary[29340]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Aug 18 02:03:03 Machine update-notifier[29923]: Unable to connect to the Notification Watcher: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Aug 18 02:03:03 Machine update-notifier[29923]: Unable to connect to the Notification Watcher: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Aug 18 02:03:03 Machine gsd-media-keys[29638]: g_variant_get_va: assertion 'value != NULL' failed
Aug 18 02:03:03 Machine gsd-media-keys[29638]: g_variant_unref: assertion 'value != NULL' failed
Aug 18 02:03:03 Machine gsd-media-keys[29638]: Failed to grab accelerators: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying (4)
Aug 18 02:03:03 Machine kernel: [ 5354.214981] rfkill: input handler enabled
Aug 18 02:03:03 Machine bluetoothd[1460]: Endpoint unregistered: sender=:1.1489 path=/MediaEndpoint/A2DPSource
Aug 18 02:03:03 Machine bluetoothd[1460]: Endpoint unregistered: sender=:1.1489 path=/MediaEndpoint/A2DPSink
Aug 18 02:03:03 Machine at-spi-bus-launcher[29437]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"
Aug 18 02:03:03 Machine at-spi-bus-launcher[29437]:       after 2287 requests (2287 known processed) with 0 events remaining.
Aug 18 02:03:03 Machine gsd-power[29581]: gsd-power: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 02:03:03 Machine gsd-wacom[29604]: gsd-wacom: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 02:03:03 Machine gsd-clipboard[29617]: gsd-clipboard: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 02:03:03 Machine gsd-color[29625]: gsd-color: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 02:03:03 Machine gsd-keyboard[29627]: gsd-keyboard: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 02:03:03 Machine gsd-media-keys[29638]: gsd-media-keys: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 02:03:03 Machine nautilus-deskto[29677]: nautilus-desktop: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 02:03:03 Machine gnome-terminal-[29886]: gnome-terminal-server: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 02:03:03 Machine update-notifier[29923]: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 02:03:03 Machine gsd-xsettings[29595]: gsd-xsettings: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Aug 18 02:03:03 Machine libreoffice-writer.desktop[30049]: X IO Error
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (**) Option "fd" "44"
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) event2  - Power Button: device removed
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (**) Option "fd" "47"
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) event3  - Video Bus: device removed
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (**) Option "fd" "48"
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) event1  - Power Button: device removed
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (**) Option "fd" "49"
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) event0  - Sleep Button: device removed
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (**) Option "fd" "50"
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) event5  - Genius Optical Mouse: device removed
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (**) Option "fd" "51"
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) event4  - CHICONY HP Basic USB Keyboard: device removed
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (**) Option "fd" "52"
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) event6  - Eee PC WMI hotkeys: device removed
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) UnloadModule: "libinput"
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) systemd-logind: releasing fd for 13:70
Aug 18 02:03:03 Machine systemd[29310]: gnome-terminal-server.service: Main process exited, code=exited, status=1/FAILURE
Aug 18 02:03:03 Machine systemd[29310]: gnome-terminal-server.service: Failed with result 'exit-code'.
Aug 18 02:03:03 Machine gsd-color[2101]: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/xrandr_Acer_Technologies_Acer_G277HL_T0YSG0024210_master_1000
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) UnloadModule: "libinput"
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) systemd-logind: releasing fd for 13:68
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) UnloadModule: "libinput"
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) systemd-logind: releasing fd for 13:69
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) UnloadModule: "libinput"
Aug 18 02:03:03 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) systemd-logind: releasing fd for 13:64
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) UnloadModule: "libinput"
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) systemd-logind: releasing fd for 13:65
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) UnloadModule: "libinput"
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) systemd-logind: releasing fd for 13:67
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) UnloadModule: "libinput"
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) systemd-logind: releasing fd for 13:66
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) NVIDIA(GPU-0): Deleting GPU-0
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[29328]: (II) Server terminated successfully (0). Closing log file.
Aug 18 02:03:04 Machine NetworkManager[1501]: <warn>  [1597687384.2719] error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: Authorization check failed: Failed to open file &#8220;/proc/29586/status&#8221;: No such file or directory
Aug 18 02:03:04 Machine NetworkManager[1501]: <warn>  [1597687384.2721] error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: Authorization check failed: Failed to open file &#8220;/proc/29586/status&#8221;: No such file or directory
Aug 18 02:03:04 Machine NetworkManager[1501]: <warn>  [1597687384.2724] error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: Authorization check failed: Failed to open file &#8220;/proc/29586/status&#8221;: No such file or directory
Aug 18 02:03:04 Machine NetworkManager[1501]: <warn>  [1597687384.2727] error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: Authorization check failed: Failed to open file &#8220;/proc/29586/status&#8221;: No such file or directory
Aug 18 02:03:04 Machine NetworkManager[1501]: <warn>  [1597687384.2729] error requesting auth for org.freedesktop.NetworkManager.settings.modify.global-dns: Authorization check failed: Failed to open file &#8220;/proc/29586/status&#8221;: No such file or directory
Aug 18 02:03:04 Machine NetworkManager[1501]: <warn>  [1597687384.2731] error requesting auth for org.freedesktop.NetworkManager.reload: Authorization check failed: Failed to open file &#8220;/proc/29586/status&#8221;: No such file or directory
Aug 18 02:03:04 Machine NetworkManager[1501]: <warn>  [1597687384.2733] error requesting auth for org.freedesktop.NetworkManager.checkpoint-rollback: Authorization check failed: Failed to open file &#8220;/proc/29586/status&#8221;: No such file or directory
Aug 18 02:03:04 Machine NetworkManager[1501]: <warn>  [1597687384.2735] error requesting auth for org.freedesktop.NetworkManager.enable-disable-statistics: Authorization check failed: Failed to open file &#8220;/proc/29586/status&#8221;: No such file or directory
Aug 18 02:03:04 Machine NetworkManager[1501]: <warn>  [1597687384.2737] error requesting auth for org.freedesktop.NetworkManager.enable-disable-connectivity-check: Authorization check failed: Failed to open file &#8220;/proc/29586/status&#8221;: No such file or directory
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 13:68
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 13:64
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 13:69
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 13:65
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 13:70
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 13:66
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 226:0
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): CRT-0: disconnected
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0):
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-0: disconnected
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0):
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): connected
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): Internal TMDS
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): Acer G277HL (DFP-1): 340.0 MHz maximum pixel clock
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0):
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-2: disconnected
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0):
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-3: disconnected
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0):
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-4: disconnected
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (--) NVIDIA(GPU-0):
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) NVIDIA(0): Setting mode "DFP-1:nvidia-auto-select"
Aug 18 02:03:04 Machine acpid: client 29330[0:0] has disconnected
Aug 18 02:03:04 Machine acpid: client connected from 1824[0:0]
Aug 18 02:03:04 Machine acpid: 1 client rule loaded
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event2  - Power Button: is tagged by udev as: Keyboard
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event2  - Power Button: device is a keyboard
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event1  - Power Button: is tagged by udev as: Keyboard
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event1  - Power Button: device is a keyboard
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event0  - Sleep Button: is tagged by udev as: Keyboard
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event0  - Sleep Button: device is a keyboard
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event5  - Genius Optical Mouse: is tagged by udev as: Mouse
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event5  - Genius Optical Mouse: device is a pointer
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event4  - CHICONY HP Basic USB Keyboard: is tagged by udev as: Keyboard
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event4  - CHICONY HP Basic USB Keyboard: device is a keyboard
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event6  - Eee PC WMI hotkeys: is tagged by udev as: Keyboard
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event6  - Eee PC WMI hotkeys: device is a keyboard
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) systemd-logind: got resume for 13:67
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event3  - Video Bus: is tagged by udev as: Keyboard
Aug 18 02:03:04 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event3  - Video Bus: device is a keyboard
Aug 18 02:03:05 Machine gnome-shell[1926]: Ignoring length property that isn't a number at line 1950, col 24
Aug 18 02:03:05 Machine gnome-shell[1926]: Ignoring excess values in shadow definition
Aug 18 02:03:05 Machine gnome-shell[1926]: Ignoring excess values in shadow definition
Aug 18 02:03:10 Machine systemd[1]: Stopping User Manager for UID 1000...
Aug 18 02:03:10 Machine systemd[29310]: Stopping Virtual filesystem service - disk device monitor...
Aug 18 02:03:10 Machine systemd[29310]: Stopping Evolution address book service...
Aug 18 02:03:10 Machine systemd[29310]: Stopping Evolution calendar service...
Aug 18 02:03:10 Machine systemd[29310]: Stopping Virtual filesystem service - GNOME Online Accounts monitor...
Aug 18 02:03:10 Machine systemd[29310]: Stopping Virtual filesystem service - Apple File Conduit monitor...
Aug 18 02:03:10 Machine systemd[29310]: Stopping Virtual filesystem metadata service...
Aug 18 02:03:10 Machine systemd[29310]: Stopping Evolution source registry...
Aug 18 02:03:10 Machine systemd[29310]: Stopping Accessibility services bus...
Aug 18 02:03:10 Machine systemd[29310]: Stopping Virtual filesystem service...
Aug 18 02:03:10 Machine systemd[29310]: Stopped target Default.
Aug 18 02:03:10 Machine systemd[29310]: Stopping sandboxed app permission store...
Aug 18 02:03:10 Machine systemd[29310]: Stopping D-Bus User Message Bus...
Aug 18 02:03:10 Machine systemd[29310]: Stopping Virtual filesystem service - Media Transfer Protocol monitor...
Aug 18 02:03:10 Machine systemd[29310]: Stopping Virtual filesystem service - digital camera monitor...
Aug 18 02:03:10 Machine systemd[29310]: Stopped sandboxed app permission store.
Aug 18 02:03:10 Machine systemd[29310]: Stopped Evolution source registry.
Aug 18 02:03:10 Machine systemd[29310]: Stopped Virtual filesystem service - disk device monitor.
Aug 18 02:03:10 Machine systemd[29310]: Stopped Virtual filesystem service.
Aug 18 02:03:10 Machine systemd[29310]: Stopped Virtual filesystem service - digital camera monitor.
Aug 18 02:03:10 Machine systemd[29310]: Stopped Virtual filesystem service - GNOME Online Accounts monitor.
Aug 18 02:03:10 Machine systemd[29310]: Stopped Virtual filesystem service - Apple File Conduit monitor.
Aug 18 02:03:10 Machine systemd[29310]: Stopped Virtual filesystem service - Media Transfer Protocol monitor.
Aug 18 02:03:10 Machine systemd[29310]: Stopped Virtual filesystem metadata service.
Aug 18 02:03:10 Machine systemd[29310]: Stopped Evolution address book service.
Aug 18 02:03:10 Machine systemd[29310]: Stopped Evolution calendar service.
Aug 18 02:03:10 Machine systemd[29310]: Stopped D-Bus User Message Bus.
Aug 18 02:03:10 Machine systemd[29310]: Stopped Accessibility services bus.
Aug 18 02:03:10 Machine systemd[29310]: Stopped target Basic System.
Aug 18 02:03:10 Machine systemd[29310]: Stopped target Timers.
Aug 18 02:03:10 Machine systemd[29310]: Stopped target Paths.
Aug 18 02:03:10 Machine systemd[29310]: Stopped Pending report trigger for Ubuntu Report.
Aug 18 02:03:10 Machine systemd[29310]: Stopped target Sockets.
Aug 18 02:03:10 Machine systemd[29310]: Closed GnuPG network certificate management daemon.
Aug 18 02:03:10 Machine systemd[29310]: Closed REST API socket for snapd user session agent.
Aug 18 02:03:10 Machine systemd[29310]: Closed GnuPG cryptographic agent and passphrase cache (restricted).
Aug 18 02:03:10 Machine systemd[29310]: Closed GnuPG cryptographic agent and passphrase cache.
Aug 18 02:03:10 Machine systemd[29310]: Closed GnuPG cryptographic agent (ssh-agent emulation).
Aug 18 02:03:10 Machine systemd[29310]: Closed GnuPG cryptographic agent and passphrase cache (access for web browsers).
Aug 18 02:03:10 Machine systemd[29310]: Closed D-Bus User Message Bus Socket.
Aug 18 02:03:10 Machine systemd[29310]: Reached target Shutdown.
Aug 18 02:03:10 Machine systemd[29310]: Starting Exit the Session...
Aug 18 02:03:10 Machine systemd[29310]: Received SIGRTMIN+24 from PID 3492 (kill).
Aug 18 02:03:10 Machine systemd[1]: Stopped User Manager for UID 1000.
Aug 18 02:03:10 Machine systemd[1]: Removed slice User Slice of master.
Aug 18 02:03:13 Machine gnome-shell[1926]: Ignoring excess values in shadow definition
Aug 18 02:03:13 Machine gnome-shell[1926]: Ignoring excess values in shadow definition
Aug 18 02:03:16 Machine systemd[1784]: Stopping D-Bus User Message Bus...
Aug 18 02:03:16 Machine systemd[1784]: xdg-permission-store.service: Main process exited, code=exited, status=1/FAILURE
Aug 18 02:03:16 Machine systemd[1784]: xdg-permission-store.service: Failed with result 'exit-code'.
Aug 18 02:03:16 Machine gnome-session[1908]: gnome-session-binary[1908]: WARNING: Lost name on bus: org.gnome.SessionManager
Aug 18 02:03:16 Machine gnome-session[1908]: gnome-session-binary[1908]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Aug 18 02:03:16 Machine gnome-session-binary[1908]: WARNING: Lost name on bus: org.gnome.SessionManager
Aug 18 02:03:16 Machine gsd-power[2122]: Error releasing name org.gnome.SettingsDaemon.Power: The connection is closed
Aug 18 02:03:16 Machine gnome-session-binary[1908]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Aug 18 02:03:16 Machine gnome-shell[1926]: gnome-shell: Fatal IO error 0 (Success) on X server :0.
Aug 18 02:03:16 Machine systemd[1]: Stopping Save/Restore Sound Card State...
Aug 18 02:03:16 Machine systemd[1]: Stopping Thunderbolt system service...
Aug 18 02:03:16 Machine systemd[1]: Stopping Manage, Install and Generate Color Profiles...
Aug 18 02:03:16 Machine systemd[1]: Stopped target Printer.
Aug 18 02:03:16 Machine systemd[1]: Stopped target Timers.
Aug 18 02:03:16 Machine systemd[1]: Stopped Discard unused blocks once a week.
Aug 18 02:03:16 Machine systemd[1]: Stopping Session c2 of user gdm.
Aug 18 02:03:16 Machine systemd[1]: Stopped target Sound Card.
Aug 18 02:03:16 Machine bluetoothd[1460]: Terminating
Aug 18 02:03:16 Machine systemd[1]: Stopped Daily Cleanup of Temporary Directories.
Aug 18 02:03:16 Machine systemd[1]: Stopped target Bluetooth.
Aug 18 02:03:16 Machine systemd[1]: Stopping Bluetooth service...
Aug 18 02:03:16 Machine systemd[1]: Stopping ACPI event daemon...
Aug 18 02:03:16 Machine gdm3: Tried to look up non-existent conversation gdm-launch-environment
Aug 18 02:03:16 Machine systemd[1]: Stopped Message of the Day.
Aug 18 02:03:16 Machine /usr/lib/gdm3/gdm-x-session[1822]: (**) Option "fd" "48"
Aug 18 02:03:16 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event2  - Power Button: device removed
Aug 18 02:03:16 Machine /usr/lib/gdm3/gdm-x-session[1822]: (**) Option "fd" "46"
Aug 18 02:03:16 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event1  - Power Button: device removed
Aug 18 02:03:16 Machine /usr/lib/gdm3/gdm-x-session[1822]: (**) Option "fd" "29"
Aug 18 02:03:16 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event0  - Sleep Button: device removed
Aug 18 02:03:16 Machine /usr/lib/gdm3/gdm-x-session[1822]: (**) Option "fd" "43"
Aug 18 02:03:16 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event5  - Genius Optical Mouse: device removed
Aug 18 02:03:16 Machine /usr/lib/gdm3/gdm-x-session[1822]: (**) Option "fd" "28"
Aug 18 02:03:16 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event4  - CHICONY HP Basic USB Keyboard: device removed
Aug 18 02:03:16 Machine /usr/lib/gdm3/gdm-x-session[1822]: (**) Option "fd" "47"
Aug 18 02:03:16 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event6  - Eee PC WMI hotkeys: device removed
Aug 18 02:03:16 Machine /usr/lib/gdm3/gdm-x-session[1822]: (**) Option "fd" "63"
Aug 18 02:03:16 Machine /usr/lib/gdm3/gdm-x-session[1822]: (II) event3  - Video Bus: device removed
Aug 18 02:03:16 Machine systemd[1784]: Stopped D-Bus User Message Bus.
Aug 18 02:03:16 Machine systemd[1784]: Started D-Bus User Message Bus.
Aug 18 02:03:16 Machine systemd[1]: Stopping PackageKit Daemon...
Aug 18 02:03:16 Machine systemd[1]: Stopped Stop ureadahead data collection 45s after completed startup.
Aug 18 02:03:16 Machine systemd[1]: Removed slice system-getty.slice.
Aug 18 02:03:16 Machine systemd[1]: Stopped Daily apt upgrade and clean activities.
Aug 18 02:03:16 Machine systemd[1]: Stopped Daily apt download activities.
Aug 18 02:03:16 Machine systemd[1]: Stopping Daemon for power management...
Aug 18 02:03:16 Machine systemd[1]: Stopping User Manager for UID 121...
Aug 18 02:03:16 Machine systemd[1]: Stopped target Graphical Interface.
Aug 18 02:03:16 Machine systemd[1]: Stopping Accounts Service...
Aug 18 02:03:16 Machine systemd[1]: Stopped target Multi-User System.
Aug 18 02:03:16 Machine bluetoothd[1460]: Stopping SDP server
Aug 18 02:03:16 Machine systemd[1]: Stopping vboxweb-service.service...
Aug 18 02:03:16 Machine bluetoothd[1460]: Exit
Aug 18 02:03:16 Machine systemd[1]: Stopping Regular background program processing daemon...
Aug 18 02:03:16 Machine canonical-livepatch[1552]: stopping client daemon
Aug 18 02:03:16 Machine systemd[1]: Stopping Dispatcher daemon for systemd-networkd...
Aug 18 02:03:16 Machine canonical-livepatch[1552]: stopping service "mitigation loop"
Aug 18 02:03:16 Machine systemd[1]: Stopping Service for snap application canonical-livepatch.canonical-livepatchd...
Aug 18 02:03:16 Machine canonical-livepatch[1552]: service "mitigation loop" stopped
Aug 18 02:03:16 Machine systemd[1]: Stopping Thermal Daemon Service...
Aug 18 02:03:16 Machine canonical-livepatch[1552]: stopping service "socket servers"
Aug 18 02:03:16 Machine canonical-livepatch[1552]: while starting HTTP server: accept unix /var/snap/canonical-livepatch/95/livepatchd-priv.sock: use of closed network connection
Aug 18 02:03:16 Machine canonical-livepatch[1552]: while starting HTTP server: accept unix /var/snap/canonical-livepatch/95/livepatchd.sock: use of closed network connection
Aug 18 02:03:16 Machine canonical-livepatch[1552]: service "socket servers" stopped
Aug 18 02:03:16 Machine canonical-livepatch[1552]: stopping service "refresh loop"
Aug 18 02:03:16 Machine canonical-livepatch[1552]: service "refresh loop" stopped
Aug 18 02:03:16 Machine canonical-livepatch[1552]: client daemon stopped

```

---

