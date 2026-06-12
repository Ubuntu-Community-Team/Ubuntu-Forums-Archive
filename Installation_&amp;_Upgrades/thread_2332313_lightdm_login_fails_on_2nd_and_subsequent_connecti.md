---
title: "lightdm login fails on 2nd and subsequent connection"
date: 2016-07-30
forum: Installation &amp; Upgrades
---

### Post by David_Partridge on 2016-07-30
After upgrade to 16.04.1 from 14.04 I'm getting problems with lightdm.

Here's what I see in syslog after a first (successful) login

```

Jul 30 10:51:36 Charon lightdm[4444]: (lightdm:4444): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Jul 30 10:51:36 Charon systemd[1]: Started Session c2 of user lightdm.
Jul 30 10:51:36 Charon lightdm[4444]: (lightdm:4444): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Jul 30 10:51:36 Charon systemd[1]: Started Session c2 of user lightdm.
Jul 30 10:51:36 Charon lightdm[4444]: ** (lightdm:4444): WARNING **: Error activating login1 session: GDBus.Error:org.freedesktop.DBus.Error.NotSupported: Operation not supported
Jul 30 10:51:36 Charon org.a11y.atspi.Registry[8379]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jul 30 10:51:37 Charon systemd[1]: Started Run anacron jobs.
Jul 30 10:51:37 Charon anacron[8502]: Anacron 2.3 started on 2016-07-30
Jul 30 10:51:37 Charon anacron[8502]: Will run job `cron.daily' in 5 min.
Jul 30 10:51:37 Charon anacron[8502]: Will run job `cron.monthly' in 15 min.
Jul 30 10:51:37 Charon anacron[8502]: Jobs will be executed sequentially
Jul 30 10:51:42 Charon org.gtk.vfs.Daemon[8370]: A connection to the bus can't be made
Jul 30 10:51:42 Charon systemd[1]: Created slice User Slice of amonra.
Jul 30 10:51:42 Charon systemd[1]: Started Session c3 of user amonra.
Jul 30 10:51:42 Charon systemd[1]: Starting User Manager for UID 1000...
Jul 30 10:51:42 Charon systemd[8649]: Reached target Paths.
Jul 30 10:51:42 Charon systemd[8649]: Reached target Sockets.
Jul 30 10:51:42 Charon systemd[8649]: Reached target Timers.
Jul 30 10:51:42 Charon systemd[8649]: Reached target Basic System.
Jul 30 10:51:42 Charon systemd[8649]: Reached target Default.
Jul 30 10:51:42 Charon systemd[8649]: Startup finished in 85ms.
Jul 30 10:51:42 Charon systemd[1]: Started User Manager for UID 1000.
Jul 30 10:51:42 Charon lightdm[4444]: ** (lightdm:4444): WARNING **: Error activating login1 session: GDBus.Error:org.freedesktop.DBus.Error.NotSupported: Operation not supported
Jul 30 10:51:43 Charon org.a11y.Bus[8721]: Activating service name='org.a11y.atspi.Registry'
Jul 30 10:51:43 Charon org.a11y.Bus[8721]: ** (process:8819): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```

If I logout and then attempt to reconnect, I get the greeter login prompt and when I press enter to login, the X session closes, and this is what I see in syslog

