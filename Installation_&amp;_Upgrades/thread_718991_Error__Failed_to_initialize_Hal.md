---
title: "Error : Failed to initialize Hal"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by didli on 2008-03-08
Hi you all !
 ... one problem down, another rise up :
I got this message at every startup. Here's a command that seems to point my problem (but I don't quite understand it yet), if you can help me with it ...
**sudo hald --daemon=no --verbose=yes**```
22:58:35.519 [i] hald.c:529: hal 0.5.9.1
22:58:35.519 [i] hald.c:594: Will not daemonize
22:58:35.520 [i] hald_dbus.c:4807: local server is listening at unix:abstract=/var/run/hald/dbus-BLSucaeB5v,guid=3b9a6152960ae02b41c77f0047d30c0b
Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
22:58:35.525 [i] hald_runner.c:299: Runner has pid 6543
22:58:35.525 [W] ci-tracker.c:200: Could not get uid for connection: org.freedesktop.DBus.Error.NameHasNoOwner Could not get UID of name 'org.freedesktop.DBus': no such name
22:58:35.525 [E] hald_dbus.c:4462: Cannot get caller info for org.freedesktop.DBus
22:58:35.525 [i] hald_runner.c:180: runner connection is 0x8094a18
22:58:35.526 [i] mmap_cache.c:251: cache mtime is 1205009659
22:58:35.527 [W] ids.c:294: Couldn't stat pci.ids file '/usr/share/misc/pci.ids', errno=13: Permission denied
22:58:35.527 [W] ids.c:515: Couldn't stat usb.ids file '/usr/share/misc/usb.ids', errno=13: Permission denied
22:58:35.527 [E] osspec.c:310: Unable to inotify_add_watch() for '/usr/share/hal/fdi/preprobe': Permission denied
*** [DIE] osspec.c:watch_fdi_files():389 : Error watching fdi files
```
Do you guys know something about that ? Thank you all in advance !

---

