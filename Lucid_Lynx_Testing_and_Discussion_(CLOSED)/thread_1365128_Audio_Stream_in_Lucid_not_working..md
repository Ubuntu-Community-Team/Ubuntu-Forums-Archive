---
title: "Audio Stream in Lucid not working."
date: 2009-12-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-12-26
[http://959theranch.com/](http://959theranch.com/) does not appear to work with mplayer and the codecs..at least on my machine.  All other audio works..Any ideas?

---

### Post by sports fan Matt on 2009-12-26
Strangely enough that is the only link that refuses to play atm.

---

### Post by zika on 2009-12-27
I'm having similar issue with [Apple-trailers](apple.com/trailers/)...

---

### Post by mc4man on 2009-12-27
Everything on that radio page seems to play fine (totem-mozilla plugin) or off of a r. click open with a player.
As far as the radio stream adding the url to the player of your choice should also work fine
(or make an .m3u or .xspf to load in a player

Maybe something was up on the station end.

The apple trailers don't seem to be working here either thru the totem-mozilla plug-in, while they work perfectly in karmic (one of the few things totem did/does right
Maybe file a bug on totem-mozilla

For the moment you could use mplayer if desired or download for player of choice

Ex. ( adjust cache as needed, plus any add. options add to end like -fs, for wget add red to link

```
mplayer -user-agent 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' http://movies.apple.com/movies/independent/warlords/warlords-tlr1_720p.mov -cache 4096 -fs
```

 ```
wget -U QuickTime/7.6.2 http://movies.apple.com/movies/independent/warlords/warlords-tlr1_[COLOR="Red"]h[/COLOR]720p.mov
```

---

### Post by zika on 2009-12-27
> **mc4man said:**
> Everything on that radio page seems to play fine (totem-mozilla plugin) or off of a r. click open with a player.
As far as the radio stream adding the url to the player of your choice should also work fine
(or make an .m3u or .xspf to load in a player

Maybe something was up on the station end.

The apple trailers don't seem to be working here either thru the totem-mozilla plug-in, while they work perfectly in karmic (one of the few things totem did/does right
Maybe file a bug on totem-mozilla

For the moment you could use mplayer if desired or download for player of choice

Ex. ( adjust cache as needed, plus any add. options add to end like -fs, for wget add red to link

```
mplayer -user-agent 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' http://movies.apple.com/movies/independent/warlords/warlords-tlr1_720p.mov -cache 4096 -fs
```

 ```
wget -U QuickTime/7.6.2 http://movies.apple.com/movies/independent/warlords/warlords-tlr1_[COLOR="Red"]h[/COLOR]720p.mov
```Thank You for the tip. I'll try it today.
Update. The trouble is, when I try wget, which I've tried already, before Your post, I get a small file that is not a movie. Something is wrong...
Not that AppleTrailers are important for me. I just use them as a test site ...

---

### Post by mc4man on 2009-12-27
> I get a small file that is not a movie. Something is wrong...

You must insert an h in the link as shown or you get basically nothing (about 83 bytes

---

### Post by zika on 2009-12-27
> **mc4man said:**
> You must insert an h in the link as shown or you get basically nothing (about 83 bytesI know that, I think I've put it, I'll try again.
Update: I made several typos so now it is OK. Thank You.

---

### Post by VMC on 2009-12-27
> **sox fan Matt said:**
> [http://959theranch.com/](http://959theranch.com/) does not appear to work with mplayer and the codecs..at least on my machine.  All other audio works..Any ideas?

From mplayer I get an error something about 'mmsh'.

---

### Post by sports fan Matt on 2009-12-27
Using the ppa from mplayer gives me this: mplayer:
 Depends: libdirectfb-1.0-0  but it is not installable
  Conflicts: mplayer-nogui  but 2:1.0~rc3+svn20090426-1ubuntu12 is to be installed

---

### Post by sports fan Matt on 2009-12-27
just fyi, using that ppa there is a new mplayer but it is greyed out.

---

### Post by mc4man on 2009-12-27
```
mplayer mms://lkcm.wmlivesvc.vitalstreamcdn.com/live_lkcm_vitalstream_com_LKCM-DFW-KFWRFM2?MSWMExt=.asf
```

Don't know why you'd want to use a ppa for testing alpha's ect.

---

### Post by sports fan Matt on 2009-12-27
Honestly was just seeing if there was a difference but there really isn't.

---

