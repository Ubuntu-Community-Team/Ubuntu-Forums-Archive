---
title: "[SOLVED] What if your connection drops during the upgrade?"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by bw44 on 2007-11-04
I started to upgrade from Feisty to Gutsy with the Update Manager.  Everything went well until it said it was about to download 600MB and this was the point of no return (something like that). 

I canceled the upgrade because I did not know what would happen if  2 or 3 hours later my connection dropped.  Will the update process be able to resume the download, or will I have to start over?  Or, worse, will I have to reinstall manually?

Sorry if an answer to this is available in the upgrade notes or on the forums, but I couldn't find it.

Thanks.

---

### Post by Pumalite on 2007-11-04
What's the state of Synaptic or apt-get? Functioning?

---

### Post by bw44 on 2007-11-04
> **Pumalite said:**
> What's the state of Synaptic or apt-get? Functioning?

The Synaptic Package Manager is working; it shows: 21386 packages listed, 1058 installed, 0 broken, 0 to install/upgrade, 0 to remove.  As advised by the upgrade guide, I ran the update manager before clicking on "upgrade" to 7.10 and it said there were no updates available for my system.

Will this affect how the system responds if my connection drops during the download?

Thanks.

---

### Post by Pumalite on 2007-11-04
If your apt-get is working and there are no broken packages, you are probably OK. if you want to do an upgrade. I'm not sure if it will start from zero or pick up where it was.

---

### Post by mnml on 2007-11-04
since apt-get is gettin all the package before the "actual" upgrade you don't need to worry.
if your connection drop; you just resume the upgrade.

---

### Post by bw44 on 2007-11-04
> **Pumalite said:**
> If your apt-get is working and there are no broken packages, you are probably OK. if you want to do an upgrade. I'm not sure if it will start from zero or pick up where it was.

Thanks for that.  I was mostly worried that if the connection dropped I'd have Gutsy half installed and would lose all the installed apps and settings from my Feisty system.

---

### Post by bw44 on 2007-11-04
> **mnml said:**
> since apt-get is gettin all the package before the "actual" upgrade you don't need to worry.
if your connection drop; you just resume the upgrade.

Thanks for explaining why!

---

