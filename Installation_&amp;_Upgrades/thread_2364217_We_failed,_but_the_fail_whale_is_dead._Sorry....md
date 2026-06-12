---
title: "We failed, but the fail whale is dead. Sorry..."
date: 2017-06-20
forum: Installation &amp; Upgrades
---

### Post by hskoglund on 2017-06-20
Hi, today I upgraded my Ubuntu 16.04.02 from 4.4.0-79 to 4.4.0-81. When I rebooted I could not login on the desktop any more, every time this appeared in syslog:
```
Jun 20 15:08:14 DrTungsLinux org.ayatana.bamf[4377]: bamfdaemon start/running, process 4449
Jun 20 15:08:14 DrTungsLinux org.a11y.Bus[4377]: ** (process:4471): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Jun 20 15:08:14 DrTungsLinux org.a11y.Bus[4377]: Activating service name='org.a11y.atspi.Registry'
Jun 20 15:08:14 DrTungsLinux org.a11y.Bus[4377]: Successfully activated service 'org.a11y.atspi.Registry'
Jun 20 15:08:14 DrTungsLinux org.a11y.atspi.Registry[4476]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun 20 15:08:16 DrTungsLinux gnome-session[4599]: Xlib:  extension "GLX" missing on display ":0".
Jun 20 15:08:16 DrTungsLinux gnome-session[4599]: gnome-session-is-accelerated: No hardware 3D support.
Jun 20 15:08:16 DrTungsLinux gnome-session[4599]: Xlib:  extension "GLX" missing on display ":0".
Jun 20 15:08:16 DrTungsLinux gnome-session[4599]: gnome-session-check-accelerated: Helper exited with code 256
Jun 20 15:08:16 DrTungsLinux gnome-session[4599]: gnome-session-binary[4599]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Jun 20 15:08:16 DrTungsLinux gnome-session-binary[4599]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Jun 20 15:08:16 DrTungsLinux lightdm[1031]: ** (lightdm:1031): CRITICAL **: session_get_login1_session_id: assertion 'session != NULL' failed
Jun 20 15:08:16 DrTungsLinux systemd[1]: Stopping User Manager for UID 1001...

```When I select "Ubuntu Advanced Options" in GRUB and then choose 4.4.0-79 everything works fine, I can login to my desktop. Is this some known problem with 4.4.0-81?

---

