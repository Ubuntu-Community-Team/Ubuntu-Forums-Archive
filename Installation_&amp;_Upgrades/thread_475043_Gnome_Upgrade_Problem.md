---
title: "Gnome Upgrade Problem"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by McDorian on 2007-06-15
Hello there,

I have (nearly) completed an upgrade from Dapper to Feisty on a Compaq Presario R3000 laptop. Along the way I encountered the showstopping "tty" bug and the milder problem with nvidia drivers. Now I have kde functioning perfectly, but I can't get a gnome session. 

When I try to enter a Gnome session after the graphic login page, I just get a blue screen with nothing happening, then a light blue rectangle in the upper left hand corner. I get the feeling that it's just going to be some small adjustment in a file I never knew existed. 

I already tried sudo dpkg-reconfigure gdm, and deleting the old gnomefiles in my home directory, but the problem remains. Anyone have any ideas?

By the way, thanks for all the good advice on the forum. I was really impressed by the solution to the tty problem from DannyBoy. How the hell did you work that out? OK, best not try to answer that, I don't think I'd understand the explanation.

---

### Post by McDorian on 2007-06-19
Well all I needed to do was remove mdadm, and everything worked fine.

---

