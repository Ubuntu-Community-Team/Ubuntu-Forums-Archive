---
title: "Reinstalling Ubuntu with already downloaded updates and packages"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by mahsheed on 2008-01-10
I am new to linux (Ubuntu 7.10) and i want to reinstall the operating system... 
Since i have already installed alot of updates and packages such as wine, compiz fusion etc i do not want to download them again inorder to have them reinstalled...
Is there any way i can backup these packages so that when i reinstall unbuntu 7.10 i can just use the backed-up file to install all that i want...

As i said im very new to linux so i would appreciate a detailed and complete answer...

---

### Post by forestpixie on 2008-01-10
I believe that you can use apton cd - install it to your existing setup - then use it to backup your apt cache

Reinstall and install aptoncd and you can use it to put back the apt cache, 

You can get it from the repos - so it's in synaptic as aptoncd - it installs so system >admin

---

### Post by K.Mandla on 2008-01-10
Or if you want something quicker, just copy the contents of /var/cache/apt/archives/ to a USB disk. Install your new system and then copy all those packages back to /var/cache/apt/archives/. Synchronize with the repositories and all your updates will be off current cached packages. Fun! :)

---

### Post by forestpixie on 2008-01-10
didn't actually know you could do that - thought it caused problems. Know that next time :)

---