```

Jul 30 10:57:10 Charon anacron[8502]: Job `cron.daily' terminated
Jul 30 11:00:25 Charon systemd[1]: Started CUPS Scheduler.
Jul 30 11:02:01 Charon systemd[1]: Starting Cleanup of Temporary Directories...
Jul 30 11:02:01 Charon systemd-tmpfiles[16744]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Jul 30 11:02:01 Charon systemd[1]: Started Cleanup of Temporary Directories.
Jul 30 11:03:32 Charon systemd[1]: Stopping Run anacron jobs...
Jul 30 11:03:32 Charon systemd[1]: Stopped Run anacron jobs.
Jul 30 11:04:05 Charon lightdm[4444]: (lightdm:4444): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Jul 30 11:04:05 Charon systemd[1]: Started Session c4 of user lightdm.
Jul 30 11:04:05 Charon lightdm[4444]: ** (lightdm:4444): WARNING **: Error activating login1 session: GDBus.Error:org.freedesktop.DBus.Error.NotSupported: Operation not supported
Jul 30 11:04:06 Charon systemd[1]: Started Run anacron jobs.
Jul 30 11:04:06 Charon anacron[18619]: Anacron 2.3 started on 2016-07-30
Jul 30 11:04:06 Charon anacron[18619]: Will run job `cron.monthly' in 15 min.
Jul 30 11:04:06 Charon anacron[18619]: Jobs will be executed sequentially
Jul 30 11:04:12 Charon systemd[1]: Started Session c5 of user amonra.
Jul 30 11:04:12 Charon lightdm[4444]: ** (lightdm:4444): WARNING **: Error activating login1 session: GDBus.Error:org.freedesktop.DBus.Error.NotSupported: Operation not supported
Jul 30 11:04:44 Charon systemd[1]: Stopping Run anacron jobs...
Jul 30 11:04:44 Charon systemd[1]: Stopped Run anacron jobs.
Jul 30 11:05:28 Charon systemd[1]: Started Run anacron jobs.
Jul 30 11:05:28 Charon anacron[19872]: Anacron 2.3 started on 2016-07-30
Jul 30 11:05:28 Charon anacron[19872]: Will run job `cron.monthly' in 15 min.
Jul 30 11:05:28 Charon anacron[19872]: Jobs will be executed sequentially
Jul 30 11:06:15 Charon systemd[1]: Started Session 1 of user amonra.
Jul 30 11:09:01 Charon CRON[22656]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))

```

I realise that's not much to go on, but the only thing I spot is the second log doesn't show the message:

Started User Manager for UID 1000.

looking in the /var/log/lightdm, I see

File: /var/log/lightdm/seat0-greeter.log
```
* Message: Starting lightdm-gtk-greeter 2.0.1 (Apr 11 2016, 06:05:31)
** Message: [Configuration] Reading file: /usr/share/lightdm/lightdm-gtk-greeter.conf.d/01_ubuntu.conf
** Message: [Configuration] Reading file: /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf

** (process:4451): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Activating service name='org.a11y.atspi.Registry'
Successfully activated service 'org.a11y.atspi.Registry'
upstart: indicator-application main process (4499) killed by TERM signal
upstart: indicator-application main process ended, respawning
upstart: indicator-application main process (28768) killed by TERM signal
upstart: indicator-application pre-stop process (28799) killed by HUP signal
** Message: Starting lightdm-gtk-greeter 2.0.1 (Apr 11 2016, 06:05:31)
** Message: [Configuration] Reading file: /usr/share/lightdm/lightdm-gtk-greeter.conf.d/01_ubuntu.conf
** Message: [Configuration] Reading file: /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf

** (process:4301): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Activating service name='org.a11y.atspi.Registry'
Successfully activated service 'org.a11y.atspi.Registry'
upstart: indicator-application main process (4350) killed by TERM signal
** Message: Starting lightdm-gtk-greeter 2.0.1 (Apr 11 2016, 06:05:31)
** Message: [Configuration] Reading file: /usr/share/lightdm/lightdm-gtk-greeter.conf.d/01_ubuntu.conf
** Message: [Configuration] Reading file: /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf

** (process:4619): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Activating service name='org.a11y.atspi.Registry'
Successfully activated service 'org.a11y.atspi.Registry'
```

File: /var/log/lightdm/(null)-greeter.log
```
** Message: Starting lightdm-gtk-greeter 2.0.1 (Apr 11 2016, 06:05:31)
** Message: [Configuration] Reading file: /usr/share/lightdm/lightdm-gtk-greeter.conf.d/01_ubuntu.conf
** Message: [Configuration] Reading file: /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf

** (process:4913): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
Activating service name='org.a11y.atspi.Registry'
Successfully activated service 'org.a11y.atspi.Registry'
upstart: indicator-application main process (4953) killed by TERM signal
** Message: Starting lightdm-gtk-greeter 2.0.1 (Apr 11 2016, 06:05:31)
** Message: [Configuration] Reading file: /usr/share/lightdm/lightdm-gtk-greeter.conf.d/01_ubuntu.conf
** Message: [Configuration] Reading file: /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf
Failed to launch bus: Failed to connect to session buslibGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
upstart: indicator-application main process ended, respawning
upstart: indicator-application main process ended, respawning
upstart: indicator-application respawning too fast, stopped
/usr/lib/lightdm/lightdm-greeter-session: 23: kill: No such process


