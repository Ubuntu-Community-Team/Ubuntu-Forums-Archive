---
title: "Gnome daemon settings error"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Ihsahn on 2008-05-07
Apologies if this has already been posted.

Today I upgraded 7.10 to 8.04 and all is well apart from one thing and it seems rather curious.

On starting my computer Ubuntu runs fine. However, I log in and it takes bloody ages to log in. By that I mean about 5 minutes which is much longer than usual of course. When I can finally get going I get this message...

'There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.'

...After this everything works fine. After about 5 minutes however, Ubuntu makes the 'startup jingle' and my theme changes. However, Linux is working at normal speed. Nothing peculiar other than this seems to be occurring. How can I remedy this problem?

---

### Post by doood81 on 2008-05-07
I've had a similar issue with the gnome-settings-daemon as well.

I've been upgrading via editing /etc/apt/sources.list since dapper and have not had any real major issues, this one is quite annoying.

Upon login I'll get an error stating that the daemon can't be run. At the same time in /var/log/messages I can see segfaults from gnome-keyring. Eventually it lets my user login, and I run gnome-settings-daemon manually which produces the following output:

```
686:~$ gnome-settings-daemon &
[1] 9716
686:~$ ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192

```

A new user with no files in his/her home directory never makes it to the desktop upon login either. I'm left with a blank screen.

---

