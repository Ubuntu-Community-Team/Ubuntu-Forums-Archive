---
title: "Upgrading problem - computer keeps restarting"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by avram on 2008-07-05
Hi all, I recently installed ubuntu 7.04 and its been fine i have it on dual boot with Vista. I used the update manager and i tried to upgrade to 8.04 it all went well with no errors and then i restarted like it asked me to. When my computer boots up its all normal until ubuntu loads and it just has a little orange bar going from left to right and it continues and after a minute or so my computer restarts and it repeats... :(

anyone know whats going on? thanks for any help :)

---

### Post by Rallg on 2008-07-05
Try this: Boot to Ubuntu recovery mode. That give you a text command interface. When you get the command prompt,

sudo apt-get update && sudo apt-get dist-upgrade

That will install any updates that came around after you first did the upgrade. On rare occasions, you need to "update an update" (so to speak). Then, re-boot in the usual way.

That might not work, but it won't hurt.

---

