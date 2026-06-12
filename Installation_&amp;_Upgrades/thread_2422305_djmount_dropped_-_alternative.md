---
title: "djmount dropped - alternative?"
date: 2019-07-05
forum: Installation &amp; Upgrades
---

### Post by Newbunto on 2019-07-05
djmount exists and works fine in 18.04 and while I am not running 18.10 seems still to exist in that release but seems to have been dropped from 19.04 (I've just upgraded from 18.04 to 19.04)

(So there's no DJ in the disco)

In 19.04 are there any alternatives for exposing DLNA content transparently as a file system or failing that exposing DLNA content? My main goal is organising my music, rather than playing it e.g. finding music by string in track title or string in artist name or e.g. listing tracks by a given artist. (I tried VLC under 18.04 for this but the search function seemed limited and/or flaky.)

---

### Post by TheFu on 2019-07-05
I don't understand the question. Why does DLNA matter?

clementine
miniDLNA
Plex
Kodi
gnump3
EasyTag

If you want to organize audio files, then EasyTag can be used to move each file into a directory structure based on the ID3 tags in each file.  Or you can use the directory structure to put ID3 tags into each file.

DLNA doesn't create a file system. It makes virtual folders only based on tags in the files.  DLNA doesn't have **any** security at all, which can be a huge negative if you have children on the network.

VLC is a terrible music player, unless you are only using it to access DLNA virtual folders.

---

### Post by Newbunto on 2019-07-05
> DLNA doesn't create a file system.

Correct - but that is precisely what **[FONT=courier new]djmount[/FONT]** does - it exposes content that is served by a DLNA server as a file system, which is what I want.

I am already using EasyTag to set tags (when they are not set automatically). I already have a DLNA server.

(I'm not too worried about the lack of security with DLNA. This is LAN-only, not exposed to the internet. None of the content is writable to the DLNA server. None of the content is confidential or personal. However if you want to elaborate on the security issues with DLNA, please do.)

I'm not using VLC to play music. I tried it as a one-off to see what its DLNA support was like. In the absence of **[FONT=courier new]djmount[/FONT]** maybe what I am looking for is a good GUI DLNA client or preferably a good command line DLNA client, where "good" relates to *finding* music, not playing it.

---

### Post by TheFu on 2019-07-06
> **Newbunto said:**
>   what I am looking for is a good GUI DLNA client or preferably a good command line DLNA client, where "good" relates to *finding* music, not playing it.

Thanks for the clarification. I think I understand.

Plex probably isn't an option - way too much JS to be automated.

Just throwing out a few other ideas below.

gnump3 has great search capabilities through their web interfaces. gnump3 will generate playlists. gnump3 is an old-school cgi solution, so it could be considered a REST interface. ;)  I remember searching for "walk" and getting about 50 songs back from my collection.  No BPM capabilities, unfortunately.

Clemetine has good search too, but it wants direct access to the files.
I've been using cmus lately. It is a TUI music player. It is handy to ssh into my music-Pi and control it.  Search is very simplistic with it.

Have you looked at any mpd-based audio solutions?  There are lots of different clients, each can control the mpd server.  I haven't played with this type of solution nearly enough. Might find some better clients down this direction.  [https://github.com/trapd00r/pimpd2](https://github.com/trapd00r/pimpd2) has search. Supports filters
```
$ pimpd2 --randomize 42 Nirvana | pimpd2 -af
```

Spent about 30 min screwing around with mpd and pimpd2 on a few systems here.  mpd requires X11 which is bloated for a server-only install.  Ended up installing mopidy on a r-pi, but never got passed the *scan* media part before it locked up.  So I moved onto a linux laptop and installed pimpd2 ... which is a perl thing (I'm a perl guy), but the install was non-trivial.  Had to install 3 ubuntu packages before going into the perl cpanm package world to get those dependencies install, and finally had to pull the pmpd2 code from github --- and it wouldn't connect to the r-pi mpd server.  The mpd documentation isn't clear enough for me to "get it."  Some days I'm just an idiot.  Back to using Clementine and cmus for me.

I'm not worried about DLNA security on a home network, beyond limiting access to content you might not want pre-teen kids accessing.

---

### Post by Newbunto on 2019-07-08
> Just throwing out a few other ideas below.

Thanks for the ideas. It looks as if **[FONT=courier new]cmus[/FONT]** may be able to do the job. It does require access to the underlying files (i.e. not reflecting what the DLNA server is serving) but that should be adequate in my situation. Using **[FONT=courier new]cmus[/FONT]**, I can see that I really want "filter" rather than "find", but I can live with that. Maybe I haven't yet discovered all that this package can do.

I (re)tested a few GUI DLNA clients today. The summary is:

* VLC - rock solid when accessing the DLNA server but seemingly doesn't have sufficient search capability (in part because my DLNA server itself doesn't have *any* search capability?)
* Gnome Videos (Totem) - always crashes when traversing the DLNA tree (I let it send an error report) but does recognise the DLNA server - requires an additional package (which is OK)
* Rhythmbox - recognises the DLNA server but DLNA client seems to hang fairly soon and stops working - requires an additional package (which is OK)

---

### Post by Newbunto on 2019-07-30
An alternative approach to the original problem as posed (expose DLNA-served content as a file system) is to put in a DLNA to WebDAV converter to a web server and then use the WebDAV backend for gvfs. Not tested on 19.04 which is of course where it needs to work to cover for the absence of **[FONT=courier new]djmount[/FONT]**.

This would be a messy solution as it involves lots of moving parts e.g. two web servers (DLNA is already a web server), and duplication, as both DLNA and WebDAV involve doing stuff by sending XML over HTTP (but are completely incompatible). Goodness knows why DLNA didn't just use or build on WebDAV, albeit that WebDAV is very much a superset of what you need in order to do DLNA.

---

### Post by TheFu on 2019-07-30
WebDAV is pretty famous for having really, really, bad security.  Easily hacked doesn't begin to say enough about it.

---

### Post by Newbunto on 2019-07-30
WebDAV itself or any given implementation? I see quite a few obvious attempts to exploit WebDAV implementation problems come in to my existing internet facing web server - so yes the hackers are out there.

As stated originally though this (DLNA etc.) is not exposed to the internet so I am not too concerned about hackers. As an added safety measure, DLNA is itself intrinsically read-only, as far as I know, therefore presenting it through WebDAV doesn't magically allow media to be altered, and the media is read-only to the DLNA server, potentially not even accessible to the web server. The clunky two web server architecture even enforces a measure of separation or isolation.

However if you want to elaborate with examples of successful WebDAV exploits I am interested.

---

