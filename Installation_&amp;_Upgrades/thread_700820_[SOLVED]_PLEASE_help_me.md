---
title: "[SOLVED] PLEASE help me"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by bvav22 on 2008-02-18
alright im on my second fresh install of gutsy, first time ubuntu user btw. i am trying to get my ati drivers to work, but its just not coming. i cannot just install the ubuntu ones because i cannot satisfy the dependency for libstdc++5. so i downloaded them fresh from ati, and used their auto installer, which worked, but glxgears is now reading a slower fps (went from 830, to 740). 


i want to try the envy install, but i don't know how to remove the drivers i just installed, AND i cant satisfy another dependency for envy - dh-make.......

---

### Post by Partyboi2 on 2008-02-18
I think envy gives you the option to uninstall your current driver.

---

### Post by bvav22 on 2008-02-18
envy won't install.... it has dependencies that it cannot meet.

---

### Post by bvav22 on 2008-02-18
well i got lucky and figured it out, only by chance tho. i tried this once article once 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a)

and it didnt work, however the second time it FINALLY installed the libstdc++5 and i was able to install the ubuntu drivers :guitar:


just if anyone has that problem, be sure to make sure u follow the instructions for the right release that you have.

---

