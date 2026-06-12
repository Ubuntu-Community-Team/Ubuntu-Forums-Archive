---
title: "Cant unrar using Ark!!"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by badguyanil on 2006-12-09
Hi all, I have some downloads which are is RAR format. Not able to extract files from those using ark. Keep getting a message...

"The utility unrar is not in your PATH.

Please install it or contact your system administrator."

i did install unrar-free from adept. But still not working i !!! Kindly help.

---

### Post by aysiu on 2006-12-09
Maybe try the non-free version of unrar? ```
sudo aptitude update && sudo aptitude install unrar
```

---

### Post by badguyanil on 2006-12-09
getting the following error:

Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
"

any idea????

---

### Post by aysiu on 2006-12-09
Is it possible that you have Synaptic Package Manager, Add/Remove Programs, or Adept Package Manager open while you're trying to run that command?

---

### Post by anorexicpillow on 2006-12-10
worked for me great, thanks :D

---

