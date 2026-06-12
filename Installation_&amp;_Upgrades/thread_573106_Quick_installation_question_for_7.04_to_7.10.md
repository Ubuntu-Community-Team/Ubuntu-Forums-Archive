---
title: "Quick installation question for 7.04 to 7.10"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by thewrinklyninja on 2007-10-11
Quick question,  rather than doing an upgrade I was thinking of doing a full clean install of 7.10. But I was hoping to keep my home directory with all my docs and cedega games installed.  IS it possiblt to do this during the install using the settings migration bit?

---

### Post by Forlong on 2007-10-11
Do you have a separate partition for /home?

Then all you need to do is choose that partition for /home in the installation process.

---

### Post by thewrinklyninja on 2007-10-12
No, my /home is on the same partition as the system.  I was wondering if it picks it up in the migration settings on the install dialogue.

---

### Post by celticbhoy on 2007-10-12
Your best bet is to back up your home directory, then do clean install, and then restore.

---

### Post by Forlong on 2007-10-12
+1 for the backup. But I recommend pulling only the configs back in you want to restore (like Firefox profile and Cedega stuff).

I don't know, frankly, if the migration manager can copy the whole home directory. I only know it checks for Firefox and Evolution.

---

