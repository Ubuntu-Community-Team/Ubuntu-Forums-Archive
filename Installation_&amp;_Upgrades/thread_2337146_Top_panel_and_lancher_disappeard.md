---
title: "Top panel and lancher disappeard"
date: 2016-09-15
forum: Installation &amp; Upgrades
---

### Post by eda3 on 2016-09-15
Hi friends,
The top panel and launcher disappeared in Ubuntu 16.04. Control buttons (open,close) also disapeard. 
I can access the terminal from desktop.
What can i do for restore settings?
Have you ever seen this kind of problem?
Thank you.

---

### Post by patspiper on 2016-09-18
I updated yesterday my Ubuntu 16.04 and got the same symptoms: No launcher, no open/close buttons, no top bar.

The following didn't resolve the issue:
- Delete ~.config/compiz-1/compizconfig/*
- Delete ~/.config/dconf/user

The guest session works however.

I hope there is a solution to this.

CPU is skylake in case this is relevant.

---

### Post by patspiper on 2016-09-18
Solved by deleting ~/.cache

Steps:
- after booting, press Ctrl+Alt+F1 to access a terminal session
- cd /home/<username>
- mv .cache bak.cache
- rm .cache
- press Ctrl+Alt+F7 to get back to the login screen
- login and your launcher should be back
- You can delete bak.cache if you want

---

### Post by eda3 on 2016-09-24
Hello, I just seen your message and I am so glad to see.
I now solved and want to inform to the users if somebody face to face with this kind of situation.
First of all, I understood my problem related with nvidia graphic card. 
So that i decided to apply some codes than top panel and windows menus appeared but left panel lost after 1-2 second.  First codes here i applied:
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
sudo apt-get purge nvidia* bumblebee*
sudo apt-get install nvdia-prime
than top panel appeared but for luncher i opened system->software&updates->drivers->i selected apropriate and tested one than i opened again unity form terminal as write ccsm then selected hide luncher menu as newer then menü appeard. Now works very well but i dont know will be problem or not in the future because this graphic card is not developed from linux developers but as i learn tested. I hope will be help to the users. 
Thank you very much patspiper.

---

