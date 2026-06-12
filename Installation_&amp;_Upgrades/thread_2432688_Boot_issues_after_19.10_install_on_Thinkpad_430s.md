---
title: "Boot issues after 19.10 install on Thinkpad 430s"
date: 2019-12-06
forum: Installation &amp; Upgrades
---

### Post by the-pad on 2019-12-06
Hi Ubuntu Forums,

my boot procedure seems to get stuck from time to time on my Thinkpad 430s after installing 19.10 (fresh install). I didn't see this problem with 18.04.

The boot is stuck at the ubuntu logo and this dotted bar and it doesn't continue.
Trying to switch to a different login with ctrl+alt+FX doesn't work.
Normally it works again after forcing power off and rebooting a couple of times.

I ran the command journalctl -g "error|failed" for a normal boot and a failed boot but I don't know how to interpret the information?

For some reason I can't upload the files as attachment here, they don't show up as uploaded even after I selected the file and clicked "upload".

So, here is output inlined:
**FAILED BOOT:**
```
-- Logs begin at Tue 2019-08-20 20:58:13 CEST, end at Fri 2019-12-06 20:24:38 CET. --Dez 06 19:16:43 kai-ThinkPad-T430s kernel: acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPM
Dez 06 19:16:43 kai-ThinkPad-T430s kernel: RAS: Correctable Errors collector initialized.
Dez 06 19:16:43 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:16:43 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:16:43 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:16:43 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:16:43 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:16:43 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:16:43 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:16:43 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:16:43 kai-ThinkPad-T430s systemd[1]: Failed to bump fs.file-max, ignoring: Invalid argument
Dez 06 19:16:43 kai-ThinkPad-T430s kernel: EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
Dez 06 19:16:44 kai-ThinkPad-T430s kernel: usb 1-1.4: device descriptor read/all, error -32
Dez 06 19:16:44 kai-ThinkPad-T430s systemd-udevd[405]: Process '/usr/sbin/alsactl -E HOME=/run/alsa restore 0' failed with exit code 99.
Dez 06 19:16:45 kai-ThinkPad-T430s systemd[1]: Started Process error reports when automatic reporting is enabled (file watch).
Dez 06 19:16:45 kai-ThinkPad-T430s systemd[1]: Starting GRUB failed boot detection...
Dez 06 19:16:45 kai-ThinkPad-T430s thermald[970]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
Dez 06 19:16:45 kai-ThinkPad-T430s thermald[970]: [WARN]error: could not parse file /etc/thermald/thermal-conf.xml
Dez 06 19:16:45 kai-ThinkPad-T430s thermald[970]: [WARN]sysfs write failed /sys/devices/virtual/powercap/intel-rapl/intel-rapl:0/enabled
Dez 06 19:16:45 kai-ThinkPad-T430s thermald[970]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
Dez 06 19:16:45 kai-ThinkPad-T430s thermald[970]: [WARN]error: could not parse file /etc/thermald/thermal-conf.xml
Dez 06 19:16:45 kai-ThinkPad-T430s thermald[970]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
Dez 06 19:16:45 kai-ThinkPad-T430s thermald[970]: [WARN]error: could not parse file /etc/thermald/thermal-conf.xml
Dez 06 19:16:45 kai-ThinkPad-T430s systemd[1]: Started GRUB failed boot detection.
Dez 06 19:16:45 kai-ThinkPad-T430s udisksd[1015]: failed to load module mdraid: libbd_mdraid.so.2: cannot open shared object file: No such file or directory
Dez 06 19:16:45 kai-ThinkPad-T430s udisksd[1015]: Failed to load the 'mdraid' libblockdev plugin
Dez 06 19:16:46 kai-ThinkPad-T430s NetworkManager[999]: <warn>  [1575656206.5983] Error: failed to open /run/network/ifstate
Dez 06 19:16:46 kai-ThinkPad-T430s wpa_supplicant[1022]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface.P2PDevice dbus_property=P2PDeviceConfig getter failed
Dez 06 19:16:47 kai-ThinkPad-T430s gnome-session-c[1213]: Error creating FIFO: File exists
Dez 06 19:16:50 kai-ThinkPad-T430s systemd-resolved[730]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Dez 06 19:16:50 kai-ThinkPad-T430s systemd-resolved[730]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Dez 06 19:16:50 kai-ThinkPad-T430s gnome-shell[1233]: Unable to connect to ibus: Error receiving data: Connection reset by peer
Dez 06 19:16:50 kai-ThinkPad-T430s systemd-resolved[730]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Dez 06 19:16:50 kai-ThinkPad-T430s gnome-shell[1233]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
Dez 06 19:16:50 kai-ThinkPad-T430s gsd-media-keys[1391]: Failed to grab accelerator for keybinding settings:hibernate
Dez 06 19:16:50 kai-ThinkPad-T430s gsd-media-keys[1391]: Failed to grab accelerator for keybinding settings:rfkill
Dez 06 19:16:50 kai-ThinkPad-T430s gsd-media-keys[1391]: Failed to grab accelerator for keybinding settings:screen-brightness-cycle
Dez 06 19:16:50 kai-ThinkPad-T430s gsd-media-keys[1391]: Failed to grab accelerator for keybinding settings:playback-repeat
Dez 06 19:16:50 kai-ThinkPad-T430s gsd-media-keys[1391]: Failed to grab accelerator for keybinding settings:playback-random
Dez 06 19:16:50 kai-ThinkPad-T430s gnome-shell[1233]: Failed to DPMS: Failed to set connector 67 property 2: Permission denied
Dez 06 19:16:50 kai-ThinkPad-T430s colord[1500]: failed to get session [pid 1412]: No data available
Dez 06 19:16:50 kai-ThinkPad-T430s gnome-shell[1233]: Failed to CRTC gamma: drmModeCrtcSetGamma on CRTC 42 failed: Permission denied
Dez 06 19:16:51 kai-ThinkPad-T430s colord-sane[1504]: [bjnp] create_broadcast_socket: ERROR - bind socket to local address failed - Cannot assign requested address
Dez 06 19:16:52 kai-ThinkPad-T430s systemd[1]: Starting Process error reports when automatic reporting is enabled...
Dez 06 19:16:52 kai-ThinkPad-T430s systemd[1]: Started Process error reports when automatic reporting is enabled.
Dez 06 19:17:13 kai-ThinkPad-T430s dbus-daemon[974]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
```

