---
title: "Su does not authenticate"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by erik33045 on 2008-06-05
When i am using terminal and i get asked to put in the su password, i put in the correct one and it says authentication failure. My password works for the packet manager and all the other admin tools just not terminal. Anyone have a clue on how to fix this? I am the admin on this machine just to add clarity.

---

### Post by wpshooter on 2008-06-05
Are you positive that the cap lock is not on ?

---

### Post by aysiu on 2008-06-05
*su* without any other arguments switches to the root user, and root logins are disabled by default in Ubuntu, and there's usually absolutely no reason for you to renable the root login.

Ubuntu uses *sudo* instead of root.

If you get tired of typing *sudo* ```
sudo -i
``` will give you a persistent root terminal.

More details here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

