---
title: "Missing VLC after install Gutsy"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by gbbetts on 2008-04-01
Total noob here -- I'm trying to get Ubuntu set up, but can't find the Video Lan application, and the VLC website doesn't have anything to download. Can somebody walk me through how to get this set up? I'm trying to use my computer as an entertainment hub, but alas without much luck.

Much obliged,
GB

:guitar:

---

### Post by Thanoulis on 2008-04-01
The VLC is in the repositories...you can either search for it in synaptic package manager, or simply write in a terminal:
```
sudo apt-get install vlc
```
Good luck with your entertainment PC!!!

---

### Post by gbbetts on 2008-04-01
Okay -- here's what I get:

Reading package lists ... Done
Building dependency tree
Reading State information... Done
E: Couldn't find package vlc

??

---

### Post by warp99 on 2008-04-02
You need to enable the universe repositories. Open the Synaptic package manager then go to Settings >  Repositories and tick the box marked "universe", close then click "Reload". VLC will then show up in the package list. 

Please check out my signature for more helpful tips.

---

### Post by gbbetts on 2008-04-02
Issue solved -- thanks for the help -- turned out that I needed wireless access/network setup before VLC became available. I  set up using Linuxant, which allowed me to bypass problems I was having with ndiswrapper, and presto! everything works. Downloading LinuxMCE now, and well on my way to my media hub!

GB

:guitar:

---

