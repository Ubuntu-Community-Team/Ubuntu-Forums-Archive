---
title: "File and folder permission problems"
date: 2009-01-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by darrenadams on 2009-01-04
Hello there,

Since upgrading to the Jackelope alphas, I've run into a few problems. The first involved NetworkManager (documented in LP [bug 307204](https://bugs.edge.launchpad.net/ubuntu/+source/dhcp3/+bug/307204), and duly corrected), but now I seem to have problems with various GNOME applications creating the wrong permissions on folders / directories. This seems similar to LP [bug 242618](https://bugs.launchpad.net/glib/+bug/242618) but Nautilus creates folder / directories without any problem.

I first noticed this when I was using Transmission to download a torrent. I kept getting "Permission denied" errors on my torrents, only to realise that this was because Transmission was creating directories but not applying the correct permissions to them, so that I ended up with permissions like this:

```

drw-rw----  2 darren darren    4096 2009-01-05 00:37 test-folder

```

Rather than this:

```

drwxr-xr-x  2 darren darren    4096 2009-01-05 00:37 test-folder

```

This shows up in other places too. For instance:

[LIST]
[*]If I save something in Epiphany (a PDF for example) then create a folder to save this PDF, the PDF is never saved because folder permissions are incorrect. Strangely Firefox doesn't seem affected by this problem.
[*]It's impossible to rip a CD using Rhythmbox if it needs to create a folder to save my ripped files into
[*]Transmission has trouble saving torrents if it needs to create a folder during the download process
[/LIST]

Before I go trawling through Launchpad some more tomorrow (and possibly file a bug), I'd like to know, has anybody else experienced this problem? It doesn't seem to have been mentioned in the forums so far...

Darren

---

