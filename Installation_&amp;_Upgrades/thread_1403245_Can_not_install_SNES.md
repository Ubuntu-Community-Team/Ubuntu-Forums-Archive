---
title: "Can not install SNES"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by rwh824 on 2010-02-10
Ok I am brand new to Ubuntu and have been struggling all day to get it to work. My main purpose is to be able to play snes on my ps3. I keep getting the error cannot find package snes9express. How do I fix this?

---

### Post by murderslastcrow on 2010-02-10
I have Karmic set up on my PS3 currently with enlightenment17, and the SNES program I have set up is snes9express- I installed it through the Ubuntu Software Center. However, to install it from a terminal, you would simply have to enter the following.

sudo apt-get install snes9express

If this doesn't work, go to synaptic and check for broken packages (that is, Edit/Fix Broken Packages). Also, running the initial update would be a very good idea if you haven't done so already.

Also, it would be helpful to search for snes9express (or just type snes) in Synaptic itself to see if you can install it from there. If you still can't see it, that would imply you might not have the main repositories properly enabled, which you can manage in Software Sources.

---

