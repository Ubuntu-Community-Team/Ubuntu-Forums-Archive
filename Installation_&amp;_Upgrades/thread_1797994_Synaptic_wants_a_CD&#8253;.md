---
title: "Synaptic wants a CD&#8253;"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by Earl_Maroon on 2011-07-05
==Background==
The other day I dropped my laptop and the battery fell out. When I tried to reboot I got an error message immediately after Grub that I couldn't fix. So I decided to reinstall.

I didn't have an Ubuntu CD so I installed ElementaryOS and then upgraded to Ubuntu Natty. I uninstalled all of the Elementary programs I could identify and installed ubuntu-desktop and ubuntu-standard, which got me to roughly what a clean install is like (as far as I can tell).

==Problem==
Anyway, now I can't add any repositories in Synaptic. When I try I get the error message "Please insert a disc in the drive:".

Any idea how I can solve this?


Solution:
I removed Synaptic and reinstalled it and the problem was solved:
```
sudo apt-get purge synaptic && sudo apt-get autoremove --purge
sudo apt-get install synaptic
```

---

