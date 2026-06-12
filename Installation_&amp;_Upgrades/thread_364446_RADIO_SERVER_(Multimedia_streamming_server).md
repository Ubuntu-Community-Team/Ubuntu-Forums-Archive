---
title: "RADIO SERVER (Multimedia streamming server)"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by jorgerosa on 2007-02-18
Hello All.
Im trying to set (in a simple way) a multimedia broadcast by streaming
(**video/audio streamming web server**).

To start, im going only for a audio (web radio) server:

I found some ways (using: **icecast2 - ices - MuSE**),
But after all my tries, everything seems to be too complicated, it worked one time (i dont know how ive done it. lol). Since ive restarted the compuner never worked again. Im trying for 3 days since but no way... (im pro in Windows, but Im newbie in Linux, just 15 days using it, (never used it, just read in internet about it)  Im _trying_ really hard to go for Ubuntu Linux forever :)  
I had no problems to setup FTP, HTTP, EMAILS, and much other Servers.
Even using terminal commands, but now about streaming server... no way :(  

I found **dynabolic** (multimedia linux) - [COLOR="RoyalBlue"][http://www.dynebolic.org](http://www.dynebolic.org)[/COLOR]
And this module for it (**Soma Suite**) - [COLOR="RoyalBlue"][http://www.dynebolic.org/index.php?show=modules](http://www.dynebolic.org/index.php?show=modules)[/COLOR]

1 - There is some kind of "radio straming kit (server and GUIs)" in the way of "install and you are ready" ? (Like i found in dynebolic linux?) 
2 - Or a SIMPLE way installing ICECAST2 - MUSE ?
3 - Or a SIMPLE way installing ICECAST2 - SOMA SUITE ?

*(sorry my english, guys) * THX!

:guitar: :-({|=:-\" \\:D/

---

### Post by jorgerosa on 2007-02-21
OK, after some time i solved myself this issue. (Its about creating a stream audio/radio server)
**[COLOR="Red"]RESOLVED:[/COLOR]** I posted here, in a very simple way: [http://www.ubuntuforums.org/showthread.php?t=365955](http://www.ubuntuforums.org/showthread.php?t=365955)

So about multimedia ([COLOR="Red"]**movies in real time from webcams and/or avi files**[/COLOR]) server... not yet.
Any help here?... please? THX.

---

### Post by jorgerosa on 2007-02-21
Im trying this **VLC** *(VLS is dincontinued)* multimedia server from VideoLAN:

Official Web site: [http://www.videolan.org/](http://www.videolan.org/)

Installing VLC on **Ubunu** GNU/Linux: [http://wiki.videolan.org/Ubuntu](http://wiki.videolan.org/Ubuntu)
Simple "how it works diagram": [http://www.videolan.org/vlc/streaming.html](http://www.videolan.org/vlc/streaming.html)
Forum: [http://forum.videolan.org/](http://forum.videolan.org/)
HOW-TO page: [http://wiki.videolan.org/How_to](http://wiki.videolan.org/How_to)

Ive no results yet. But i think im in the right way...
If anyone can explain in a **easy way** How to have movie files (and also a webcam) on my PC (server) and send it to HTTP (web) pages, please do so. *(Im new in Linux stuff)* THX.

---

### Post by jorgerosa on 2007-02-21
Guys! Plz Help!

---

### Post by christhemonkey on 2007-02-21
Maybe try GNUMP3d?
Not tried it just remember that it did something similar to what you want?

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Streaming_Media_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Streaming_Media_Server)

---

### Post by jorgerosa on 2007-02-21
*THX christhemonkey, im on it. Later, Ill post here my experience. :-D*

1 Day Later...
**My result:** Easy to install its on the repositories, seconds later i tried in the browser: [http://localhost:8888](http://localhost:8888) (you can also put [http://127.0.0.1:8888](http://127.0.0.1:8888)) and... WORKED!... (I tested with MP3 OGG and AVI files, so like you can see this is not only a radio server but also a video (multimedia) server, as it works fine with AVI files!)

[COLOR="Red"]**Ubuntu Install:**[/COLOR] (On the menus) *System* ---- *Administration* ---- *Synaptic* (here search for then mark for installation finally click Apply)... 

[COLOR="Red"]**How to set: **[/COLOR]GNUMP3d
EDIT FILE: /etc/gnump3d/gnump3d.conf

IN THIS FILE (gnump3d.conf) CHANGE THIS (To match your personal settings)
***REPLACE:*** root = /var/music ***BY YOURS:*** root = /home/mymusic
***REPLACE:*** user = gnump3d ***BY:*** user = root

SAVE CHANGES THEN RESTART SERVER: /etc/init.d/gnump3d restart

SEE IF IT WORKS IN YOUR BROWSER: [http://127.0.0.1:8888](http://127.0.0.1:8888)

( THX again christhemonkey)



[COLOR="Red"]**[COLOR="SeaGreen"]Now, apeared also this "how-to" in the ubuntu forums, that can be usefull:[/COLOR]**[/COLOR] [http://ubuntuforums.org/showthread.php?t=34359](http://ubuntuforums.org/showthread.php?t=34359)

---

