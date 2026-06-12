---
title: "Boot Program"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by Captain_MDS on 2010-02-18
I tried to boot from CD for demo mode (9.10) but my XP machine wouldn't do it. I opened CD from My Computer and a selection window opened. Choices were to reboot to demo, Install to Windows or Help with Boot. I selected Help with Boot and a boot program was downloaded and installed (I think to drive C: (XP)). When I restarted, a new boot window opened giving me a choice to boot to XP or Ubuntu (9.10) and I chose Ubuntu. Instead of opening for demo it went to full install and I aborted the procedure, went to add/remove programs and uninstalled Ubuntu.  Now when I restart I still get the boot selection window,  Any suggestions as how to remove the boot program? Can't find it. 
Sorry for the long question, new to this.
Thanks, Captain_MDS

---

### Post by darkod on 2010-02-18
For XP open C:\boot.ini (it's probably a hidden file) and delete the line relating to ubuntu/boot program, etc.

Just MAKE SURE you don't delete your XP line!!! Save and close the file. Reboot.

---

### Post by Captain_MDS on 2010-02-18
Thanks for your advice....
Captain_MDS

---

