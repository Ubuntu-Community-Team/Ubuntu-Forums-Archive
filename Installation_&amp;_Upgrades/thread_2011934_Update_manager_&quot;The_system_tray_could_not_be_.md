---
title: "Update manager: &quot;The system tray could not be found on this system. Closing Update .."
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by KarelWullaert on 2012-06-28
Update manager: "The system tray could not be found on this system. Closing Update monitor service"
I get this message when I startup Ubuntu.
Any body any Idea?
Karel

---

### Post by dino99 on 2012-06-28
open a terminal and run:

sudo apt-get purge ubuntu-desktop
sudo apt-get purge update-manager
sudo apt-get install synaptic
sudo synaptic

note: update-manager is too buggy, better to use synaptic

---

