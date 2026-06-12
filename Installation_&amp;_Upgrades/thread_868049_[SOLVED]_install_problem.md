---
title: "[SOLVED] install problem"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by mikedemario17 on 2008-07-23
when i try to install anything it always says----> > only one software management tool is allowed to run at the same time.... i don't have any thing else running on the PC so y this happening? and i turned off my PC and i tried to install lime wire (not frost wire) right when i started the PC and it said the same error...same for aim or anything else...:confused:

---

### Post by Partyboi2 on 2008-07-23
System - Administration - System Monitor and check that there are no package managers running. If there is one running highlight it and right click and choose "Kill process"
If there are no package managers running then try in a terminal (Applications>accessories>terminal)
```
sudo dpkg --configure -a
```  If that does not work you may need to remove the lock file. But hopefully one of the above 2 will work.

---

### Post by mikedemario17 on 2008-07-24
yeah i endded up just installing 7.10 and every thing workes just fine and i have no problems now....thanks anyways

---

