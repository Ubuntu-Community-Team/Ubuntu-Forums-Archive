---
title: "Torrent for a linux server (and ps3 media server) - unenlightened user"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by sereth on 2008-09-12
Hi! I’m new to the forums and basically new to the linux world :) 

Installed Ubuntu 8.04.1 server on a computer here. Got www, ftp and ssh up and running. Missing a few things, amongst the others, a good torrent client. Got transmission running on my macbook and I like the fact that I can download a file to a certain folder, and it will automatically  download the file, in a temporary folder, then move the completed file to another folder. After a certain ratio, the .torrent file is removed.

In other words:
- I download a .torrent file to a specified folder (ex: /home/torrent/torrentDWN)
- It starts the downloading process in a new folder (ex: /home/torrent/torrentTMP) and removes the .torrent file
- All finished downloads in yet another folder (ex: /home/torrent/torrentfinished or /ftp/new/)
- After a certain ratio the download gets removed from the torrent list (deactivated from the program itself, IOW stops seeding)

First of all, the server is only console based(ssh), it’ll be a box in a corner without much else than a power cord and a couple of ethernet cables. 

I’d really like it to be “not java”, hopefully c/c++ and I would also like to be able to add trackers. To top it of it would be great if it had a www interface to manage the whole thing (adding, seeing the status, removing active torrents etc, could remove the necessity of automatically adding throug folders), but not a necessity(unless the web functionality is better than the automatic functions described above). I feel the important part is the automatics of the managing of the files(auto-detecting of a new torrent file in a folder..). Would be great if I could just “throw” a file at the server and a few days later it would be downloaded and put where it should be...


Yes, I’ve googled it and searched around for a lot of different programs, none who offer easy information about what I am looking for. I’m asking about you’re suggestions, what is the best, which doesn’t “hog” all the memory, which don’t inflict the system much when idle? etc..


On another note, got a ps3 on the network, any ideas on a service which would provide both audio and video through the media server thing? (upnp I think?). Trouble seems to be supporting both sound and video (mp3 and wmv or something). I’d like something which provide most “normal” formats (xvid, divx (avi) and mp3. Any info would be great!



Thanks for any replies, I really do appreciate and depend on it. 
(sorry if I'm in the wrong category, feel it's in teh installation category though..)

:popcorn:

---

### Post by alexpenson on 2008-10-02
have you looked at rtorrent?

---

### Post by jay3712 on 2008-10-15
I'm looking into rtorrent myself right now.
For your question about streaming to the ps3, I use mediatomb. It works great for streaming my audio (mostly mp3), video (mostly divx, avi), and pictures to my ps3. Search for it here and you will find guides.

Jason

---

### Post by sereth on 2008-10-17
alexpenson: Yeah, it seems like the most promising one. Although getting the documentation about features was a bit "hard". But reading the online(example) config file cleared things up ;) I guess it covered most of my needs. Thanks.


jay3712: Seen it has been mentioned, but haven't tried it yet. If I can stream mp3 and divx I guess I'm pretty much covered ;) Thanks to you as well.

---

