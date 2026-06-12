---
title: "Enhanced postscript files not printing"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by tamalbasak on 2011-04-29
I use a Dual core desktop PC with ***Ubuntu 10.10***. A **hp-laser- jet 4250** printer is connected to it. I am getting able to print all files except **.ps** and **.eps** files. When I send a** .ps** or **.eps **file for printing, no job is actually reaching to printer. Please help.

---

### Post by dino99 on 2011-04-29
into a terminal, copy/paste these commands one by one then hit Enter

sudo apt-get update
sudo apt-get install -f

sudo apt-get install psfontmgr
sudo apt-get install ghostscript

sudo dpkg --configure -a

---

### Post by tamalbasak on 2011-05-02
Thanks a lot dino99. Its working.

---

### Post by tamalbasak on 2011-05-27
sudo apt-get update
sudo apt-get install -f

sudo apt-get install psfontmgr
sudo apt-get install ghostscript

sudo dpkg --configure -a


these suggestion was working for some days for .eps file printing. but now again this eps is not printing again, even after running these above mentioned commands. please help.

---

