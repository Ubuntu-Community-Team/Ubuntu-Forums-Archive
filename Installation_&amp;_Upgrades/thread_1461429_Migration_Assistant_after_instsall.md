---
title: "Migration Assistant after instsall ?"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by Troca on 2010-04-24
Hi there all Ubuntu users. I started using ubuntu now again as my second os. when i want to do some gaming i still need windows most of the times and some windows apps i just cant find equal versions in ubuntu at least not as user friendly yet. Now my question is this. I did not migrate my music to ubuntu during the installation due to i simply forgot so is there anyway to simply relaunch just the Migration assistant ? All i want is that my music from windows appears when i go to my music folder this will also make it easier for me when i use amarok.

---

### Post by ajgreeny on 2010-04-24
There is no real need to use a Migration Assistant.

You can either just copy the files across, or make a link to the music folder in the windows partition from your music folder in Ubuntu.

The latter assumes that the windows partition is mounted at boot time, of course, and if it isn't, that is very easy to setup manually with an edit to /etc/fstab or by using ntfs-config from the repos.

---

