---
title: "banshee, trouble after pc got too hot while updating mediathek"
date: 2016-08-09
forum: MINT
---

### Post by prettynew2 on 2016-08-09
hello there. first of all, im using linux mint, but as its basically the same i thought maybe i'd get helpt sooner here.  what i did: i fed my old media folder into a completely new banshee, and let it copy all the files into a new mediathek folder. then my laptop got too hot, cause it was closed and i was watching a video and summer... (i know, really stupid) and shut down without a warning in a microsecond. after rebooting, i checked if the two folders where the same size, they werent so i deleted the new mediathek folder. then i started banshee, but it only got me an error message (see below). reinstalling didnt help, deinstalling, rebooting, then then reinstalling didnt help either.  heres the error message i get at the beginning, when i close it, the backgrounded banshee window closes too:    ```
 Eine nicht behandelte Ausnahme ist ausgelöst worden: Sqlite error 11: database disk image is malformed (SQL: SELECT COUNT(*), SUM(CoreTracks.FileSize), SUM(CoreTracks.Duration) FROM CoreTracks CROSS JOIN CoreArtists,CoreAlbums WHERE CoreArtists.ArtistID = CoreTracks.ArtistID AND CoreAlbums.AlbumID = CoreTracks.AlbumID  AND CoreTracks.PrimarySourceID = 1 )    at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in :0    at Hyena.Data.Sqlite.Statement.CheckError (Int32 code) [0x00000] in :0    at Hyena.Data.Sqlite.QueryReader.Read () [0x00000] in :0    at Hyena.Data.Sqlite.ArrayDataReader..ctor (IDataReader reader, System.String sql) [0x00000] in :0    at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in :0  Exception has been thrown by the target of an invocation.    at System.Reflection.MonoCMethod.InternalInvoke (System.Object obj, System.Object[] parameters) [0x00000] in :0    at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in :0    at System.Activator.CreateInstance (System.Type type) [0x00000] in :0    at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in :0    at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in :0   .NET Version: 4.0.30319.17020 OS Version: Unix 4.4.0.34  Assembly Version Information:  mscorlib (4.0.0.0) Banshee (2.6.0.0) Banshee.Services (2.6.0.0) System (4.0.0.0) glib-sharp (2.12.0.0) dbus-sharp (1.0.0.0) Hyena (2.6.0.0) dbus-sharp-glib (1.0.0.0) System.Core (4.0.0.0) DBus.Proxies (0.0.0.0) Nereid (2.6.0.0) Banshee.ThickClient (2.6.0.0) Hyena.Gui (2.6.0.0) gtk-sharp (2.12.0.0) Mono.Posix (4.0.0.0) atk-sharp (2.12.0.0) Mono.Addins (1.0.0.0) gdk-sharp (2.12.0.0) Hyena.Data.Sqlite (2.6.0.0) Banshee.Core (2.6.0.0) System.Xml (4.0.0.0) Mono.Security (4.0.0.0) Banshee.NowPlaying (2.6.0.0) Banshee.Gnome (2.6.0.0) gconf-sharp (2.24.0.0) System.Configuration (4.0.0.0) Banshee.GStreamer (2.6.0.0) Banshee.Gio (2.6.0.0) gudev-sharp (1.0.0.0) gio-sharp (2.14.0.0) Banshee.Widgets (2.6.0.0) Banshee.Fixup (2.6.0.0) Mono.Cairo (4.0.0.0) pango-sharp (2.12.0.0) Banshee.Lastfm (2.6.0.0) Banshee.Wikipedia (2.6.0.0) Banshee.WebBrowser (2.6.0.0) Banshee.CoverArt (2.6.0.0) Lastfm (2.6.0.0) Banshee.Dap (2.6.0.0) Banshee.MultimediaKeys (2.6.0.0) Banshee.Bpm (2.6.0.0) Banshee.Podcasting (2.6.0.0) Migo (2.6.0.0) Banshee.OpticalDisc (2.6.0.0) Banshee.Mpris (2.6.0.0) Banshee.NotificationArea (2.6.0.0) notify-sharp (0.4.0.0) Banshee.Daap (2.6.0.0)  Platform Information: Linux 4.4.0-34-generic x86_64 x86_64 GNU/Linux  Disribution Information:  [/etc/lsb-release] DISTRIB_ID=LinuxMint DISTRIB_RELEASE=17.3 DISTRIB_CODENAME=rosa DISTRIB_DESCRIPTION="Linux Mint 17.3 Rosa"  [/etc/os-release] NAME="Ubuntu" VERSION="14.04.3 LTS, Trusty Tahr" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.3 LTS" VERSION_ID="14.04" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"  [/etc/debian_version] jessie/sid 
```  ps: i dont know why it doesnt use new lines, tell me how and ill fix it

---

### Post by howefield on 2016-08-09
Thread moved to the "*MINT*" sub forum.

---

### Post by prettynew2 on 2016-08-09
should somebody ever have the same problem, the last point in [this FAQ-website]("http://banshee.fm/support/faq/") did it for me.

greetings.

---

