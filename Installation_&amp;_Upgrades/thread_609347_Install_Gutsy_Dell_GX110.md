---
title: "Install Gutsy Dell GX110"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by NJC on 2007-11-10
Dell Optiplex GX110 PIII/933Mhz 512 megs RAM

Installing Gutsy on a clean 6.4gb - configured three partitions: /, /home and swap. Currently trying 3rd install and it continues to hang at "Configuring apt (82%) Scanning the mirror.."
I checked the Live CD for errors ... as well, I have run Dapper on this machine OK. So I assume the hardware will work. Any ideas on the problem??

---

### Post by NJC on 2007-11-11
After further searching, an easy fix was to disable network connection. My PC is hooked up to a router, but no internet connection so I think Gutsy hung while trying to download updates. 

NOTE: Heaps of repositories will be commented out in the Sources.list file - if no internet connection exist. This will obviously need to be fixed. 

Hopefully I can post more info about Gutsy but it seems VERY good - LOTS of improvements over Dapper.

---

