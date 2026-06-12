---
title: "anyone torrenting just now?"
date: 2005-05-15
forum: Installation &amp; Upgrades
---

### Post by rogerdean on 2005-05-15
hi folks

my question is a little prior to install, but couldn't see a download forum... apologies

i'm having trouble with the torrents from the ubuntu site. i'm told the tracker is fine and there are loads of seeds and peers, but i never connect to anyone. i need the hoary i386 install disc, although it's the same problem with all ubuntu torrents at the moment it seems. non-ubuntu torrents are fine. does anyone have any ideas?

cheers
roger

---

### Post by codejunkie on 2005-05-15
i've noticed the same thing using azureus the tracker shows fine but will not download the only thing that seems to work is use the direct download links here
[http://us.releases.ubuntu.com/releases/5.04/](http://us.releases.ubuntu.com/releases/5.04/) they still work.

---

### Post by rogerdean on 2005-05-15
god i hope they fix it for us. i'm at 34% of the download and here in the desert of sudan it's taken me three days! couldn't face starting again...

does anyone know how to get this message to the ubuntu torrent guru?

---

### Post by codejunkie on 2005-05-15
i hope it's fixed soon i've been trying to get the hoary-i386-dvd for three days but it's not looking good.

---

### Post by goofrider on 2005-05-16
I think it has to do with the fact that the tracker is just a BitTorrent client - BitTornado.

Goto [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/) and it clearly says on the top:

```

tracker version: T-0.3.8 (BitTornado)

```

I won't be suprise if BitTornado just stop working after being up for too long handling too many connections and needs to be restarted periodically.

using a bona fide tracker like BNBT should be a lot more reliable.

[http://bnbt.depthstrike.com/](http://bnbt.depthstrike.com/)

---

### Post by rogerdean on 2005-05-16
i see now that the whole tracker page is down. maybe they've spotted it...

---

### Post by bored2k on 2005-05-16
[QUOTE=rogerdean]i see now that the whole tracker page is down. maybe they've spotted it...[/QUOTE]
 It is down
[http://www.demonoid.com/torrents/details/110153/](http://www.demonoid.com/torrents/details/110153/)
Panickedthumb upload another 386 image.

---

### Post by bored2k on 2005-05-16
[QUOTE=bored2k]It is down
[http://www.demonoid.com/torrents/details/110153/](http://www.demonoid.com/torrents/details/110153/)
Panickedthumb upload another 386 image.[/QUOTE]
 [http://mininova.org/search/?search=ubuntu](http://mininova.org/search/?search=ubuntu)
Those work apparently.

---

### Post by rogerdean on 2005-05-17
thanks guys

maybe i'm being a bit dim but i can't find a clickable link on those alternative pages. do i have to be a member or something?

also, although the ubuntu tracker page is back i'm still having no joy. is anyone out there successfully using the torrent just now?

cheers
roger

---

### Post by Rodrigo on 2005-05-17
I did have a similar problem. but I just upgraded Azeurus and that fix the problem.

---

### Post by rogerdean on 2005-05-18
ladies and gentlemen...   the torrent is back up
many thanks to mako for fixing it  :)
roger

---

### Post by fuego on 2005-05-21
I've had the same problem since 20 May, not only on the ubuntu tracker but all the mirrors as well. Thought it was my client, and it could be as I updated both Deb boxes on Friday but I was able to download other, non-ubuntu, torrents as tests.

The client error message is:

[17:18:18] Problem connecting to tracker - <urlopen error (111, 'Connection refused')>

The same error message will be displayed when clicking on the ubuntu torrent link:

 [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

I think  goofrider may be correct in his post.

rob

---

