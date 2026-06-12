---
title: "Update Freeze. Ubuntu 13.10 Not starting up."
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by mofpeaches on 2013-10-17
I was updating my Ubuntu to 13.10 (from 13.04) and my computer froze while updating. Now when I start my Ubuntu up I get the login screen and when I login The screen becomes black. The computer in the login screen still recognizes itself as Ubuntu 13.04. I want to be able to use my computer because let's face it, the login screen does not help to much ;). If anyone can help thank you very much. 
-Uriel

---

### Post by zzgary on 2013-10-19
I met the same problem...and now fix it, here is what i do.

1. Though i can not see the desktop, I still can get into the console by press  Ctrl-Alt F1-F6;
2. Then I input apt-get or sth else i couldn't remember, and i get a hint that let me to input the "dpkg --configure -a", then it restore my configuration and restart my ubuntu;
3. Then you can login and see the screen, but if you lost your wifi or network then you can use your old linux-image to restore it(BY choose the advance start before the login screen, I choose the 3.8 image to restore and update again, then I got the 13.10~)~

Good Luck!
Hope helpful~

---

