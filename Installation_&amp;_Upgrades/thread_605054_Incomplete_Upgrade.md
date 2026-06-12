---
title: "Incomplete Upgrade"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by Adam_clmns on 2007-11-06
i have an old Toshiba Satellite with a 6GB HDD and 128MB RAM. i put Xubuntu 7.04 on it and then upgraded to 7.10. i let it upgrade over night (slow connection) and when i got up to check it it was turned off. i booted it up and it booted fine, but the resolution is lower than before and i can't change it back, and the synaptic Package Manager and the Update manager will not open, the error message says

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

I'm kind of a newb with Ubuntu, so please be kind. any assistance would be much appreciated. 

-Clemonsa

---

### Post by Pumalite on 2007-11-06
Run:

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by Adam_clmns on 2007-11-07
didn't work. when i run the "sudo dpkg --configure -a" it runs for about two hours and ends syaing it had trouble with some of the files, then i run the "...get update" and it goes for a few hours (don't know how many, let it run over night) and it freezes  and dies. i'm going to upgrade the harddrive so i'll just reinstall. thanks anyways.

-Adam_clmns

---

### Post by Pumalite on 2007-11-07
Better save /home and data and do a clean install.

---

