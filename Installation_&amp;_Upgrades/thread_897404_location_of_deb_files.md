---
title: "location of deb files"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2008-08-22
Hi,


In ubuntu 6.06 dapper after installing a program all the deb files are found in /var/cache/apt/archives, but in ubuntu 8.04 hardy, i am not finding any deb files here.

Is it stored in a different location ..???

---

### Post by Herman on 2008-08-22
My .deb files are all stored in /var/cache/apt/archives, I just checked. 
The only way I can think of to cause them to vanish is to type 'sudo apt-get clean'.
You haven't used the 'sudo apt-get clean' command recently have you?

---

### Post by DavidTangye on 2008-08-22
Start Synaptic, go to the Preferences, and in the Files tab I think you will see that the .debs are set to be deleted on install. Change this option to what you want.

---

