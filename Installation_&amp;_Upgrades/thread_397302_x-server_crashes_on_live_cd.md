---
title: "x-server crashes on live cd"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by Mynsc on 2007-03-30
Hello all,
  I used to run a dual boot win xp and ubuntu 6.06. all worked fine. last night i got a new video card, Geforce 7600gs 256mb AGP. So i decided to do a total fresh install and just use ubuntu no more winXP. turned my machine off installed the new card and put in the ubuntu 6.06 live cd i have used many times. when i click on the first option use/install it crashes x-server and puts me at prompt. 
  Ok then, i tried kubuntu edgy, installs fine no problems. I have tried to install ubuntu 6.06 a couple times now and it wont run the x-server. i even tried the oem install and whennit goes to start after installing it crashes the x-server.
  Now when i put my ati x1300 agp card in the machine i can install ubuntu 6.06 no problem.

Any ideas why kubuntu edgy would install fine but ubuntu 6.06 wont?

---

### Post by zvacet on 2007-03-31
Did you said that you can go to the terminal?if it is so 
```
 sudo dpkg-reconfigure xserver-xorg
```

pick **vesa **driver and try then.After you finish installation you can go for your new video card drivers. i belive it is Envy script.

---

