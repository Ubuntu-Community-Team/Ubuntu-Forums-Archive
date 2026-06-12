---
title: "please I cant open video with firefox"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by ireme49 on 2007-08-21
Bad Transport (rtsp://a151.v37374b.c37374.g.vr.akamaistream.net/ondemand/7/151/37374/1.0/clipdownloads.bbc.co.uk/realmedia/news/media/avdb/news/world/video/114000/nb/114175_16x9_nb.rm?title="BBC"&author="BBC"&copyright="(C)%20British%20Broadcasting%20Corporation")

this is the error that I get. also hjow can I install Real player or helix. I know helix is already installed even with the plugins but it wont open the video 
thank you

---

### Post by janbockaert on 2007-08-21
best way to watch video in firefox is the mplayer plugin (in synaptic, search for mplayer). You may need to add the medibuntu repositories: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Pumalite on 2007-08-21
Make sure you copy first: 'cp /etc/apt/souces.list /etc/apt/sources.list.back'
Then: 'gksudo gedit /etc/apt/souces.list'
Then add:
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

---

### Post by Gremlinzzz on 2007-08-21
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Helix_plug-in_.28plays_Realplayer_files.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Helix_plug-in_.28plays_Realplayer_files.29)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_RealPlayer_10_Multimedia_Player_.28RealPlayer.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_RealPlayer_10_Multimedia_Player_.28RealPlayer.29)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

