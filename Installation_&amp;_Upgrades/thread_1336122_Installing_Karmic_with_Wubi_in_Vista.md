---
title: "Installing Karmic with Wubi in Vista"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by roobee on 2009-11-24
Hi there, 
I've been running 8.10 on my Vista laptop since last year. I installed it using Wubi. 
I'd like to install Karmic now, but I'm concerned about simply hitting "uninstall" on Vista. Is that really all I have to do or should I boot into 8.10 first and delete all the files I don't want etc. I'm happy to do a completely clean install on 9.10. 

Is there a best practice way of doing this?!

Thanks very much, 
Roobee

---

### Post by darkod on 2009-11-24
Since wubi is not an actual install, there is no need to delete any files from within 8.10. Clicking the uninstall in Add/Remove Programs will delete the 8.10 "installation" which at the moment is one big file. If you open the disk where you installed it (C:, D:, E:) you will see something like Ubuntu folder with a size you dedicated to 8.10.
But do not just delete this folder, do it from Add/Remove programs like removing any windows app. It will delete the folder completely and with it all files from 8.10 and the entry for Ubuntu in the windows bootloader.

---

### Post by MelDJ on 2009-11-24
see: [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

