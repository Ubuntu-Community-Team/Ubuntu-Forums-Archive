---
title: "Did Ctrl+c by mistake while in update manager installs. How to fix ?"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2010-07-29
While running the update manager, I wanted to copy/paste a message so I did ctrl+c (thinking copy) but I soon realized it did a stop in the update it was doing (totem-mozilla update). 

How do I fix this ? I haven't rebooted.

I am not sure anymore that it proceeded with the rest of the updates.

---

### Post by quixote on 2010-07-30
It was smart not to reboot.  Try running```
sudo dpkg --configure -a
```in a terminal to fix anything that might have broken, and then run update-manager again.  It should pick up where it was interrupted.

---