** (lightdm-gtk-greeter:26282): WARNING **: [PIDs] Failed to terminate process #26284: No such process
** Message: Starting lightdm-gtk-greeter 2.0.1 (Apr 11 2016, 06:05:31)
** Message: [Configuration] Reading file: /usr/share/lightdm/lightdm-gtk-greeter.conf.d/01_ubuntu.conf
** Message: [Configuration] Reading file: /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf
Failed to launch bus: Failed to connect to session buslibGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
upstart: indicator-application main process ended, respawning
upstart: indicator-application main process ended, respawning
upstart: indicator-application respawning too fast, stopped

(lightdm-gtk-greeter:26464): Gdk-WARNING **: lightdm-gtk-greeter: Fatal IO error 11 (Resource temporarily unavailable) on X server 192.168.129.64:0.

/usr/lib/lightdm/lightdm-greeter-session: 23: kill: No such process

** Message: Starting lightdm-gtk-greeter 2.0.1 (Apr 11 2016, 06:05:31)
** Message: [Configuration] Reading file: /usr/share/lightdm/lightdm-gtk-greeter.conf.d/01_ubuntu.conf
** Message: [Configuration] Reading file: /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf
Failed to launch bus: Failed to connect to session buslibGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
upstart: indicator-application main process ended, respawning
upstart: indicator-application main process ended, respawning
upstart: indicator-application respawning too fast, stopped
/usr/lib/lightdm/lightdm-greeter-session: 23: kill: No such process


** (lightdm-gtk-greeter:26763): WARNING **: [PIDs] Failed to terminate process #26777: No such process
** Message: Starting lightdm-gtk-greeter 2.0.1 (Apr 11 2016, 06:05:31)
** Message: [Configuration] Reading file: /usr/share/lightdm/lightdm-gtk-greeter.conf.d/01_ubuntu.conf
** Message: [Configuration] Reading file: /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf
Failed to launch bus: Failed to connect to session buslibGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
upstart: indicator-application main process ended, respawning
upstart: indicator-application main process ended, respawning
upstart: indicator-application respawning too fast, stopped
/usr/lib/lightdm/lightdm-greeter-session: 23: kill: No such process


** (lightdm-gtk-greeter:27283): WARNING **: [PIDs] Failed to terminate process #27285: No such process
** Message: Starting lightdm-gtk-greeter 2.0.1 (Apr 11 2016, 06:05:31)
** Message: [Configuration] Reading file: /usr/share/lightdm/lightdm-gtk-greeter.conf.d/01_ubuntu.conf
** Message: [Configuration] Reading file: /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf
Failed to launch bus: Failed to connect to session buslibGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
upstart: indicator-application main process ended, respawning
upstart: indicator-application main process ended, respawning
upstart: indicator-application respawning too fast, stopped

(lightdm-gtk-greeter:28006): Gdk-WARNING **: lightdm-gtk-greeter: Fatal IO error 11 (Resource temporarily unavailable) on X server 192.168.129.64:0.

/usr/lib/lightdm/lightdm-greeter-session: 23: kill: No such process

** Message: Starting lightdm-gtk-greeter 2.0.1 (Apr 11 2016, 06:05:31)
** Message: [Configuration] Reading file: /usr/share/lightdm/lightdm-gtk-greeter.conf.d/01_ubuntu.conf
** Message: [Configuration] Reading file: /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf

** (process:4639): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
Activating service name='org.a11y.atspi.Registry'
Successfully activated service 'org.a11y.atspi.Registry'
upstart: indicator-application main process (4667) killed by TERM signal
** Message: Starting lightdm-gtk-greeter 2.0.1 (Apr 11 2016, 06:05:31)
** Message: [Configuration] Reading file: /usr/share/lightdm/lightdm-gtk-greeter.conf.d/01_ubuntu.conf
** Message: [Configuration] Reading file: /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf
Failed to launch bus: Failed to connect to session buslibGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
upstart: indicator-application main process ended, respawning
upstart: indicator-application main process ended, respawning
upstart: indicator-application respawning too fast, stopped
/usr/lib/lightdm/lightdm-greeter-session: 23: kill: No such process


