---
title: "Network Monitor broke wireless card alias"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by marion on 2006-07-12
I installed a clean version of Dapper, installed ndiswrapper to get my wifi working and all was great until... Dapper auto updated the network monitor.  

Here's the problem I have now.  Before I would boot, the wifi connected and life was with out annoyances.

Now since the network monitor was updated, I have to sudo modprobe ndiswrapper from terminal, and all is well again.

I remember editing an alias file or something a long time ago (FC2 I think) to get wlan0 to be recognized.

The problem here is that Dapper is seeing the wifi as eth1, and the network montior is looking for wlan0 again.

when I sudo modprobe ndiswrapper, it recognizes eth1 and connects to the router.

Just don't know how to fix that problem at boot up.

Any help is appreciated, and thank in advance.

---

### Post by marion on 2006-07-12
I found the file.  It's in  sudo gedit /etc/modprobe.d/ndiswrapper

I found this line...

alias wlan0 ndiswrapper

...and changed it back to...

alias eth1 ndiswrapper

... rebooted and I was connected.

---

