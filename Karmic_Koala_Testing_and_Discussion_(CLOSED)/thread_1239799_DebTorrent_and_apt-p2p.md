---
title: "DebTorrent and apt-p2p"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Progressive on 2009-08-13
Just wondering if Ubuntu is considering implementing [DebTorrent]("http://debtorrent.alioth.debian.org/") or [apt-p2p]("http://www.camrdale.org/apt-p2p/") in the foreseeable future.

Are the devs aware of it? Surely it would drastically reduce the load on ubuntu's servers and provide much faster downloads for us users.

Perhaps we as a community could even contribute to the development of this software.

In a perfect world we could even mix this with the idea of [delta upgrades]("http://brainstorm.ubuntu.com/idea/13/") and LZMA2 compression :D

---

### Post by kingborel on 2009-08-13
There's already a blueprint underway for a deltadeb mechanism

[https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads](https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads)

Personally I don't like the idea of any torrent-based update system, I'd rather download my updates from  a signed server.

---

### Post by inportb on 2009-08-14
Why not just get the hashes from your signed server and use them to verify the files you get off p2p? That sounds rather like what bittorrent does, anyway.

---

### Post by vishalrao on 2009-08-14
related thread here: [http://ubuntuforums.org/showthread.php?t=1215217](http://ubuntuforums.org/showthread.php?t=1215217)

---

