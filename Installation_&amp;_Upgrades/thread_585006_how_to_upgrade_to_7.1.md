---
title: "how to upgrade to 7.1"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by jackmg on 2007-10-21
Can I install Ubuntu 7.1 directly over the existing 6.0 isntallation on the hard drive? Will the process overwrite all of my existing files? From what I understand of the process, from the live CD I can install onto the hard drive. But then I will have to reisntall all the programs I have added such as Google Sky, Picasa, and all of my stored photos and other documetns. Is this correct?

Thanks for the help.

---

### Post by Pumalite on 2007-10-21
Save /home and data, then install

---

### Post by logos34 on 2007-10-21
Yes, it will overwrite everything on root partition. 

Like pumalite says, back up your /home directory. (Unless you have it on a separate partition, in which case its safe).

Picasa is usually in /opt (settings in /home/.picasa).  

You can generate a list of all installed packages, then use it to fetch the gutsy versions after installation.

dpkg --get-selections > dpkgs_installed_list

then reverse it to install on gutsy:

dpkg --get-selections < dpkgs_installed_list

---

