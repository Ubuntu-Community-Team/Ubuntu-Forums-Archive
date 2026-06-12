---
title: "Ubuntu One, Tracker, etc."
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gunksta on 2010-04-09
Lucid comes with Ubuntu One (U1) installed / operating by default. I haven't used it much yet, but there it is. In addition to letting us sync/share files it also enables the sharing of notes, messaging and I suspect it will eventually do a Conduit like thing and allow us to sync more and more.

In contrast, Tracker indexes our files, making it easy as pie to search/find things. I've read the Gnome3 stuff and it looks like it will also do more to integrate work flow and messaging.

Tracker is not installed on Lucid by default, because of hal dependencies (I assume) and because it would slow down log-in/start-up of the desktop. But, Tracker does offer some utility.

I think the Ubuntu devs should consider merging the two. What if the U1 system could upload the files to the cloud, where they could be indexed and have the resulting index merged back down to the client.

This would increase the utility of U1 and give netbook users, etc. access to indexing, which is difficult to take full advantage of on a limited system and the rest of us don't have to run 10,000 daemons just to have a nifty desktop.

What do others think?

---

### Post by coutts99 on 2010-04-09
Bah, UbuntuOne always breaks for me, moved to DropBox instead

---

### Post by chrisccoulson on 2010-04-09
> **gunksta said:**
> Lucid comes with Ubuntu One (U1) installed / operating by default. I haven't used it much yet, but there it is. In addition to letting us sync/share files it also enables the sharing of notes, messaging and I suspect it will eventually do a Conduit like thing and allow us to sync more and more.

In contrast, Tracker indexes our files, making it easy as pie to search/find things. I've read the Gnome3 stuff and it looks like it will also do more to integrate work flow and messaging.

Tracker is not installed on Lucid by default, because of hal dependencies (I assume) and because it would slow down log-in/start-up of the desktop. But, Tracker does offer some utility.

I think the Ubuntu devs should consider merging the two. What if the U1 system could upload the files to the cloud, where they could be indexed and have the resulting index merged back down to the client.

This would increase the utility of U1 and give netbook users, etc. access to indexing, which is difficult to take full advantage of on a limited system and the rest of us don't have to run 10,000 daemons just to have a nifty desktop.

What do others think?

The current tracker version in Ubuntu is mostly unmaintained, doesn't work that well and isn't anything like the tracker version which has been proposed for GNOME.

If you want to test the latest tracker, then you can use the PPA here:

> deb [http://ppa.launchpad.net/tracker-team/tracker/ubuntu](http://ppa.launchpad.net/tracker-team/tracker/ubuntu) lucid main 


Or if you are brave:

> deb [http://ppa.launchpad.net/tracker-team/tracker-unstable/ubuntu](http://ppa.launchpad.net/tracker-team/tracker-unstable/ubuntu) lucid main

This will be uploaded to Maverick once we have finished with Lucid

---

### Post by gunksta on 2010-04-09
Interesting. For the time being, I don't see any need to use tracker. I think I'll just wait for the Maverick Alpha1.

I'm curious to see how the new theme gets integrated with the new Gnome-Shell or if Mark has something else up his sleeve.

---