** (lightdm-gtk-greeter:11549): WARNING **: [PIDs] Failed to terminate process #11551: No such process
** Message: Starting lightdm-gtk-greeter 2.0.1 (Apr 11 2016, 06:05:31)
** Message: [Configuration] Reading file: /usr/share/lightdm/lightdm-gtk-greeter.conf.d/01_ubuntu.conf
** Message: [Configuration] Reading file: /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf

** (process:8373): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
Activating service name='org.a11y.atspi.Registry'
Successfully activated service 'org.a11y.atspi.Registry'
upstart: indicator-application main process (8404) terminated with status 1
upstart: indicator-application main process ended, respawning

** (lightdm-gtk-greeter:8371): WARNING **: [PIDs] Failed to terminate process #8373: No such process
upstart: indicator-application main process (8644) killed by TERM signal
** Message: Starting lightdm-gtk-greeter 2.0.1 (Apr 11 2016, 06:05:31)
** Message: [Configuration] Reading file: /usr/share/lightdm/lightdm-gtk-greeter.conf.d/01_ubuntu.conf
** Message: [Configuration] Reading file: /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf
Failed to launch bus: Failed to connect to session buslibGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
upstart: indicator-application main process ended, respawning
upstart: indicator-application main process ended, respawning
upstart: indicator-application respawning too fast, stopped
/usr/lib/lightdm/lightdm-greeter-session: 23: kill: No such process


** (lightdm-gtk-greeter:18500): WARNING **: [PIDs] Failed to terminate process #18502: No such process

```

File: /var/log/lightdm/lightdm.log
```

