---
title: "Banshee crashing right after running"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Roberto_Lapuente on 2011-04-29
Hi, I have just upgraded to Ubuntu 11.04 and when I try to tun Banshee it just crashes as soon as the windows opens. Here is the log:
```
exec -a banshee mono  /usr/lib/banshee/Banshee.exe    --redirect-log --play-enqueued

[Info  10:42:33.842] Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, x86_64) @ 2011-04-18 16:18:52 UTC]
[Info  10:42:34.946] Updating web proxy from GConf
[Info  10:42:35.083] All services are started 1.046805
[Warn  10:42:35.442] Migrating Internet Radio Stations - System.IO.DirectoryNotFoundException: Directory '/home/roberto/.config/banshee/plugins/stations/user' not found. (in `mscorlib')
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String searchPattern, FileAttributes mask, FileAttributes attrs) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetFiles (System.String path, System.String searchPattern) [0x00000] in <filename unknown>:0 
  at Banshee.InternetRadio.XspfMigrator.Migrate () [0x00000] in <filename unknown>:0 
** (Banshee:24081): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:24081): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'
** (Banshee:24081): DEBUG: Loading the real store page
[Info  10:42:36.110] nereid Client Started
[Info  10:42:36.175] GStreamer version 0.10.32.0, gapless: True, replaygain: False

Unhandled Exception: GLib.GException: Can't recursively copy directory
  at GLib.FileAdapter.Move (File destination, FileCopyFlags flags, GLib.Cancellable cancellable, GLib.FileProgressCallback progress_callback) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Gio.Directory.Move (Hyena.SafeUri from, Hyena.SafeUri to) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Directory.Move (Hyena.SafeUri from, Hyena.SafeUri to) [0x00000] in <filename unknown>:0 
  at Banshee.Podcasting.PodcastService.<DelayedInitialize>m__11 () [0x00000] in <filename unknown>:0 
```

Somebody help?

---

