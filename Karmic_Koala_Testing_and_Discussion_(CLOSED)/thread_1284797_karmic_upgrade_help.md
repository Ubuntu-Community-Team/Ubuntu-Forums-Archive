---
title: "karmic upgrade help"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by skakid177 on 2009-10-07
i just upgraded kubuntu 9.04 to 9.10 using update-manager -d and it went through the installation with no problems but when i restarted it loaded but it didnt. it seems loaded but the screens completely black. if i press alt+f2 i can open files and i have a cursor but thats it. and for some reason when it loads it shows the new splash screen then reverts back to the old one to finish loading. please help me id like to use my computer again :(

---

### Post by rex4u on 2009-10-07
Hi,

Try this it might help you...
ctrl+alt+f1
sudo apt-get update

Good luck...

---

### Post by Blackwolf_Oz on 2009-10-07
Think you might have warned this person, that issuing ctrl+alt+f1, was going to log him out ? Seems slightly irresponsible in my book. More experienced users may know but your answer was of no help.

---

### Post by masux594 on 2009-10-07
Have u reinstalled your graphic drivers? Maybe that during the upgrade something messed-up the drivers.. 

Sysc, A

---

### Post by Nickedynick on 2009-10-07
> **legend1264 said:**
> Think you might have warned this person, that issuing ctrl+alt+f1, was going to log him out ? Seems slightly irresponsible in my book. More experienced users may know but your answer was of no help.

Ctrl+Alt+F1 doesn't log you out, it switches to a terminal. You can go back to where you were by using Ctrl+Alt+F7.

---

### Post by skakid177 on 2009-10-07
either way it just made my problem worse. i just installed it from scratch and it works fine, now just the usual problems trying to get flash to work

---

### Post by masux594 on 2009-10-07
Easy man =) ```
sudo apt-get install flashplugin-installer flashplugin-nonfree 
```.. that worked for me!

Sysc, A

---

