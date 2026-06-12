---
title: "Question About Music Players"
date: 2016-07-26
forum: MINT
---

### Post by billy30 on 2016-07-26
i have spent a couple years now trying to get a music player on my Linux machine (Banshee, Rhythmbox, Amarok, VLC, etc) to play my music via UPNP from my windows computer running Foobar. The only players i could get to work were eezUPnP and Foobar running in Wine. I like to listen to my music constantly and this, coupled with needing to use some adobe programs for school, made logging onto ubuntu an inconvenience. It is about 3 months now and i updated to Linux Mint 18 and decided to give it a try again with no luck. So then i figured maybe i should make sure i have the most up-to-date versions of these music players and, to my amazement, these programs seem outdated. The last update to Banshee seems to be 2014 and Rhythmbox is 2015.

So my question is: What gives? Why are there no good, up-to-date, continuously maintained music players for Ubuntu? It just seems like a feature that would be a priority. Furthermore; why can i only get eezUPnN and Foobar (running through Wine) to discover my media server (Something i have asked on the forums before and on the Banshee site to little response)?

I would love to see a fork of Foobar for Linux Foobnix is ok but doesn't support Foobar components.

Also, don't take this as a complaint, just astonishment, and frustration.

---

### Post by TheFu on 2016-07-26
Why?   One possibility is .... perhaps 
a) the developers all run Linux.
b) don't use UPnP (which is fraught with security issues).  
c) They barely test anything with Windows. It just isn't a priority.
d) WINE isn't used much.  When I was first making the switch to Linux full-time, I used WINE a bunch. Eventually, it was just too much hassle and easier to use native programs.

I'm not a dev anymore, but keep all my music on Linux shares and available through a Plex Server. If any client wants access, they can get it via DLNA or the web interface or over sshfs. Before switching to plex, I used clementine in client/server mode and before that used gnump3.  My clients are ... kodi, kodi, web-based, Clementine, and a dlna client on android. Clementine is for long listening periods at my desk from time to time - maybe 3 times annually. Stereo systems are connected to kodi machines here.

None of this means what you are doing is wrong or bad, just not what a typical Linux dev would be doing ... probably. That's my guess.  Could be wrong.

Sounds like you have an "itch" that would be scratchable.  OTOH, I see any license data for foobar or the "components" on the website. Might make forking impossible.

---

### Post by Keith_Helms on 2016-07-27
I have 2 Linux desktop systems upstairs that I sometimes run DLNA/UPNP servers on (ushare) - one for audio and one for video.  That lets my TV and blu-ray player downstairs play files over the network, which works well.  I recently wondered if there were any good Linux DLNA clients/players and did a search.  Kodi and VLC were mentioned.  My understanding of Kodi is that it's a pretty heavyweight application, on the order of MythTV, so I thought it would be complicated and overkill.  VLC *does *have a UPNP option, but when I click on it, it does precisely nothing as far as I can tell.  No errors, no list of servers, no list of files, nada.

I suppose I'll research setting up a streaming/internet "radio" server and client next when I get around to it.  I assume Linux has **some** way of serving up media over the network other than just a plain Samba/NFS mount.  I saw something about streaming pulse audio to a different computer which sounded strange, but didn't dig into it at the time.

---

### Post by howefield on 2016-07-27
Thread moved to the "*MINT*" forum.

---

### Post by TheFu on 2016-07-27
Kodi does like to take over the GUI, but don't think I'd call it *heavy*. Kodi isn't really that complicated, just demands that different local media types be named in specific ways. It parses the filename/directories to use different video *grabbers* and fill in the metadata. Kodi isn't that great for music/audio listening. Audio quality isn't the issue. If you have pre-made playlists, it works. Anything more complicated than that, not so much ... Too much hassle to create a list of music to play by commonly used filters (keywords, BPM)

VLC is great to playback 1 video file or a play list of videos. Can't say that it is useful as a music player. I've gotten the DLNA client part of vlc to work maybe 3 times in 3 years. Tried it again a few weeks ago and gave up. Claiming DLNA as a feature and actually having it work are 2 very different things, it seems. It isn't even alpha level. Something that works 1 time in 500 attempts isn't a feature.

The great thing about Kodi is all the free plugins. Basically, most internet media has a plugin and these work better than other options.  I prefer Kodi over my Roku for interent streaming. Fewer entries to get what I want. Control over streaming quality too.  But this isn't what the OP wants.  

I think **clementine** is the best answer - can be used from anywhere in the world using sshfs. It works. It is cross-platform too.  Want the v1.3+ version to get all the remote control stuff. I like that the android application team spell out WHY the different permissions are needed AND that the permissions make sense for the purpose of the application.  I don't use internet media for music, but clementine can play from streaming services and file storage services (dropbox, box, google and MSFT storage).
 I use it with sshfs a bunch (which doesn't help Windows clients). My tricks are:
a) always mount the remote music storage to the same place. /Music, perhaps?
b) be certain to let clementine parse the files on the LAN to not waste time doing it on the WAN.

Since I've never used or seen foobar2000, don't know how well this can gel into the OPs playback methods.

---

### Post by billy30 on 2016-07-27
All great replies. To simplify what i want, though:
I just want an easy and simple way to stream my music from my PC to my Laptop. I sometimes like to go to my backyard when it is nice out and do work on my laptop. So it would be nice to still be able to tap into my music on my PC and considering it is on the same network, it makes sense to just stream it to my laptop.

Foobar is my music player on my PC. I love it and have used it for a long time due to its customizability (i think that is a word) and it is lightweight and has a great community. I have a plugin for Foobar that allows me to use it as a server to stream my library through UPnP. It is very simple. Very easy. My problem is that music players on Linux (like Banshee and Rhythmbox) **DO SUPPORT UPnP.** Banshee supports it through a plugin, and i think Rhythmbox does out of the box (or maybe a plugin as well). But the only way i can get either of them to even recognize the server is when eeZUPnP music player is running for whatever reason. Then the server magically appears on Banshee but it is unusable/unplayable. To me, this is something that could probably be fixable, but i have little clue as to the reason.

I understand what you all are saying about UPnP and priorities and such and that makes sense and is fine. I just think streaming music over the same network shouldn't be difficult. In the meantime, i have Foobar running fine in Wine right now and it is able to play music off of the stream. It isn't ideal, but it works.

Thanks again for all the input though and i am going to look at Clementine. I really don't know how i overlooked this. I even google searched things like "best Linux music player" and "banshee alternatives." For whatever reason, it never came up.

Also, the reason why i posted this in Ubuntu is because 1. i feel like this is an ubuntu problem and not specifically Linux Mint which is based on Ubuntu, and 2, whenever i post in Linux Mint forums, i rarely get responses.

---

### Post by yoshii on 2016-08-02
SHOUTcast.com might have some answers.  I believe they invented internet radio technologies.

---

### Post by jaycrav3ns on 2016-09-13
Banshee could suddenly see the shared files was because of eezUPnP having the 'out of the box' ability to be a UPnP controller/renderer, which I would say it is more than a music player at all. It has written into the software what those other apps did not.  VLC should...but ole boy is right about it.  It works instantly with android, but vlc on linux has never once showed me a list of upnp shares.  My determination to make minidlna led me to this project which may help you out:  [http://miniupnp.free.fr/](http://miniupnp.free.fr/)  :KS

---

