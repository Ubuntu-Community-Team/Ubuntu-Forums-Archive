---
title: "problem after trying out 12.04 beta2"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by jrl1 on 2012-04-22
I recently tried out the live CD of 12.04 64bit beta2, but did not install it. Now I am back using 11.10 64bit, I have problems when updates are available.I get a message saying CD/DVD 'Ubuntu 12.04LTS_Precise Pangolin_- Beta amd64(20120328) is required. When I insert the disk a message says Failed to download package files, check your internet connection. The details show failed to fetch cdrom ubuntu 12.04 lts
My system is a desktop alienware amd 64 4000+ with 2gb ram,ubuntu 11.10 dual booting with windows xp.
I thought the idea of using a live cd was that you can try out an OS without it affecting your current system. 
Does anyone know why this should happen when its not been installed?

---

### Post by darkod on 2012-04-22
Live mode shouldn't change anything on your hdd.

Very weird. Take a look in Software Sources, in case somehow the 12.04 cd exists as a source there. Deselect any cd sources and leave only the online repositories.

Not sure if those options are at the Update tab in Software Sources or not, look around.

---

### Post by jrl1 on 2012-04-22
Thanks. You were right. In software sources I deselected CD 12.04beta, as a source. Update manager now works perfectly.

---

### Post by The Cog on 2012-04-22
Excellent. You can use **[COLOR="Red"]Thread Tools[/COLOR]** at the top of this page to mark the thread as solved.

---

