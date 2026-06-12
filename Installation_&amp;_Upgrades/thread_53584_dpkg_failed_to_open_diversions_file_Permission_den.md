---
title: "dpkg: failed to open diversions file: Permission denied"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by mjrmua on 2005-08-01
I've installed without any problem, but when I try to install new packages, I get this error:

dpkg: failed to open diversions file: Permission denied

Any suggestions?

---

### Post by adwait on 2005-08-01
Are you using sudo?

---

### Post by mjrmua on 2005-08-01
yes, starting through default gnome menu.

It seems that root does not have permission to access /var/lib/dpkg/diversions file,  but I can't chmod it (permission denied)

---

### Post by az on 2005-08-01
Did you do anything "funny" to you system or did you just use tha GUI tols provided?

What happens when you type
sudo apt-get update

from the command line?

---

