---
title: "Banshee"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by kaurie on 2011-05-03
I have just upgraded to Naty (11.04) Ubuntu 64 bit and was very surprised to see GNOME changed to UNITY Open Office to Libre Office. There seems to be very little documentation so it took an hour before I realised that 3D and 2D and Ubuntu were all confused - I had to read [http://en.wikipedia.org/wiki/Unity_%28desktop_environment%29](http://en.wikipedia.org/wiki/Unity_%28desktop_environment%29) 
OKAY after wasting a lot of time I found 
[http://unity.ubuntu.com/projects/unity/](http://unity.ubuntu.com/projects/unity/)

I hope that the UBUNTU maker read this and consider that in my (BIASED) view THIS TIME the documentation for such a major change was appalling. However I also hope that they realise that they have such a lot of good will (dating in my case back to Dapper Drake) that although they are blamed for this problem they are generally blessed and thanked in thought often {if not always by writing}
:mad::confused:\\:D/\\:D/:popcorn:


However I am now sorted on that so after the RANT onto the main problem

Banshee would not work after the upgrade - I do have Rhythmbox working

Typing sudo banshee

I get 
Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, x86_64) @ 2011-04-18 16:18:52 UTC]
[Warn  12:34:16.119] DBus support could not be started. Disabling for this session.
[Info  12:34:16.320] Migrating album-art cache directory
[Warn  12:34:16.323] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 1: no such table: CoverArtDownloads (SQL: DELETE FROM CoverArtDownloads) (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 
[Info  12:34:16.326] Migrated 0 files in 0.004165s
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml

ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstgnomevfs.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap --gst-disable-registry-fork and debug.


Any comments/ help  would be appreciated

Thanks

---

### Post by mörgæs on 2011-05-04
> **kaurie said:**
> 
Please either:
- remove it and restart.
- run with --gst-disable-segtrap --gst-disable-registry-fork and debug.


And sudo should not be necessary for this.

---

