---
title: "Add/Remove Progams doesn't work"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by justins92 on 2008-05-21
Okay folks:

I'm relatively new to Linux so I'm going to sound like a noob here. Anyways, I was running an update, when my power cut out on me... now I can't run anything that installs programs or anything close. I've tried installing things in terminal and all that good crap... hell even pressing the button doesn't work.... I keep getting a terminal message that keeps saying:
 
            E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem, I do that and it does nothing except say it requires superuser privelelge... now, I'm the only one on this computer and I'm the only user created... how do I become a super user?

---

### Post by Pumalite on 2008-05-21
Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
(one command at the time)

---

### Post by justins92 on 2008-05-21
Thanks, for some reason all of a sudden the first command started working... how long should it take?

---

### Post by Pumalite on 2008-05-21
Usually a few seconds.

---

