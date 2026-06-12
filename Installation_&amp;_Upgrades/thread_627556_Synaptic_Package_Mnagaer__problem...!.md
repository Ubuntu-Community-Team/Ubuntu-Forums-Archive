---
title: "Synaptic Package Mnagaer  problem...!"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by Biggy on 2007-11-30
i try to open Sunaptic Package Manager  and give this error :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


what can i do ?

help....!

---

### Post by Pumalite on 2007-11-30
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by Biggy on 2007-11-30
thank you ..... :)

---

### Post by panaretos22 on 2007-11-30
thanx i had the same problem but now is fixed . the only problem it\s when i am runnign the comand sudo apt-get  upgrade it telling me that i dont have root permisions

---

### Post by Biggy on 2007-11-30
instert Gutsy cd and try again.....work for me.

---

