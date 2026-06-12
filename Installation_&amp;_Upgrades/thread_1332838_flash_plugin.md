---
title: "flash plugin"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by sadeceengin on 2009-11-20
hey. i have a problem with my adobe flash player plugin. i tried to update it. it uninstalled first but couldnt install the new version. i dont know why it couldnt but problem is not that. when i tried to uninstall from the terminal, it said i cant find any archive, please reinstall flash. and i tried to install again, from the terminal; it gave the same error. i cannot find any archive please re-install it :) what can i do now? please help
thanks...

---

### Post by Lofnes on 2009-11-20
> **sadeceengin said:**
> hey. i have a problem with my adobe flash player plugin. i tried to update it. it uninstalled first but couldnt install the new version. i dont know why it couldnt but problem is not that. when i tried to uninstall from the terminal, it said i cant find any archive, please reinstall flash. and i tried to install again, from the terminal; it gave the same error. i cannot find any archive please re-install it :) what can i do now? please help
thanks...
 
i am very new to Ubuntu and have this exact problem. Not only can I not install flash but no other programmes can be installed because of this error. I can neither install nor update

---

### Post by sadeceengin on 2009-11-21
could someone please solve this problem? i cannot install or delete anything connected with flash :icon_frown:

---

### Post by sadeceengin on 2009-11-21
ok i solved this problem.
i used some codes in terminal but cant help more than this because i used someoneelse's  help.

**cd /var/lib/dpkg**
**sudo cp available available.bad**
**sudo cp status status.bad**
**gksudo gedit available**

after these i reinstalled it;
**sudo apt-get --reinstall install**

if an error occurs try
**apt-get autoremove**   or **sudo apt-get autoremov**e

then install adobe flash again if u downloaded. if not, 
**apt-get install adobe-flashplugin**

---

### Post by cucheme09 on 2009-11-21
> **sadeceengin said:**
> ok i solved this problem.
i used some codes in terminal but cant help more than this because i used someoneelse's  help.

**cd /var/lib/dpkg**
**sudo cp available available.bad**
**sudo cp status status.bad**
**gksudo gedit available**

after these i reinstalled it;
**sudo apt-get --reinstall install**

if an error occurs try
**apt-get autoremove**   or **sudo apt-get autoremov**e

then install adobe flash again if u downloaded. if not, 
**apt-get install adobe-flashplugin**

What did you do after '**gksudo gedit available'** did you delete the flash section in the file or did you do something else or nothing
thanks

---

### Post by sadeceengin on 2009-11-22
i tried to reinstall; if no error occurs; flash will be installed. but some error occured on my plugin. so i removed it and installed again. i dont know much about that,  i used help as i said above. but the guy that helped me told we'd delete and reinstall it in a different way. coz the other ways ( apt-get remove  or  purge)  did not work.

---

