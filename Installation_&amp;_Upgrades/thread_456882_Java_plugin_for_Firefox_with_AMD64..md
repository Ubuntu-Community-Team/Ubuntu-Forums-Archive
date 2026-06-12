---
title: "Java plugin for Firefox with AMD64."
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Chris_no on 2007-05-28
Is it really so that there is no 64bit java plugin for Firefox?

Here is what I've got so far.

--------------------------------------------

sudo apt-get install sun-java6-plugin

sun-java6-plugin not available.

---------------------------------------------

sudo aptitude install sun-java6-plugin

sun-java6-plugin not available.

----------------------------------------------

sudo dpkg -i sun-java6-plugin_6-00-2_i386.deb

wrong arcitechture.

-----------------------------------------------

Is there another way short of writing the thing myself?

Or do I just have to wait for sun?

Chris

---

### Post by Chris_no on 2007-05-28
sudo dpkg -i --force-all sun-java6-plugin_6-00-2_i386.deb

Firefox flash broke...

---

### Post by Chris_no on 2007-05-28
sudo aptitude install j2re1.4 j2re1.4-mozilla-plugin

Firefox now has java installed, but when I tried to use a java app it crashed.

By the way the place I'm trying to start is Pacificpokers quick play no download.

[www.pacificpoker.com](www.pacificpoker.com)

---

### Post by Kilz on 2007-05-28
There is **no** and I repeat **no** java plugin for the amd64bit version using the 64bit browser that is in synaptic, that works for all sites. Forcing in the java from the i386 will not work, its a 32bit plugin that will not work with the 64bit browser.
Even the install script for a 32bit browser I have written will not work on all sites, partypoker is one of them

---

### Post by Chris_no on 2007-05-28
Thanks for making that clear Kilz.

Sun better get moving. I wanna play! :(

---

