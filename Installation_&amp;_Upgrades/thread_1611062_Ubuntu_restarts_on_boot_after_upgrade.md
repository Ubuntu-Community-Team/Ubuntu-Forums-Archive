---
title: "Ubuntu restarts on boot after upgrade"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by Crazedpsyc on 2010-11-01
I had perfectly working lucid on my laptop (64 bit) which I installed from a live CD not wubi. I tried to upgrade with update-manager and everything looked fine until I accidentally updated compiz from the cache before everything else finished. this made compiz stop working completely, which also broke metacity. I tried to fix this with multiple things: Downgrading compiz (failed to apply changes), sudo apt-get install -f, finishing the upgrade (see the following). during the applying changes stage of the upgrade i got an error with almost every package it tried to apply (sorry I don't know what, but it said something about 'this package failed to upgrade and may be left in a broken state'. I let the upgrade finished and at the end it said 'Upgrade Finished but not all changes were successfully applied' and I shut down the computer. when I turned it back on everything looked fine until I past to the usplash screen. Then the screen went black, a bunch of error messages scrolled by too fast to read, and my system rebooted. 

I tried recovery mode and another kernel choice at grub but all did basically the same thing. Windows still works as much as it usually does but I want my ubuntu back! I am OK with doing a fresh install if I can somehow recover a small amount of my data in my home folder. If you can tell me how to get into ubuntu from windows or something that would be great but I also need to know how to decrypt my home folder (I used the encrypting option in the installer)

---

### Post by Crazedpsyc on 2010-11-02
If someone could just tell me how to decrypt my home folder? I saw the .desktop file and README.txt in place of my home folder's contents, but I read the readme and ran the .desktop last time ubuntu crashed (I was using karmic then) and nothing worked.

---

### Post by Crazedpsyc on 2010-11-03
I'll just start a new thread for how to recover from ecryptfs

---

