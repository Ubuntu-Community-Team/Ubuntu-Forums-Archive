---
title: "several problems"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by Setlec on 2007-08-30
i've installed Ubuntu 3 days ago but here iam:
the bittorrent doesn't work! why? i've reinstalled the whole bittorrent (with the gui) via a console but it won't start, I've installed then the Azureus it work but when i start a torrent download it donwload at 5kbps (and less 0bps most of the time) while on my previous distrib i could download at 100kbps.

and what firewall eays to use will you suggest to me? i've installed Firestarter but i don't really understand how to config...

---

### Post by senuxis on 2007-08-30
Try an other client; perhaps [deluge]("http://deluge-torrent.org/"). You could also try ```
sudo apt-get install deluge
``` to see if it's in the ubuntu repositories.

---

### Post by Setlec on 2007-08-30
it's not on the repositories...

---

### Post by forestpixie on 2007-08-30
you can get deluge [here ]("http://deluge-torrent.org/downloads") - just pick the feisty fawn deb for you - either 386 or 64 bit

download and dble clik

---

### Post by Setlec on 2007-08-30
> **forestpixie said:**
> you can get deluge [here ]("http://deluge-torrent.org/downloads") - just pick the feisty fawn deb for you - either 386 or 64 bit

download and dble clik

i've installed but it doesn't start it open a bar saying opening deluge-torrent then nothing happens

---

### Post by forestpixie on 2007-08-30
try running from the terminal - post error messages here

I don't know too much about deluge - co I didn't like it myself

---

### Post by Setlec on 2007-08-30
as you asked:

```
setlec@ruthlessearth:~/Telechargement$ deluge 
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Capping download to -1 bytes per second
Capping upload to -1 bytes per second
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin EventLogging
Initialising plugin TorrentNotification
Initialising plugin SpeedLimiter
Initialising plugin DesiredRatio
Initialising plugin TorrentFiles
Initialising plugin NetworkHealth
Initialising plugin BlocklistImport
Initialising plugin TorrentCreator
Initialising plugin ExtraStats
Initialising plugin TorrentPieces
Initialising plugin NetworkGraph
Initialising plugin Locations
Initialising plugin SimpleRSS
Initialising plugin TorrentPeers
Initialising plugin TorrentSearch
Applying preferences
Starting DHT...
No DHT file to resume
terminate called after throwing an instance of 'asio::system_error'
  what():  Address already in use
Aborted (core dumped)
setlec@ruthlessearth:~/Telechargement$ 

```

---

### Post by forestpixie on 2007-08-30
well as I thought I have no idea - perhaps someone else is watching and can jump in :(

If not try posting athread on Absolute Beginners

In the meantime if you want to try a different torrent I use ktorrent, you can get it from Add/Remove, Synaptic or straight from the terminal

```
sudo apt-get install ktorrent
```

Sorry I can't be of more assistance

---

