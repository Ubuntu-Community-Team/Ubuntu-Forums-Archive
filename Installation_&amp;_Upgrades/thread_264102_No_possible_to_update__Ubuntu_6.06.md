---
title: "No possible to update  Ubuntu 6.06"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by aabento on 2006-09-24
Hi


During a session of updates the computer blocked and I had to 
force the reboot. :| 
Now there are updates to make but I always get the following message:



""""Only one software management tool is allowed to run at same time
Please close the other application e.g. "Aptitude" or "Synaptic" """"



Will be able anybody to help me to understand and to solve this problem? [-o<


Thanks
Arnaldo

---

### Post by angkor on 2006-09-24
Make sure you're not running two package management tools at the same time, for example the Update Manager and Synaptic.

Log out and log back in and open Synaptic and try again.

---

### Post by aabento on 2006-09-24
dpkg --configure -a

After did this it solve my update problem. Now everything is ok.:D 

Thanks
Arnaldo

---

### Post by Neobuntu on 2006-09-24
Me too, 

sudo apt-get install -f 

...(for Fix) worked for me. Then do your upgrades.

Paste it in and see. Looks like an impotant Firefox update was needed too!

---

