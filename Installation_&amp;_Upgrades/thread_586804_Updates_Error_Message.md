---
title: "Updates Error Message"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by Michaelin on 2007-10-22
I have an icon in the bar at the bottom of the screen (taskbar?) saying there are 35 updates available. When I try to install the updates I keep getting an error message:

E:/var/cache/apt/archives/audacious-plugins_1.3.5-3ubunt4 - i386.deb:
trying to overwrite
'/usr/lib/audacious/General/libcurl.so:
which is also in package audacious-plugins-extra.

Does anyone know what this means and what I need to do to install the updates.

Many thanks.

Michael

---

### Post by psmar on 2007-10-22
had the same problem while dealing with updates during gutsy testing. I found If I removed the audacious-plugins-extra via synaptic firs,t  then  update it would complete the dependency problem. If I remember there are some parts of the extra-plugins built into the update causing the conflict  
good luck hope this helps

---

### Post by Michaelin on 2007-10-22
Thank you. That helped a lot.

All updates now installed.

---

### Post by psmar on 2007-10-22
glad it helped,

 you might mak this as solved in case some one else is looking for the fix

---

