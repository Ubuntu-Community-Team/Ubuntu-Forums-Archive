---
title: "Ubuntu 11.04 freezes when in dual screen"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by Luc484 on 2011-05-11
Hi! I've been using Ubuntu 11.04 for some time now and I'm experiencing many severe bugs. One of this is very bothering and I still can't find a solution.

I experienced many problems maybe related to this, but seems to have gone away by downgrading xserver-xorg-video-ati. Still anyway, when in dual screen, after some time, the screen completely freezes. The system is completely freezed, I can't even go to a shell, but I noticed it is possible to log in via ssh.

I've never had problems with ATI opensource drivers. Now I even noticed a logout problem anyway (which is known as far as I know).

Is there anyone else experiencing the same? I found some others complaining about something similar, but not exactly the same and still no solution.
Is it possible to somehow debug this when it happens?

I have to note that I'm still using kernel version 2.6.35 because the new 2.6.38 is not booting at all. But I don't know whether this is the problem or not.

Any advice is really appreciated! Thanks!

---

### Post by MAFoElffen on 2011-05-11
> **Luc484 said:**
> Hi! I've been using Ubuntu 11.04 for some time now and I'm experiencing many severe bugs. One of this is very bothering and I still can't find a solution.

I experienced many problems maybe related to this, but seems to have gone away by downgrading xserver-xorg-video-ati. Still anyway, when in dual screen, after some time, the screen completely freezes. The system is completely freezed, I can't even go to a shell, but I noticed it is possible to log in via ssh.

I've never had problems with ATI opensource drivers. Now I even noticed a logout problem anyway (which is known as far as I know).

Is there anyone else experiencing the same? I found some others complaining about something similar, but not exactly the same and still no solution.
Is it possible to somehow debug this when it happens?

I have to note that I'm still using kernel version 2.6.35 because the new 2.6.38 is not booting at all. But I don't know whether this is the problem or not.

Any advice is really appreciated! Thanks!Have you lokked at your .xessionerrors.log in your Home directory?

---

### Post by Luc484 on 2011-05-11
The system has suddenly just logged out right now. This is the content of .xsession-errors.old:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-PofJ1U
SSH_AUTH_SOCK=/tmp/keyring-PofJ1U/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-PofJ1U
SSH_AUTH_SOCK=/tmp/keyring-PofJ1U/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-PofJ1U
SSH_AUTH_SOCK=/tmp/keyring-PofJ1U/ssh
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
** Message: adding killswitch idx 0 state KILLSWITCH_STATE_UNBLOCKED
** Message: killswitch 0 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitches state KILLSWITCH_STATE_UNBLOCKED
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
** Message: killswitch 0 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitches state KILLSWITCH_STATE_UNBLOCKED
Initializing fade options...done
Initializing scale options...done
I/O warning : failed to load external entity "/home/luca/.compiz/session/1056e945b2be5b89d6130515011059583700000016890034"
Initializing session options...done
Starting unity-window-decorator

(unity-window-decorator:1834): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:1834): Gdk-CRITICAL **: IA__gdk_window_set_events: assertion `GDK_IS_WINDOW (window)' failed
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
** (nm-applet:1779): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1779): DEBUG: foo_client_state_changed_cb
Initializing nautilus-gdu extension

** (gnome-screensaver:1974): WARNING **: screensaver already running in this session
** (nm-applet:1779): DEBUG: foo_client_state_changed_cb
** (process:1787): DEBUG: zeitgeist-datahub.vala:174: Inserting 73 events
sys:1: Warning: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (process:1787): DEBUG: zeitgeist-datahub.vala:174: Inserting 3 events
** (process:1787): DEBUG: zeitgeist-datahub.vala:174: Inserting 3 events
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"

      after 19167 requests (19167 known processed) with 5 events remaining.

nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
gnome-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"

      after 11 requests (11 known processed) with 0 events remaining.

unity-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
checkerservice.pyc: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
gnome-terminal: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
firefox-bin: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.

** (process:1787): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
** (process:1787): DEBUG: zeitgeist-datahub.vala:58: Zeitgeist-daemon disappeared from the bus, exitting...
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
```

I suppose that is the correct one, reporting errors from the last login. Right?
I will look at this the next time I get the freeze. Does this mean anything to you? Seems quite frequent around.
Thanks for your help!

---

### Post by gsoundsgood on 2011-08-03
I've got the same problem... I'm trying the solution suggested here ([http://www.rajeshrana.net/2011/05/27/ubuntu-11-04-freezes-hangs-idle/](http://www.rajeshrana.net/2011/05/27/ubuntu-11-04-freezes-hangs-idle/)) for a similar problem, i.e. enabling just any screensaver, or uninstall gnome screensaver and install xscreensaver

---

### Post by Pattinson on 2011-08-03
Thanks for sharing!

---

