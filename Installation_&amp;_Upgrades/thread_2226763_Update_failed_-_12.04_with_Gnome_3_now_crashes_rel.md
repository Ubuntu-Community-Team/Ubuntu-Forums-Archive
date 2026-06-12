---
title: "Update failed - 12.04 with Gnome 3 now crashes reliably"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by dhlocker on 2014-05-28
Never had a problem with updates before; this one is killing me.

Symptoms:

Firefox (29.0 Mozilla Firefox for Ubuntu canonical - 1.0) crashes immediately upon startup. "This is embarassing" screen which then goes away and takes Gnome desktop with it. Firefox still has an active PID, but no graphical existence and gnome system monitor shows it using 0% processor and no memory. (I renamed ~/.mozilla/firefox to ~/.mozilla/firefox.NOT to run this instance which has crashed twice anyway.)

Gnome3 desktop has turned into something looking like the early Gnome desktop. until it goes away. I just started an xterm before things went down so I could start firefox.

Screen geometry is broken. The screen was 1400x900? (approximately;) is now 1280x768 or thereabouts with no other options.

This is the /var/log/history.log for the events leading to the problem (two lines). I am suspicious of the ringtail-related changes, as I expect to still be in precise.

Any help appreciated,
Donald.

=========================
Start-Date: 2014-05-27  22:08:04
Commandline: aptdaemon role='role-commit-packages' sender=':1.67'
Upgrade: libcupsppdc1:amd64 (1.5.3-0ubuntu8.2, 1.5.3-0ubuntu8.3), libcupsimage2:amd64 (1.5.3-0ubuntu8.2, 1.5.3-0ubuntu8.3), libcupscgi1:amd64 (1.5.3-0ubuntu8.2, 1.5.3-0ubuntu8.3), libcupsdriver1:amd64 (1.5.3-0ubuntu8.2, 1.5.3-0ubuntu8.3), cups-client:amd64 (1.5.3-0ubuntu8.2, 1.5.3-0ubuntu8.3), cups-ppdc:amd64 (1.5.3-0ubuntu8.2, 1.5.3-0ubuntu8.3), cups-common:amd64 (1.5.3-0ubuntu8.2, 1.5.3-0ubuntu8.3), libcups2:amd64 (1.5.3-0ubuntu8.2, 1.5.3-0ubuntu8.3), libcups2:i386 (1.5.3-0ubuntu8.2, 1.5.3-0ubuntu8.3), cups:amd64 (1.5.3-0ubuntu8.2, 1.5.3-0ubuntu8.3), cups-bsd:amd64 (1.5.3-0ubuntu8.2, 1.5.3-0ubuntu8.3), linux-libc-dev:amd64 (3.2.0-61.93, 3.2.0-63.95), libcupsmime1:amd64 (1.5.3-0ubuntu8.2, 1.5.3-0ubuntu8.3)
End-Date: 2014-05-27  22:09:16

Start-Date: 2014-05-27  22:16:23
Commandline: aptdaemon role='role-commit-packages' sender=':1.67'
Install: linux-headers-3.8.0-41:amd64 (3.8.0-41.60~precise1), linux-headers-3.8.0-41-generic:amd64 (3.8.0-41.60~precise1), linux-image-3.8.0-41-generic:amd64 (3.8.0-41.60~precise1)
Upgrade: linux-image-generic-lts-raring:amd64 (3.8.0.39.39, 3.8.0.41.41), linux-headers-generic-lts-raring:amd64 (3.8.0.39.39, 3.8.0.41.41), linux-generic-lts-raring:amd64 (3.8.0.39.39, 3.8.0.41.41)
End-Date: 2014-05-27  22:19:52

---

