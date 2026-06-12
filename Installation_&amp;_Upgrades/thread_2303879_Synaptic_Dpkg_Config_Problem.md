---
title: "Synaptic Dpkg Config Problem"
date: 2015-11-22
forum: Installation &amp; Upgrades
---

### Post by SpikeLS6 on 2015-11-22
Just after my successful Upgrade from 15.04 to 15.10, I went into Synaptic Manager to remove some old OS packages. Before Synaptic loads all the files it has I get an error of: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.

I tried using this instruction in Terminal, but get an error that wants me to go into dpkg help files for an answer. Why won't this command run?

---

### Post by bapoumba on 2015-11-22
Please close Synaptic and run **sudo dpkg --configure -a** and post the complete output here, thanks.

---

### Post by SpikeLS6 on 2015-11-22
"SUDO" leading the command worked. Synaptic re-configured and I was able to remove the file I no longer needed.

Thank you!

---

### Post by bapoumba on 2015-11-22
Cool, you're most welcome :)

---

