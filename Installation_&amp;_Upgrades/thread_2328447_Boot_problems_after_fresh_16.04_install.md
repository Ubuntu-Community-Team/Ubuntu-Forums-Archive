---
title: "Boot problems after fresh 16.04 install"
date: 2016-06-21
forum: Installation &amp; Upgrades
---

### Post by hans12345 on 2016-06-21
I have recently done a fresh install of 16.04 after failing to update cleanly from 15.10.

I assume those problem were related to having an AMD CPU and graphics (HD 5400).

Now my PC crashes during boot up. Fglrx is not installed, so I am using the correct drivers. There are no broken packages.

Recovery mode / terminal works OK.

I have run memory and file checks, all seem good.

While booting, I have several screens that flash up very briefly after the grub menu, but it usually ends with a black screen or with a black screen with a single non-flashing dash in the top left corner.

On the 7th attempt, I managed to boot up today. This last time I did not speed up the grub menu step by hitting 'return' key. Can this be relevant?

I got errors "16.04 has experienced an internal error" but it seems to work fine.

Syslog:

Jun 19 11:59:06 Atlas rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="637" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jun 19 11:59:43 Atlas com.canonical.Unity.Scope.Applications[1100]: Error loading package indexes: Couldn't stat '/var/cache/software-center/xapian'
Jun 19 11:59:43 Atlas com.canonical.Unity.Scope.Applications[1100]: (unity-scope-loader:4175): unity-applications-daemon-CRITICAL **: daemon.vala:144: Failed to load Software Center index. 'Apps Available for Download' will not be listed
Jun 19 11:59:44 Atlas com.canonical.Unity.Scope.Applications[1100]: (unity-scope-loader:4175): libunity-WARNING **: unity-appinfo-manager.vala:160: Error loading '/usr/share/app-install/desktop/wesnoth-1.10-core:wesnoth-1.10.desktop': No such file or directory
Jun 19 12:01:25 Atlas anacron[658]: Job `cron.daily' terminated
Jun 19 12:01:25 Atlas anacron[658]: Normal exit (1 job run)
Jun 19 12:01:55 Atlas dbus[587]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jun 19 12:01:55 Atlas systemd[1]: Starting Hostname Service...
Jun 19 12:01:55 Atlas dbus[587]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jun 19 12:01:55 Atlas systemd[1]: Started Hostname Service.
Jun 19 12:01:57 Atlas org.gtk.vfs.Daemon[1100]: ** (process:4298): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
Jun 19 12:01:57 Atlas org.gtk.vfs.Daemon[1100]: ** (process:4294): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend


On pastebin, Xorg.0.log:
[http://pastebin.com/N5byKHYk](http://pastebin.com/N5byKHYk)

---

### Post by hans12345 on 2016-06-23
Bump

I need advice on whether I should look for:

- a HW problem,
- an installation problem,
- a conflict between my HW and 16.04.

Your help is appreciated.

---

### Post by hans12345 on 2016-08-06
The problem is erratic. Sometimes it 
- works OK, or
- crashes apparently in the early boot (typically the screen is black with a flashing '_' character in the top left corner), or
- boots with a message about 'internal error' and when I dig down I find:
 unity-settings-daemon crashed with SIGSEGV in up-expected-daemon-get-lid-is-closed()
(note: the '-' above may be '_')

Any ideas?

---

