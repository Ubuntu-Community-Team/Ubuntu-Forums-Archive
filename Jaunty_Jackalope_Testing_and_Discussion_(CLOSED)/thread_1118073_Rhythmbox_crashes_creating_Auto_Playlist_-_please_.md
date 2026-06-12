---
title: "Rhythmbox crashes creating Auto Playlist - please test?"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Xero Xenith on 2009-04-06
Anyone on 9.04 at the moment, please test this out.

[LIST=1]
[*]Start Rhythmbox
[*]Go to Music -> Playlist -> Automatic Playlist
[*]Select any terms, hit OK
[*]Post below with what happens; whether or not it crashes.
[/LIST]

For me, it crashes every time, but it never starts Apport. I tried filing a bug, [as did this guy]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/354928"), but they were both dismissed as "invalid" because no .crash file is supplied; this is because Apport doesn't start.

Any information would be appreciated.

---

### Post by nicedanmonkey on 2009-04-06
It crashes for me too.

---

### Post by lvlo on 2009-04-07
Same issue here:```
**
Rhythmbox:ERROR:rb-auto-playlist-source.c:745:rb_auto_playlist_source_do_query: assertion failed: (priv->cached_all_query)
Aborted

```

---

### Post by CrashTest71 on 2009-04-07
Looks like a fix has been identified for this bug.

[https://bugs.launchpad.net/bugs/354928]("https://bugs.launchpad.net/bugs/354928")
[quote=seb128]
the stacktrace is similar to
[http://bugzilla.gnome.org/show_bug.cgi?id=576846](http://bugzilla.gnome.org/show_bug.cgi?id=576846) which is fixed to svn

** Bug watch added: GNOME Bug Tracker #576846
   [http://bugzilla.gnome.org/show_bug.cgi?id=576846](http://bugzilla.gnome.org/show_bug.cgi?id=576846)

** Changed in: rhythmbox (Ubuntu)
       Status: Confirmed => Fix Committed
[/quote]

---