[B]SUCCESSFUL BOOT:
[/B]```
-- Logs begin at Tue 2019-08-20 20:58:13 CEST, end at Fri 2019-12-06 20:24:38 CET. --Dez 06 19:26:12 kai-ThinkPad-T430s kernel: acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPM
Dez 06 19:26:12 kai-ThinkPad-T430s kernel: RAS: Correctable Errors collector initialized.
Dez 06 19:26:12 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:26:12 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:26:12 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:26:12 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:26:12 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:26:12 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:26:12 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:26:12 kai-ThinkPad-T430s kernel: ima: Error Communicating to TPM chip
Dez 06 19:26:12 kai-ThinkPad-T430s systemd[1]: Failed to bump fs.file-max, ignoring: Invalid argument
Dez 06 19:26:12 kai-ThinkPad-T430s kernel: EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
Dez 06 19:26:13 kai-ThinkPad-T430s kernel: usb 1-1.4: device not accepting address 6, error -32
Dez 06 19:26:13 kai-ThinkPad-T430s systemd-udevd[463]: Process '/usr/sbin/alsactl -E HOME=/run/alsa restore 0' failed with exit code 99.
Dez 06 19:26:13 kai-ThinkPad-T430s systemd[1]: Started Process error reports when automatic reporting is enabled (file watch).
Dez 06 19:26:13 kai-ThinkPad-T430s systemd[1]: Starting GRUB failed boot detection...
Dez 06 19:26:13 kai-ThinkPad-T430s systemd[1]: Started GRUB failed boot detection.
Dez 06 19:26:14 kai-ThinkPad-T430s thermald[897]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
Dez 06 19:26:14 kai-ThinkPad-T430s thermald[897]: [WARN]error: could not parse file /etc/thermald/thermal-conf.xml
Dez 06 19:26:14 kai-ThinkPad-T430s thermald[897]: [WARN]sysfs write failed /sys/devices/virtual/powercap/intel-rapl/intel-rapl:0/enabled
Dez 06 19:26:14 kai-ThinkPad-T430s thermald[897]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
Dez 06 19:26:14 kai-ThinkPad-T430s thermald[897]: [WARN]error: could not parse file /etc/thermald/thermal-conf.xml
Dez 06 19:26:14 kai-ThinkPad-T430s thermald[897]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
Dez 06 19:26:14 kai-ThinkPad-T430s thermald[897]: [WARN]error: could not parse file /etc/thermald/thermal-conf.xml
Dez 06 19:26:14 kai-ThinkPad-T430s udisksd[938]: failed to load module mdraid: libbd_mdraid.so.2: cannot open shared object file: No such file or directory
Dez 06 19:26:14 kai-ThinkPad-T430s udisksd[938]: Failed to load the 'mdraid' libblockdev plugin
Dez 06 19:26:15 kai-ThinkPad-T430s NetworkManager[921]: <warn>  [1575656775.3567] Error: failed to open /run/network/ifstate
Dez 06 19:26:15 kai-ThinkPad-T430s wpa_supplicant[932]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface.P2PDevice dbus_property=P2PDeviceConfig getter failed
Dez 06 19:26:16 kai-ThinkPad-T430s gnome-session-c[1214]: Error creating FIFO: File exists
Dez 06 19:26:19 kai-ThinkPad-T430s gnome-shell[1232]: ibus_bus_hello: assertion 'ibus_bus_is_connected (bus)' failed
Dez 06 19:26:19 kai-ThinkPad-T430s gnome-shell[1232]: Error while sending AddMatch() message: The connection is closed
Dez 06 19:26:19 kai-ThinkPad-T430s gnome-shell[1232]: ibus_bus_call_async: assertion 'ibus_bus_is_connected (bus)' failed
Dez 06 19:26:19 kai-ThinkPad-T430s gnome-shell[1232]: ibus_bus_call_async: assertion 'ibus_bus_is_connected (bus)' failed
Dez 06 19:26:19 kai-ThinkPad-T430s systemd-resolved[686]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Dez 06 19:26:19 kai-ThinkPad-T430s systemd-resolved[686]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Dez 06 19:26:19 kai-ThinkPad-T430s systemd-resolved[686]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Dez 06 19:26:19 kai-ThinkPad-T430s gnome-shell[1232]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
Dez 06 19:26:19 kai-ThinkPad-T430s gsd-media-keys[1402]: Failed to grab accelerator for keybinding settings:screen-brightness-cycle
Dez 06 19:26:19 kai-ThinkPad-T430s gsd-media-keys[1402]: Failed to grab accelerator for keybinding settings:rfkill
Dez 06 19:26:19 kai-ThinkPad-T430s gsd-media-keys[1402]: Failed to grab accelerator for keybinding settings:playback-repeat
Dez 06 19:26:19 kai-ThinkPad-T430s gsd-media-keys[1402]: Failed to grab accelerator for keybinding settings:hibernate
Dez 06 19:26:19 kai-ThinkPad-T430s gsd-media-keys[1402]: Failed to grab accelerator for keybinding settings:playback-random
Dez 06 19:26:19 kai-ThinkPad-T430s colord[1497]: failed to get session [pid 1397]: No data available
Dez 06 19:26:19 kai-ThinkPad-T430s colord-sane[1503]: [bjnp] create_broadcast_socket: ERROR - bind socket to local address failed - Cannot assign requested address
Dez 06 19:26:20 kai-ThinkPad-T430s systemd[1]: Starting Process error reports when automatic reporting is enabled...
Dez 06 19:26:21 kai-ThinkPad-T430s systemd[1]: Started Process error reports when automatic reporting is enabled.
Dez 06 19:26:24 kai-ThinkPad-T430s /usr/lib/gdm3/gdm-x-session[1590]:         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
Dez 06 19:26:24 kai-ThinkPad-T430s /usr/lib/gdm3/gdm-x-session[1590]: xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
Dez 06 19:26:25 kai-ThinkPad-T430s gnome-session-c[1753]: Error creating FIFO: File exists
Dez 06 19:26:25 kai-ThinkPad-T430s xdg-desktop-por[1738]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: Cannot invoke method; proxy is for the well-known name org.gnome.Shell without an owner, and proxy was constructed with the G_DBUS_PROXY_FLAGS_DO_NOT_AUTO_START flag
Dez 06 19:26:27 kai-ThinkPad-T430s gnome-shell[1808]: ibus_bus_hello: assertion 'ibus_bus_is_connected (bus)' failed
Dez 06 19:26:27 kai-ThinkPad-T430s gnome-shell[1808]: Error while sending AddMatch() message: The connection is closed
Dez 06 19:26:27 kai-ThinkPad-T430s gnome-shell[1808]: ibus_bus_call_async: assertion 'ibus_bus_is_connected (bus)' failed
Dez 06 19:26:27 kai-ThinkPad-T430s gnome-shell[1808]: ibus_bus_call_async: assertion 'ibus_bus_is_connected (bus)' failed
Dez 06 19:26:27 kai-ThinkPad-T430s gsd-sharing[1968]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-user-share-webdav.service not loaded.
Dez 06 19:26:27 kai-ThinkPad-T430s gsd-sharing[1968]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-remote-desktop.service not loaded.
Dez 06 19:26:28 kai-ThinkPad-T430s gnome-shell[1232]: Failed to CRTC gamma: drmModeCrtcSetGamma on CRTC 42 failed: Permission denied
Dez 06 19:26:28 kai-ThinkPad-T430s gnome-shell[1808]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
Dez 06 19:26:28 kai-ThinkPad-T430s gsd-media-keys[1950]: Failed to grab accelerator for keybinding settings:playback-random
Dez 06 19:26:28 kai-ThinkPad-T430s gsd-media-keys[1950]: Failed to grab accelerator for keybinding settings:screen-brightness-cycle
Dez 06 19:26:28 kai-ThinkPad-T430s gsd-media-keys[1950]: Failed to grab accelerator for keybinding settings:playback-repeat
Dez 06 19:26:28 kai-ThinkPad-T430s gsd-media-keys[1950]: Failed to grab accelerator for keybinding settings:hibernate
Dez 06 19:26:28 kai-ThinkPad-T430s gsd-media-keys[1950]: Failed to grab accelerator for keybinding settings:rfkill
Dez 06 19:26:28 kai-ThinkPad-T430s colord[1497]: failed to get session [pid 1929]: No data available
Dez 06 19:26:28 kai-ThinkPad-T430s gnome-shell[1232]: Failed to CRTC gamma: drmModeCrtcSetGamma on CRTC 42 failed: Permission denied
Dez 06 19:26:30 kai-ThinkPad-T430s gsd-color[1929]: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/xrandr_Seiko_Epson_Corporation_gdm_123
Dez 06 19:26:30 kai-ThinkPad-T430s systemd[1185]: xdg-permission-store.service: Failed with result 'exit-code'.
Dez 06 19:26:41 kai-ThinkPad-T430s dbus-daemon[917]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
Dez 06 19:26:41 kai-ThinkPad-T430s pulseaudio[1580]: E: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
Dez 06 19:26:42 kai-ThinkPad-T430s gnome-software[2328]: g_path_get_basename: assertion 'file_name != NULL' failed
Dez 06 19:26:42 kai-ThinkPad-T430s gnome-software[2328]: g_regex_match_full: assertion 'string != NULL' failed
Dez 06 19:26:42 kai-ThinkPad-T430s gnome-software[2328]: g_path_get_basename: assertion 'file_name != NULL' failed
Dez 06 19:26:42 kai-ThinkPad-T430s gnome-software[2328]: g_regex_match_full: assertion 'string != NULL' failed
Dez 06 19:26:42 kai-ThinkPad-T430s gnome-software[2328]: Failed to load snap icon: local snap has no icon
Dez 06 19:26:43 kai-ThinkPad-T430s gnome-software[2328]: Failed to load snap icon: local snap has no icon
Dez 06 19:26:46 kai-ThinkPad-T430s gnome-software[2328]: Failed to find one package for google-earth-pro.desktop, /usr/share/applications/google-earth-pro.desktop, [0]
Dez 06 19:26:48 kai-ThinkPad-T430s tracker-miner-f[2032]: tracker_file_system_set_property: assertion 'file != NULL' failed
Dez 06 19:26:48 kai-ThinkPad-T430s tracker-miner-f[2032]: tracker_file_system_set_property: assertion 'file != NULL' failed
Dez 06 19:26:48 kai-ThinkPad-T430s tracker-miner-f[2032]: tracker_file_system_set_property: assertion 'file != NULL' failed
Dez 06 19:26:48 kai-ThinkPad-T430s tracker-miner-f[2032]: tracker_file_system_set_property: assertion 'file != NULL' failed
Dez 06 19:26:48 kai-ThinkPad-T430s tracker-miner-f[2032]: tracker_file_system_set_property: assertion 'file != NULL' failed
Dez 06 19:26:48 kai-ThinkPad-T430s tracker-miner-f[2032]: tracker_file_system_set_property: assertion 'file != NULL' failed
Dez 06 19:26:51 kai-ThinkPad-T430s gnome-software[2328]: Failed to load snap icon: local snap has no icon
Dez 06 19:26:51 kai-ThinkPad-T430s gnome-software[2328]: Failed to load snap icon: local snap has no icon
Dez 06 19:26:51 kai-ThinkPad-T430s gnome-software[2328]: Failed to load snap icon: local snap has no icon
Dez 06 19:26:51 kai-ThinkPad-T430s gnome-software[2328]: Failed to load snap icon: local snap has no icon
Dez 06 19:26:51 kai-ThinkPad-T430s gnome-software[2328]: Failed to load snap icon: local snap has no icon
Dez 06 19:26:52 kai-ThinkPad-T430s gnome-software[2328]: Failed to load snap icon: local snap has no icon
Dez 06 19:26:52 kai-ThinkPad-T430s gnome-software[2328]: Failed to load snap icon: local snap has no icon
Dez 06 19:26:52 kai-ThinkPad-T430s gnome-software[2328]: Failed to load snap icon: local snap has no icon
Dez 06 19:26:52 kai-ThinkPad-T430s gnome-software[2328]: Failed to load snap icon: local snap has no icon
Dez 06 19:26:52 kai-ThinkPad-T430s tracker-miner-fs.desktop[2032]: Tracker:ERROR:../src/libtracker-miner/tracker-file-system.c:259:file_tree_lookup: assertion failed: (ptr[0] == '/')
Dez 06 19:26:52 kai-ThinkPad-T430s tracker-miner-fs.desktop[2032]: Bail out! Tracker:ERROR:../src/libtracker-miner/tracker-file-system.c:259:file_tree_lookup: assertion failed: (ptr[0] == '/')
Dez 06 19:27:14 kai-ThinkPad-T430s gnome-software[2328]: not GsPlugin error g-io-error-quark:19: Operation was cancelled
Dez 06 19:27:14 kai-ThinkPad-T430s gnome-software[2328]: not handling error failed for action refine: Operation was cancelled
Dez 06 19:27:18 kai-ThinkPad-T430s remmina[3121]: g_signal_handlers_disconnect_matched: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Dez 06 19:27:18 kai-ThinkPad-T430s remmina[3121]: gtk_menu_detach: assertion 'GTK_IS_MENU (menu)' failed
Dez 06 19:27:26 kai-ThinkPad-T430s xdg-desktop-por[1738]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: App introspection not allowed
Dez 06 19:27:37 kai-ThinkPad-T430s gnome-software[2328]: g_path_get_basename: assertion 'file_name != NULL' failed
Dez 06 19:27:37 kai-ThinkPad-T430s gnome-software[2328]: g_regex_match_full: assertion 'string != NULL' failed
Dez 06 19:27:37 kai-ThinkPad-T430s gnome-software[2328]: g_path_get_basename: assertion 'file_name != NULL' failed
Dez 06 19:27:37 kai-ThinkPad-T430s gnome-software[2328]: g_regex_match_full: assertion 'string != NULL' failed
Dez 06 19:27:38 kai-ThinkPad-T430s gnome-software[2328]: Failed to find one package for google-earth-pro.desktop, /usr/share/applications/google-earth-pro.desktop, [0]
Dez 06 19:27:38 kai-ThinkPad-T430s gnome-software[2328]: Failed to load snap icon: local snap has no icon
Dez 06 19:28:26 kai-ThinkPad-T430s xdg-desktop-por[1738]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: App introspection not allowed
Dez 06 19:29:12 kai-ThinkPad-T430s gnome-shell[1808]: st_widget_add_style_pseudo_class: assertion 'ST_IS_WIDGET (actor)' failed
Dez 06 19:29:12 kai-ThinkPad-T430s gnome-shell[1808]: clutter_actor_get_allocation_box: assertion 'CLUTTER_IS_ACTOR (self)' failed
Dez 06 19:29:12 kai-ThinkPad-T430s gnome-shell[1808]: clutter_actor_get_parent: assertion 'CLUTTER_IS_ACTOR (self)' failed
Dez 06 19:29:12 kai-ThinkPad-T430s gnome-shell[1808]: JS ERROR: Error: actor not in scroll view
                                                      ensureActorVisibleInScrollView@resource:///org/gnome/shell/misc/util.js:412:19
                                                      _setSelected@resource:///org/gnome/shell/ui/search.js:765:13
                                                      highlightDefault@resource:///org/gnome/shell/ui/search.js:732:9
                                                      ViewSelector</<@resource:///org/gnome/shell/ui/viewSelector.js:144:13
Dez 06 19:29:14 kai-ThinkPad-T430s gnome-shell[1808]: st_widget_remove_style_pseudo_class: assertion 'ST_IS_WIDGET (actor)' failed
Dez 06 19:29:23 kai-ThinkPad-T430s chrome[4079]: Failed to load module "canberra-gtk-module"
Dez 06 19:29:23 kai-ThinkPad-T430s chrome[4079]: Failed to load module "canberra-gtk-module"
```

