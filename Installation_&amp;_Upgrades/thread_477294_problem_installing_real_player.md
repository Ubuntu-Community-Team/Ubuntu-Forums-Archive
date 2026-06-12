---
title: "problem installing real player"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by Saptagirish on 2007-06-18
HI! I am new to Ubuntu and have just recently installed it on my computer.
I tried to install Realplayer and downloaded the .bin file and after downloading to my desktop ran the commands " chmod a+x RealPlayer10Gold.bin" but I keep getting this message" chmod: cannot access `realplayer10gold.bin': No such file or directory"
How do I go about with the installation.

---

### Post by tgoose on 2007-06-18
Try ```
cd Desktop
``` first, that might work.

---

### Post by 00arthuryu on 2007-06-19
Realplayer screws up my sound on my ubuntu and i needed to reinstall it,
and plus the sound realplayer has is very jolty
this might be a problem on my behalf, but i'm just trying to raise concern :)

---

### Post by arakali on 2007-06-27
> **Saptagirish said:**
> HI! I am new to Ubuntu and have just recently installed it on my computer.
I tried to install Realplayer and downloaded the .bin file and after downloading to my desktop ran the commands " chmod a+x RealPlayer10Gold.bin" but I keep getting this message" chmod: cannot access `realplayer10gold.bin': No such file or directory"
How do I go about with the installation.

Hey, I get the exact same problem with RealPlayer. Even after "cd Desktop".
Please help.

---

### Post by tgoose on 2007-06-30
Capitalisation matters, so if the file is called "RealPlayer...", it won't be recognised by "realplayer..."

If you simply type ```
chmod a+x Re
```
then the terminal will autocomplete the rest of it, so long as it's the only file in the folder that begins "Re". That's not only faster, but it also prevents any typo, and means that if Real have changed the filename since the tutorial (for example if they came out with RealPlayer 11) you won't run into problems.

---

### Post by weblordpepe on 2007-06-30
Or you could find it in Nautilus, and use the GUI to change the permissions.
Find the file, right click, go to permissions.
There is a tick-box for 'Execute'.
Tick the one thats next to your username.
Then you will be able to run it by typing ./filename in the terminal.

---

