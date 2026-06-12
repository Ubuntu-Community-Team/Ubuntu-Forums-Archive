---
title: "samba insatallation problem.."
date: 2014-10-25
forum: Installation &amp; Upgrades
---

### Post by aanchal2 on 2014-10-25
I recently switched from a windows machine to an ubuntu machine and i need to transfer all my files from the old windows laptop to my new laptop with ubuntu. I tried installing samba using the following command: sudo apt-get install system-config-samba.There was a message saying package not available. i tried downloading samba from ubuntu software center but it also said, 
"There isn’t a software package called “system-config-samba” in your current software sources". Do i have to download this package.can anyone provide the download link?
Also what is the difference between the two commands?
sudo apt-get install system-config-samba
sudo apt-get install samba
And if i incorrectly installed any software how do i uninstall it?

---

### Post by mikewhatever on 2014-10-25
You may want to update the package info first with <sudo apt-get update>.

System-config-samba is a GUI tool (frontend) for configuring Samba. [http://packages.ubuntu.com/trusty/system-config-samba](http://packages.ubuntu.com/trusty/system-config-samba)
Samba is the backend service that makes sharing and printing work.

To uninstall, run <sudo apt-get remove packagename>

---

### Post by aanchal2 on 2014-10-28
i downloaded the package but what do i do now?

---

