---
title: "Uninstall WUBI from Win XP - error when re-booting"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by Pallkrin on 2009-12-18
Uninstall WUBI Ubuntu from your Win XP - not at all as simple as it can be!
 
When you have uninstalled WUBI from your Win XP, you will probably still see the multiboot option between Win Xp and Ubuntu, the next time you boot the PC. 
 
That is because the WUBI installer changes the boot.ini file near the root of (typically) the C drive on your PC. 
 
Solution: find the boot.ini file and open it. The last line of text in the boot.ini file contains the folowing:
 
C:\wubildr.mbr = "ubuntu"
 
Delete this line. (IMPORTANT: delete nothing else!)
 
If the boot.ini file is protected, after deleting the above mentioned line of text, save it (save as) on the desktop. Then delete the boot.ini file from your C-drive and copy/paste the new one from your desktop and back to the root of the C drive.
 
Then restart your PC - and Ubuntu are gone.
 
/Pallkrin

---

### Post by mikewhatever on 2009-12-18
Thanks for pointing out how to get rid of wubi's boot .ini entry, however, a multiboot menu is not an error. Did you get other errors when rebooting?

---

### Post by Pallkrin on 2009-12-18
> **mikewhatever said:**
> Thanks for pointing out how to get rid of wubi's boot .ini entry, however, a multiboot menu is not an error. Did you get other errors when rebooting?
 
Thanks,
 
Agree - perhaps it is not an error from the perspective of more skilled Ubuntu-people, but it is still annoying, and as new Ubuntu user, it was unpleasant.
 
No other "errors" was seen btw.
 
/Pallkrin

---

