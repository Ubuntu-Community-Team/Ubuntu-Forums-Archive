---
title: "Can not use GUI at all in 22.04 virtual machine after upgrade"
date: 2022-04-23
forum: Installation &amp; Upgrades
---

### Post by f00dl3 on 2022-04-23
I upgraded my Virtual Machine instance of Ubuntu from 20.04 to 22.04 today and immediately I am noticing that in VirutalBox I can't move anything. The mouse cursor is frozen at the login screen. Everything behind the scenes works - I can SSH in, the database and tomcat services work fine - though I can not seem to get ffmpeg network streams to work over RTSP - not sure if that's related to the GUI issues though. 

Not sure if this is a known issue or not. I tried another apt update; apt upgrade but no new packages are available.

---

### Post by TheFu on 2022-04-23
Have you reinstalled the guest additions?   Whenever a new kernel is installed, the guest additions need to be re-linked .... i.e. reinstalled if you don't do it manually.

---

