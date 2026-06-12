---
title: "Integrate Gnome Games with Empathy - Empathy Enhancement ?"
date: 2009-12-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-12-18
Pretty straightforward suggestion, could integration be possible ? A friend of mine has recently taken a shining to chess. It sparked this idea of being in a chat session, launching gnome games and inviting someone to a game. I assume the move commands, would be a few bytes of data over the pipeline :D.

What do you think ?
Side note: My latest game attached. beginner level though, haven't played in years...

---

### Post by orlox on 2009-12-18
> **Regenweald said:**
> Pretty straightforward suggestion, could integration be possible ? A friend of mine has recently taken a shining to chess. It sparked this idea of being in a chat session, launching gnome games and inviting someone to a game. I assume the move commands, would be a few bytes of data over the pipeline :D.

What do you think ?
Side note: My latest game attached. beginner level though, haven't played in years...

As far as I know, telepathy tubes are pretty generic, so they allow to transfer a wide range of data. Consider remote sessions, playlists and music can be shared along tubes...So, I guess that allowing remote multiplayer through a tube for the simple gnome games should be easy compared to the above examples.

---

### Post by zekopeko on 2009-12-18
This sort of integration is starting to come to Gnome. That was the whole point of adding Empathy to Karmic.

---

### Post by kostkon on 2009-12-18
Yeap, [this is already happening]("https://launchpad.net/~gnome-games-experimental"). You can even [try it yourself]("https://launchpad.net/~gnome-games-experimental/+archive/ppa").

---

### Post by orlox on 2009-12-18
> **kostkon said:**
> Yeap, [this is already happening]("https://launchpad.net/~gnome-games-experimental"). You can even [try it yourself]("https://launchpad.net/~gnome-games-experimental/+archive/ppa").

However, they're ppa seems very outdated. Last build of packages was nearly four months ago...

---

### Post by ranch hand on 2009-12-18
> **kostkon said:**
> Yeap, [this is already happening]("https://launchpad.net/%7Egnome-games-experimental"). You can even [try it yourself]("https://launchpad.net/%7Egnome-games-experimental/+archive/ppa").
Oh my, reading the PPA page and it says it may cause BREAKAGE.  We wouldn't want that here in the forum dedicated to just a stable system.

Sorry, couldn't resist.

---

### Post by gnomeuser on 2009-12-19
This is exactly the kind of enhancement Telepathy is designed to address. I am happy to see people finally appreciate this technology.

---

### Post by zekopeko on 2009-12-19
> **gnomeuser said:**
> This is exactly the kind of enhancement Telepathy is designed to address. I am happy to see people finally appreciate this technology.

Can't wait until Banshee replaces Rhythmbox. There is that sweet Telepathy-using extension that shares metadata and even streams and download songs.

---

### Post by jpeddicord on 2009-12-19
> **zekopeko said:**
> Can't wait until Banshee replaces Rhythmbox. There is that sweet Telepathy-using extension that shares metadata and even streams and download songs.

*drool*

I've switched back to RB from Banshee after not wanting to deal with some quirks, but as soon as that sharing feature lands I'll be won back over.

---

### Post by gnomeuser on 2009-12-19
> **zekopeko said:**
> Can't wait until Banshee replaces Rhythmbox. There is that sweet Telepathy-using extension that shares metadata and even streams and download songs.

Did I mention that we got audiobook library support, grid view, playlist syncing and internet archive support now.. Banshee is sweet.

---

### Post by Merk42 on 2009-12-19
Uh oh let's not talk about Banshee I know where that'll lead.....


So are Games with Empathy and/or clutter possibly going to be in Lucid?

---

### Post by gnomeuser on 2009-12-19
> **Merk42 said:**
> Uh oh let's not talk about Banshee I know where that'll lead.....


So are Games with Empathy and/or clutter possibly going to be in Lucid?

I believe two games were ported as part of GSoC, I think you can play tetris with your empathy mates right now..

Aside that there are less fun deployments such as sharing desktops with buddies and so on.

---

### Post by Regenweald on 2009-12-20
I think games like chess and poker could have really fun implementations over empathy+clutter... Team Chess, proper card games... it could get interesting :)

