---
title: "edgy to feisty upgrade"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by STREETURCHINE on 2007-04-26
i upgraded to feisty but i am now stuck ,when feisty loads it only takes me to the command line 
(the black screen with the white writing)
i can then login there and type startx and i go as far as the grey screen with the curser sitting there

i have tried
sudo aptitude install ubuntu desktop
sudo dpkg-reconfigure xserver-xorg
sudo dpkg-reconfigure -phigh xserver-xorg

none of these have solved this issue,

any body know where i go from here.

i used the official upgrde method

---

### Post by zvacet on 2007-04-26
```
sudo /etc/init.d/gdm start
```

---

### Post by STREETURCHINE on 2007-04-26
> **zvacet said:**
> ```
sudo /etc/init.d/gdm start
```

thanks we have now progressed,

i get to the boot screen enter username and password ,the screen now hangs at the the reddy browny screen and goes no further

---

### Post by zvacet on 2007-04-27
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by STREETURCHINE on 2007-04-27
thanks for your help,but i have read that page still hanging, i think i will wait for my dvd to arrive and try a fresh install.

---

### Post by eduardoeltortuga on 2007-04-27
Same problem with my upgrade. Every time I've installed  ubuntu the gui has always been a pain in the ****. I'm going to bed. Try again in the morning
     

                              Ubuntu to all, and to all a good night:(

---