[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.18.2, UID=0 PID=4444
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/20-lubuntu.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/20-lubuntu.conf
[+0.00s] DEBUG:   [SeatDefaults] is now called [Seat:*], please update this configuration
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG:   [SeatDefaults] is now called [Seat:*], please update this configuration
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.01s] DEBUG: Registered seat module xremote
[+0.01s] DEBUG: Registered seat module unity
[+0.04s] DEBUG: Monitoring logind for seats
[+0.04s] DEBUG: New seat added from logind: seat0
[+0.04s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.04s] DEBUG: Seat seat0: Starting
[+0.04s] DEBUG: Seat seat0: Creating greeter session
[+0.04s] DEBUG: Seat seat0: Creating display server of type x
[+0.06s] DEBUG: Using VT 7
[+0.06s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.06s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.06s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.17s] DEBUG: DisplayServer x-0: Launching X Server
[+0.17s] DEBUG: Launching process 4463: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -listen tcp vt7 -novtswitch
[+0.17s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.17s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.18s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.18s] DEBUG: Starting XDMCP server on UDP/IP port 177
[+0.20s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.20s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+1.82s] DEBUG: Got signal 10 from process 4463
[+1.82s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+1.82s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+1.84s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+1.84s] DEBUG: Session pid=4565: Started with service 'lightdm-greeter', username 'lightdm'
[+1.99s] DEBUG: Session pid=4565: Authentication complete with return value 0: Success
[+1.99s] DEBUG: Seat seat0: Session authenticated, running command
[+1.99s] DEBUG: Session pid=4565: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+1.99s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+1.99s] DEBUG: Session pid=4565: Logging to /var/log/lightdm/seat0-greeter.log
[+2.52s] DEBUG: Activating VT 7
[+2.52s] DEBUG: Activating login1 session c1
[+2.55s] DEBUG: Seat seat0 changes active session to c1
[+2.55s] DEBUG: Session c1 is already active
[+4.00s] DEBUG: Greeter connected version=1.18.2 resettable=false
[+5.97s] DEBUG: Greeter start authentication for amonra
[+5.97s] DEBUG: Session pid=4720: Started with service 'lightdm', username 'amonra'
[+6.04s] DEBUG: Session pid=4720: Got 1 message(s) from PAM
[+6.04s] DEBUG: Prompt greeter with 1 message(s)
[+238.45s] DEBUG: Got Query(authentication_names=[]) from 192.168.129.64:61250
[+238.45s] DEBUG: Send Willing(authentication_name='' hostname='Charon' status='') to 192.168.129.64:61250
[+238.82s] DEBUG: Got Request(display_number=0 connections=[192.168.129.64] authentication_name='' authentication_data= authorization_names=['MIT-MAGIC-COOKIE-1' 'XDM-AUTHORIZATION-1'] manufacturer_display_id='') from 192.168.129.64:61250
[+238.82s] CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
[+238.82s] DEBUG: Send Accept(session_id=6899 authentication_name='' authentication_data= authorization_name='MIT-MAGIC-COOKIE-1' authorization_data=F1E5579274A9CF3D1E6A91CD55EA7E12) to 192.168.129.64:61250
[+238.82s] DEBUG: Got Manage(session_id=6899 display_number=0 display_class='MIT-unspecified') from 192.168.129.64:61250
[+238.82s] DEBUG: Seat (null): Loading properties from config section Seat:*
[+238.82s] DEBUG: Seat (null): Starting
[+238.82s] DEBUG: Seat (null): Creating greeter session
[+238.82s] DEBUG: Seat (null): Creating display server of type x
[+238.82s] DEBUG: DisplayServer x-192.168.129.64-0: Connecting to XServer 192.168.129.64:0
[+238.83s] DEBUG: Seat (null): Display server ready, starting session authentication
[+238.83s] DEBUG: Session: Not setting XDG_VTNR
[+238.83s] DEBUG: Session pid=8362: Started with service 'lightdm-greeter', username 'lightdm'
[+238.84s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat1
[+238.87s] DEBUG: Session pid=8362: Authentication complete with return value 0: Success
[+238.87s] DEBUG: Seat (null): Session authenticated, running command
[+238.87s] DEBUG: Session pid=8362: Not setting XDG_VTNR
[+238.87s] DEBUG: Session pid=8362: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+238.87s] DEBUG: Session pid=8362: Logging to /var/log/lightdm/(null)-greeter.log
[+238.90s] DEBUG: Activating login1 session c2
[+238.91s] WARNING: Error activating login1 session: GDBus.Error:org.freedesktop.DBus.Error.NotSupported: Operation not supported
[+239.61s] DEBUG: Greeter connected version=1.18.2 resettable=false
[+240.41s] DEBUG: Greeter start authentication for amonra
[+240.41s] DEBUG: Session: Not setting XDG_VTNR
[+240.41s] DEBUG: Session pid=8562: Started with service 'lightdm', username 'amonra'
[+240.44s] DEBUG: Session pid=8562: Got 1 message(s) from PAM
[+240.44s] DEBUG: Prompt greeter with 1 message(s)
[+244.44s] DEBUG: Continue authentication
[+244.48s] DEBUG: Session pid=8562: Authentication complete with return value 0: Success
[+244.48s] DEBUG: Authenticate result for user amonra: Success
[+244.48s] DEBUG: User amonra authorized
[+244.50s] DEBUG: Greeter sets language en_GB
[+244.80s] DEBUG: Greeter requests session Lubuntu
[+244.80s] DEBUG: Seat (null): Stopping greeter; display server will be re-used for user session
[+244.80s] DEBUG: Session pid=8362: Sending SIGTERM
[+244.83s] DEBUG: Session pid=8362: Exited with return value 0
[+244.83s] DEBUG: Seat (null): Session stopped
[+244.83s] DEBUG: Seat (null): Greeter stopped, running session
[+244.83s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+244.85s] DEBUG: Session pid=8562: Not setting XDG_VTNR
[+244.86s] DEBUG: Session pid=8562: Running command /usr/sbin/lightdm-session /usr/bin/lxsession -s Lubuntu -e LXDE
[+244.86s] DEBUG: Session pid=8562: Logging to .xsession-errors
[+245.05s] DEBUG: Activating login1 session c3
[+245.05s] WARNING: Error activating login1 session: GDBus.Error:org.freedesktop.DBus.Error.NotSupported: Operation not supported
[+923.66s] DEBUG: Session pid=8562: Exited with return value 0
[+923.66s] DEBUG: Seat (null): Session stopped
[+923.66s] DEBUG: Seat (null): Stopping display server, no sessions require it
[+923.66s] DEBUG: Seat (null): Display server stopped
[+923.66s] DEBUG: Seat (null): Active display server stopped, starting greeter
[+923.66s] DEBUG: Seat (null): Stopping; failed to start a greeter
[+923.66s] DEBUG: Seat (null): Stopping
[+923.66s] DEBUG: Seat (null): Stopped
[+987.94s] DEBUG: Got Query(authentication_names=[]) from 192.168.129.64:64466
[+987.94s] DEBUG: Send Willing(authentication_name='' hostname='Charon' status='') to 192.168.129.64:64466
[+988.16s] DEBUG: Got Request(display_number=0 connections=[192.168.129.64] authentication_name='' authentication_data= authorization_names=['MIT-MAGIC-COOKIE-1' 'XDM-AUTHORIZATION-1'] manufacturer_display_id='') from 192.168.129.64:64466
[+988.16s] CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
[+988.16s] DEBUG: Send Accept(session_id=24477 authentication_name='' authentication_data= authorization_name='MIT-MAGIC-COOKIE-1' authorization_data=3781F5E0763ABC87842DCC5C69507DB0) to 192.168.129.64:64466
[+988.16s] DEBUG: Got Manage(session_id=24477 display_number=0 display_class='MIT-unspecified') from 192.168.129.64:64466
[+988.16s] DEBUG: Seat (null): Loading properties from config section Seat:*
[+988.16s] DEBUG: Seat (null): Starting
[+988.16s] DEBUG: Seat (null): Creating greeter session
[+988.16s] DEBUG: Seat (null): Creating display server of type x
[+988.16s] DEBUG: DisplayServer x-192.168.129.64-0: Connecting to XServer 192.168.129.64:0
[+988.17s] DEBUG: Seat (null): Display server ready, starting session authentication
[+988.17s] DEBUG: Session: Not setting XDG_VTNR
[+988.17s] DEBUG: Session pid=18491: Started with service 'lightdm-greeter', username 'lightdm'
[+988.17s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat2
[+988.21s] DEBUG: Session pid=18491: Authentication complete with return value 0: Success
[+988.21s] DEBUG: Seat (null): Session authenticated, running command
[+988.21s] DEBUG: Session pid=18491: Not setting XDG_VTNR
[+988.21s] DEBUG: Session pid=18491: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+988.21s] DEBUG: Session pid=18491: Logging to /var/log/lightdm/(null)-greeter.log
[+988.24s] DEBUG: Activating login1 session c4
[+988.24s] WARNING: Error activating login1 session: GDBus.Error:org.freedesktop.DBus.Error.NotSupported: Operation not supported
[+988.66s] DEBUG: Greeter connected version=1.18.2 resettable=false
[+989.49s] DEBUG: Greeter start authentication for amonra
[+989.49s] DEBUG: Session: Not setting XDG_VTNR
[+989.49s] DEBUG: Session pid=18680: Started with service 'lightdm', username 'amonra'
[+989.51s] DEBUG: Session pid=18680: Got 1 message(s) from PAM
[+989.51s] DEBUG: Prompt greeter with 1 message(s)
[+994.85s] DEBUG: Continue authentication
[+994.92s] DEBUG: Session pid=18680: Authentication complete with return value 0: Success
[+994.92s] DEBUG: Authenticate result for user amonra: Success
[+994.92s] DEBUG: User amonra authorized
[+994.93s] DEBUG: Greeter sets language en_GB
[+995.23s] DEBUG: Greeter requests session Lubuntu
[+995.23s] DEBUG: Seat (null): Stopping greeter; display server will be re-used for user session
[+995.23s] DEBUG: Session pid=18491: Sending SIGTERM
[+995.24s] DEBUG: Greeter closed communication channel
[+995.25s] DEBUG: Session pid=18491: Exited with return value 0
[+995.25s] DEBUG: Seat (null): Session stopped
[+995.25s] DEBUG: Seat (null): Greeter stopped, running session
[+995.25s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session1
[+995.26s] DEBUG: Session pid=18680: Not setting XDG_VTNR
[+995.26s] DEBUG: Session pid=18680: Running command /usr/sbin/lightdm-session /usr/bin/lxsession -s Lubuntu -e LXDE
[+995.26s] DEBUG: Session pid=18680: Logging to .xsession-errors
[+995.29s] DEBUG: Activating login1 session c5
[+995.30s] WARNING: Error activating login1 session: GDBus.Error:org.freedesktop.DBus.Error.NotSupported: Operation not supported
[+1505.74s] DEBUG: Session pid=18680: Exited with return value 0
[+1505.74s] DEBUG: Seat (null): Session stopped
[+1505.74s] DEBUG: Seat (null): Stopping display server, no sessions require it
[+1505.74s] DEBUG: Seat (null): Display server stopped
[+1505.74s] DEBUG: Seat (null): Active display server stopped, starting greeter
[+1505.74s] DEBUG: Seat (null): Stopping; failed to start a greeter
[+1505.74s] DEBUG: Seat (null): Stopping
[+1505.74s] DEBUG: Seat (null): Stopped

```

Thanks
Dave

---

### Post by leo4321 on 2016-08-01
I am seeing the same problem. I installed
ubuntu-gnome-16.04.1-desktop-amd64.iso
on an Intel NUC6i5SYH with
Intel® Core™ i5-6260U CPU @ 1.80GHz × 4 and
Intel® Iris Graphics 540 (Skylake GT3e).
I then installed lightdm and xfce4 with the
Synaptic Package Manager. Local logins work fine with
GDM, LighttDM, GNOME and Xfce.

However, remote XDMCP login from a VcXsrv X server running
on a Windows 10 computer works only once for each boot up
of the ubuntu system. On the second and subsequent remote
login attempts, after entering the password and proceeding,
the screen flicker twice and returns to the login screen.

The syslog for the failing logins diverges from the good
login at:
Aug  1 18:44:44 nucunifi systemd[4395]:
    Startup finished in 24ms.
Aug  1 18:44:44 nucunifi systemd[1]:
    Started User Manager for UID 1000.
Aug  1 18:44:44 nucunifi lightdm[3177]:
    ** (lightdm:3177): WARNING **: Error activating login1 session:
    GDBus.Error:org.freedesktop.DBus.Error.NotSupported:
    Operation not supported
Aug  1 18:44:44 nucunifi lightdm[3177]:
    (lightdm:3177): GLib-GObject-CRITICAL **: g_object_unref:
    assertion 'G_IS_OBJECT (object)' failed
Aug  1 18:44:44 nucunifi systemd[1]:
    Started Session c6 of user lightdm.
Aug  1 18:44:44 nucunifi lightdm[3177]:
    ** (lightdm:3177): WARNING **: Error activating login1 session:
    GDBus.Error:org.freedesktop.DBus.Error.NotSupported:
    Operation not supported
Aug  1 18:44:46 nucunifi systemd[1]:
    Stopping User Manager for UID 1000...
Aug  1 18:44:46 nucunifi systemd[4395]:
    Reached target Shutdown.

Any ideas on how to get this to work?

---

### Post by David_Partridge on 2016-08-02
Good to see I'm not alone.  My failures are also when using XDMCP.

Hope that someone can resolve this.  If you can please also join the lightdm mailing list and report the problem there:

[https://lists.freedesktop.org/mailman/listinfo/lightdm](https://lists.freedesktop.org/mailman/listinfo/lightdm)

Cheers
Dave

---

### Post by David_Partridge on 2016-08-07
I spotted the bug report for lightdm: <[https://bugs.launchpad.net/lightdm/+bug/1599478](https://bugs.launchpad.net/lightdm/+bug/1599478)> which looks mightily like this problem.

I grabbed the following from the "yakkety" repository:

I plucked up my courage and installed:
 
libgcrypt20_1.7.2-2 and
lightdm_1.19.3-0ubuntu1
 
from the yakkety repository.
 
This seems to resolve the problem.

How do I add the yakkety repository for just these two packages on 16.04.1?  Or is that not possible?

---

### Post by leo4321 on 2016-08-10
I have verified the above solution. I spun up A VM using "ubuntu-gnome-16.04.1-desktop-amd64.iso" and installed the default lightdm 1.18.2 package. I was then able to do one and only one XDMCP login per boot up of the Ubuntu host. I then did "dpkg -i libgcrypt20_1.7.2-2_amd64.deb" (a prerequisite for the new lightdm) and "dpkg -i  lightdm_1.19.3-0ubuntu1_amd64.deb" to install lightdm version 1.19.3. Now I can do multiple XDMCP logins to multiple users without any trouble.

---