---

### Post by ranch hand on 2009-12-20
But not near the FUN of having a live human being across the table.

---

### Post by gnomeuser on 2009-12-20
> **ranch hand said:**
> But not near the FUN of having a live human being across the table.

Occasionally though the live human being you want to play with isn't available. E.g. the other day I was playing Risk (Attack!) with my fiancée who currently lives in Brazil on Facebook, I would love to play in person with her but this is a fine alternative.

That reminds me, we need a good easily networked Risk clone that integrates with the buddy list.

---

### Post by Sashin on 2009-12-20
Does anyone know if empathy is going to change much in the near future? At the moment pidgin feels a whole lot more slick.

---

### Post by gnomeuser on 2009-12-20
> **Sashin said:**
> Does anyone know if empathy is going to change much in the near future? At the moment pidgin feels a whole lot more slick.

The power of Empathy isn't really the slick simple interface but the underlying telepathy framework. As for what enhancements you'll see in Lucid the Me Menu is likely going to be the biggest change to how you'll interact with instant messaging.

[http://arstechnica.com/open-source/news/2009/12/ubuntu-1004-will-bring-panel-overhaul-social-network-menu.ars](http://arstechnica.com/open-source/news/2009/12/ubuntu-1004-will-bring-panel-overhaul-social-network-menu.ars)

---

### Post by Sashin on 2009-12-21
But I'm not one that likes sacrificing one thing for another, I want to have my cake and eat it too. It shouldn't require too much effort in making empathy slicker?

---

### Post by gnomeuser on 2009-12-21
> **Sashin said:**
> But I'm not one that likes sacrificing one thing for another, I want to have my cake and eat it too. It shouldn't require too much effort in making empathy slicker?

patches welcome

---

### Post by Regenweald on 2009-12-21
> **Sashin said:**
> Does anyone know if empathy is going to change much in the near future? At the moment pidgin feels a whole lot more slick.

> **Sashin said:**
> But I'm not one that likes sacrificing one thing for another, I want to have my cake and eat it too. It shouldn't require too much effort in making empathy slicker?

Please don't hijack with this again. For empathy vs pidgin start your own thread. That bad boy is already at the glue factory.

---

### Post by Merk42 on 2009-12-21
Kind of off topic, but I see Gnometris was replaced by Quadrapassel which I believe is running on Clutter!

---

### Post by jpeddicord on 2009-12-21
> **Merk42 said:**
> Kind of off topic, but I see Gnometris was replaced by Quadrapassel which I believe is running on Clutter!

The later gnometris versions were already clutter; qudreapassel is just a rename. :)

---

### Post by Merk42 on 2009-12-21
> **jpeddicord said:**
> The later gnometris versions were already clutter; qudreapassel is just a rename. :)

Oh I guess you can tell when it's in Clutter when the blocks are all ugly and completely flat.

---

### Post by jpeddicord on 2009-12-21
> **Merk42 said:**
> Oh I guess you can tell when it's in Clutter when the blocks are all ugly and completely flat.

lol, yeah they do need some textures for the blocks. An easy way to see the clutter effects is to fill a line and clear it; the row of blocks will explode. You can also notice the smoother animations when moving blocks left and right.

---

### Post by Merk42 on 2009-12-21
> **jpeddicord said:**
> lol, yeah they do need some textures for the blocks. An easy way to see the clutter effects is to fill a line and clear it; the row of blocks will explode. You can also notice the smoother animations when moving blocks left and right.

Upon further examination of quadrapassel (and even gnometris) not only are there tango themed block, but also sounds.

Why the heck is a silent flat version the default?
Is this like a bug (ie feature request) I could file?

---

### Post by jpeddicord on 2009-12-21
> **Merk42 said:**
> Upon further examination of quadrapassel (and even gnometris) not only are there tango themed block, but also sounds.

Why the heck is a silent flat version the default?
Is this like a bug (ie feature request) I could file?

[GNOME Bugzilla]("https://bugzilla.gnome.org/") (module gnome-games) would be the nicest way to go about it since it would all be upstream, but if you're not comfortable with that just file it on Launchpad and someone will help triage it.

---

