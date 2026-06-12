---
title: "open office updates error"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by rovernaut on 2007-07-12
My system tray says there are 11 updates available. In synaptic it states they relate to open office core etc etc 
I get a message updating 9 of 11 packages then get an error 
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.2.0-1ubuntu4_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.2.0-1ubuntu4_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.2.0-1ubuntu4_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.2.0-1ubuntu4_all.deb)
  404 Not Found


 Is the update site down????

---

### Post by spd106 on 2007-07-12
The au mirror might not have fully sync'ed yet. Either try again later or switch to the main repo, that can be done via a selection box in Synaptic.

---

### Post by rovernaut on 2007-07-12
> **spd106 said:**
> The au mirror might not have fully sync'ed yet. Either try again later or switch to the main repo, that can be done via a selection box in Synaptic.
Thanx, I give it a couple more days.

---

### Post by rovernaut on 2007-07-12
> **spd106 said:**
> The au mirror might not have fully sync'ed yet. Either try again later or switch to the main repo, that can be done via a selection box in Synaptic.
Still not working.
 sorry where/how  do I change to main repo?

---

### Post by spd106 on 2007-07-13
Open System -> Admin -> Synaptic.

Then go to Settings -> Repositories

Change "Download from" to Main server.

Click on Close and then Reload.

I'm surprised that no-one else is having this problem. It should affect more then just one person. That suggests the problem may lie elsewhere.

---

### Post by rovernaut on 2007-07-13
> **spd106 said:**
> Open System -> Admin -> Synaptic.

Then go to Settings -> Repositories

Change "Download from" to Main server.

Click on Close and then Reload.

I'm surprised that no-one else is having this problem. It should affect more then just one person. That suggests the problem may lie elsewhere.
I'm using KDE, maybe it's different than Gnome. as I don't seem to have a ' Download From"

It's fixed now as the AU server must be synch'ed now.
Thanks for your help
[IMG][IMG]http://img.photobucket.com/albums/v228/Rovernaut/synaptic1.jpg[/IMG][/IMG]

---

