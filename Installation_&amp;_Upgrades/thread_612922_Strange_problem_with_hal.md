---
title: "Strange problem with hal"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by vikrant82 on 2007-11-14
Hi, 

I am facing a peculiar problem. 
All my services (hald , dbus, dhcdbd ..) start up properly without any error messages in logs. 

However, on system startup gnome-power-manager cant detect the battery. And the icon is always on AC. Neither I see "On Battery Power" in preferences. However /proc/acpi/battery /proc/acpi/ac_adapter shows correct battery and adapter states at the same time.

However as soon as I manually restart hald, gnome-power-manager detects the battery and *white* AC icon turns to one with battery plugged in.

This is what gnome-power-manager --no-daemon --verbose had to say  : 
```
[gpm_debug_init] gpm-debug.c:236 (23:17:23):     Verbose debugging enabled
[main] gpm-main.c:218 (23:17:23):        GNOME Power Manager 2.20.0
[gpm_ac_adapter_init] gpm-ac-adapter.c:229 (23:17:23):   No devices of capability ac_adapter
[gpm_control_init] gpm-control.c:657 (23:17:23):         Using a supressed policy timeout of 5 seconds
[coldplug_buttons] gpm-button.c:445 (23:17:23):  Watching /org/freedesktop/Hal/devices/computer_logicaldev_input_4
[coldplug_buttons] gpm-button.c:445 (23:17:23):  Watching /org/freedesktop/Hal/devices/computer_logicaldev_input_3
[coldplug_buttons] gpm-button.c:445 (23:17:23):  Watching /org/freedesktop/Hal/devices/computer_logicaldev_input_2
[coldplug_buttons] gpm-button.c:445 (23:17:23):  Watching /org/freedesktop/Hal/devices/computer_logicaldev_input_1
[coldplug_buttons] gpm-button.c:445 (23:17:23):  Watching /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input
[gpm_webcam_get_image] gpm-webcam.c:91 (23:17:23):       Creating source /dev/video0
[gpm_webcam_get_image] gpm-webcam.c:99 (23:17:23):       Creating sink /home/kx/.gnome2/gnome-power-manager/webcam.png
[gpm_webcam_get_image] gpm-webcam.c:106 (23:17:23):      Link together
[gpm_webcam_get_image] gpm-webcam.c:114 (23:17:23):      Set playing
[gpm_webcam_get_image] gpm-webcam.c:139 (23:17:23):      Cleanup
[gpm_prefs_server_set_capability] gpm-prefs-server.c:84 (23:17:23):      capability now 4
*** WARNING ***
[gpm_light_sensor_get_absolute] gpm-light-sensor.c:149 (23:17:23):       no hardware!
*** WARNING ***
[gpm_backlight_brightness_evaluate_and_set] gpm-backlight.c:361 (23:17:23):      no dimming hardware
[gpm_backlight_sync_policy] gpm-backlight.c:158 (23:17:23):      choosing sensible default
[gpm_backlight_sync_policy] gpm-backlight.c:160 (23:17:23):      laptop, so use GPM_DPMS_METHOD_OFF
[gpm_backlight_sync_policy] gpm-backlight.c:192 (23:17:23):      BACKLIGHT parameters 0 0 1800, method '4'
[gpm_dpms_set_enabled] gpm-dpms.c:408 (23:17:23):        setting DPMS enabled: 1
[x11_sync_server_dpms_settings] gpm-dpms.c:130 (23:17:23):       Syncing DPMS settings enabled=1 timeouts=0 0 0
[x11_sync_server_dpms_settings] gpm-dpms.c:130 (23:17:23):       Syncing DPMS settings enabled=1 timeouts=0 0 0
[gpm_idle_set_check_cpu] gpm-idle.c:236 (23:17:23):      Setting the CPU load check to 0
[gpm_manager_init] gpm-manager.c:1719 (23:17:23):        creating new inhibit instance
[gpm_manager_init] gpm-manager.c:1729 (23:17:23):        creating new control instance
[gpm_manager_init] gpm-manager.c:1734 (23:17:23):        creating new tray icon
[gpm_manager_init] gpm-manager.c:1743 (23:17:23):        initialising info infrastructure
[gpm_profile_init] gpm-profile.c:909 (23:17:23):         creating new control instance
[gpm_profile_init] gpm-profile.c:930 (23:17:23):         on AC
[gpm_idle_set_system_timeout] gpm-idle.c:287 (23:17:23):         Setting system idle timeout: 0
[gpm_warnings_init] gpm-warnings.c:266 (23:17:23):       Using per-time notification policy
[gpm_phone_dbus_connect] gpm-phone.c:267 (23:17:23):     get connection

[gpm_phone_dbus_connect] gpm-phone.c:278 (23:17:23):     get proxy

*** WARNING ***
[gpm_phone_dbus_connect] gpm-phone.c:286 (23:17:23):     Cannot connect, maybe the daemon is not running: Could not get owner of name 'org.gnome.phone': no such name

[gpm_cell_array_update] gpm-cell-array.c:277 (23:17:23):         no devices of type 0
[gpm_cell_array_update] gpm-cell-array.c:277 (23:17:23):         no devices of type 1
[gpm_cell_array_update] gpm-cell-array.c:277 (23:17:23):         no devices of type 2
[gpm_cell_array_update] gpm-cell-array.c:277 (23:17:23):         no devices of type 3
[gpm_cell_array_update] gpm-cell-array.c:277 (23:17:23):         no devices of type 5
*** WARNING ***
[gpm_phone_coldplug] gpm-phone.c:79 (23:17:23):  not connected

[gpm_cell_array_update] gpm-cell-array.c:277 (23:17:23):         no devices of type 4
[gpm_engine_get_icon] gpm-engine.c:391 (23:17:23):       Trying CRITICAL icon: primary, ups, mouse, keyboard
*** WARNING ***
[gpm_warnings_get_state_time] gpm-warnings.c:85 (23:17:23):      time zero, something's gone wrong
*** WARNING ***
[gpm_warnings_get_state_percentage] gpm-warnings.c:104 (23:17:23):       percentage zero, something's gone wrong
*** WARNING ***
[gpm_warnings_get_state_percentage] gpm-warnings.c:104 (23:17:23):       percentage zero, something's gone wrong
*** WARNING ***
[gpm_warnings_get_state_percentage] gpm-warnings.c:104 (23:17:23):       percentage zero, something's gone wrong
[gpm_engine_get_icon] gpm-engine.c:423 (23:17:23):       Trying CHARGING icon: primary, ups
[gpm_engine_get_icon] gpm-engine.c:440 (23:17:23):       Trying PRESENT icon: primary, ups
[gpm_engine_get_icon] gpm-engine.c:455 (23:17:23):       Using fallback
[gpm_engine_recalculate_state_icon] gpm-engine.c:563 (23:17:23):         ** EMIT: icon-changed: gpm-ac-adapter
[gpm_tray_icon_set_icon] gpm-tray-icon.c:173 (23:17:23):         Setting icon to gpm-ac-adapter
[gpm_engine_get_summary] gpm-engine.c:349 (23:17:24):    tooltip: Computer is running on AC power
[gpm_engine_recalculate_state_summary] gpm-engine.c:603 (23:17:24):      ** EMIT: summary-changed(1): Computer is running on AC power
[gconf_key_changed_cb] gpm-conf.c:332 (23:17:24):        emitting value-changed : '/apps/gnome-screensaver/power_management_delay'
[gconf_key_changed_cb] gpm-screensaver.c:181 (23:17:24):         key : /apps/gnome-screensaver/power_management_delay
```

Any clues, why hald is not reporting battery to g p m ? Or how to debug this ?

Thanks,

---

### Post by vikrant82 on 2007-11-15
](*,)

---

### Post by ukripper on 2007-11-15
This may help - [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/32665](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/32665)

---