Could someone give me a hint how to debug this annoying issue?

Edit:
Link to boot-repair summary report: [https://paste.ubuntu.com/p/Xdwr985VXk/](https://paste.ubuntu.com/p/Xdwr985VXk/)

Update (solved):
I updated my BIOS and EFI to the latest available version (2.76).
Then I reinstalled Ubuntu 19.10 freshly and without LVM but normal partitions.
I don't know what was the root cause of the issue in the end but since then I had no more failed boots.

Many thanks and best regards,
Kai

---

### Post by oldfred on 2019-12-07
I would think this is the major issue.
Started GRUB failed boot detection.

But then why is grub not seeing drive? 
Or did you install in BIOS mode and booting in UEFI sometimes?
Or drive is slow coming up to speed and then grub cannot find it?
If it boots sometimes, I do not think Boot-Repair report will show much, but just to confirm everything is ok.

 May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by the-pad on 2019-12-10
Thanks for your reply. 
Please find the link to the boot-repair summary report here: [https://paste.ubuntu.com/p/Xdwr985VXk/](https://paste.ubuntu.com/p/Xdwr985VXk/)

I think your hint with UEFI and BIOS might be a good indication. I had one case where it didn't boot anymore but when I switched off the fast boot option in bios and booted again. 
Is there a way to see if the installation was done in UEFI or BIOS mode?

Edit:
What are the pros and cons of UEFI vs. BIOS? I found quite some information on how to install one way or the other way and also some explanations which way is better / necessary for dual boot setups. But for a single boot setup. Is there any option that should be preferred?

---

### Post by slickymaster on 2019-12-10
*Thread moved to **Installation & Upgrades**.*

---

### Post by yancek on 2019-12-10
On a successfull boot of Ubuntu, open a terminal and run the command below, exactly as is, it will either output "EFI" or "Legacy":

```
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
```


Pros and cons are discussed at the link below and at many more sites if you do an online search.

[https://pediaa.com/difference-between-uefi-and-legacy-boot/](https://pediaa.com/difference-between-uefi-and-legacy-boot/)

Looking at your boot repair output, it shows that you have the older Legacy install with LVM and encryption.  I don't use either LVM or encryption so can't help with that.  Good luck.

---

### Post by oldfred on 2019-12-10
You have grub in the MBR and no ESP - efi system partition.
Your system is UEFI as report showed a couple of default Lenovo UEFI entries.

So you are booting in the now 35 year old BIOS/MBR configuration. Some still like BIOS as they know it.
If your system is not set to only boot in CSM/Legacy/BIOS mode, it may be trying to boot in UEFI mode and then not finding any UEFI boot, defaulting to try a BIOS boot.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off. 

I also do not know LVM, nor if there still are any advantages to BIOS or not. I am one that promotes UEFI with gpt partitioning, but early systems with UEFI (starting 2012) had a lot of issues. Most of those issues are resolved, but all systems still have bugs.

Lots of info on UEFI in link in my signature.

One of the advantages of UEFI is not UEFI, but the gpt partitioning. With gpt you have a back up partition table at the end of the drive and additional error checks. Windows requires gpt with UEFI, but Ubuntu will install in BIOS mode to MBR(msdos) partitioned drives (maybe it should not).
I converted to gpt with my BIOS only system in 2010, but BIOS needs bios_grub partition for grub to install in BIOS boot mode to gpt drive.

---

### Post by the-pad on 2019-12-10
So, running the command confirmed that my installation is the "legacy" install. 
My system setup shows that both boot modes were active with priorities set to "first legacy". For now, I set it to "legacy only". Let's see if it keeps booting normally, if it keeps booting normally for a couple of days, I will mark this thread as "solved". 
And then, as soon as I find some time I think I will run some bios updates and install again with an EFI only image.

@yancek: 
I ran the standard Ubuntu installer with default options. I wasn't aware about the encryption? In which line do see this information?

---

### Post by oldfred on 2019-12-10
I did not see anything on encryption.
Usually LVM is only used on desktops if a user wants full drive encryption.

LVM is most often used with servers or those who know & use servers a lot.
Standard desktop install is using MBR or gpt partitions without LVM.

---

### Post by the-pad on 2019-12-17
So, some bad news. After a couple of successful boots I had another failed one with the same issues.

Would it make sense to post a full journalctl output? Or could someone give me a hint on what to look for?
Otherwise the next steps I would try are:
1. BIOS Updates (my version is from 2012)
2. Fresh EFI install without LVM just normal partitions.

Cheers,
Kai

---

### Post by oldfred on 2019-12-17
If there is a UEFI update, I would do that first.

I do not think there is anything in these older posts about similar Lenovo systems. But perhaps someone posted something. I would expect newer Ubuntu to work or work better.
       Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by the-pad on 2020-01-08
Update: The issue seems to be solved.

I updated my BIOS and EFI to the latest available version (2.76).
Then I reinstalled Ubuntu 19.10 freshly and without LVM but normal partitions.
I don't know what was the root cause of the issue in the end but since then I had no more failed boots.

---

