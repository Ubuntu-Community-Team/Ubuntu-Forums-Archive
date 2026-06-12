---
title: "how to install opengl?"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by kDDs on 2007-09-15
can someone please give me instructions on installing opengl? im running ubuntu ultimate 1.4 thanks

---

### Post by Sockerdrickan on 2007-09-15
One does not install OpenGL, it comes with gpu drivers

---

### Post by kDDs on 2007-09-15
ok i have built in graphics though... ie on my asus p5s800-vm... anyway i can install it?

---

### Post by Sockerdrickan on 2007-09-15
If you can install drivers? You already have 2d support since you can see this. But if you want 3D then you might need proprietary drivers, is it a GeForce or AMD/ATi chip?

---

### Post by kDDs on 2007-09-15
SIS.... already tried there site and they support red-hat linux but i dnt think ubuntu....

---

### Post by Sockerdrickan on 2007-09-15
It's all the same :] check synaptic for "sis xorg"

---

### Post by kDDs on 2007-09-15
didnt find anything..... 

apart from X.org X Server -- SIS display driver but its already installed

---

### Post by t3hi3x on 2007-09-15
FYI your vid card is SiS661FX

Just a little tid bit: even if you have a an integrated gfx card, it's still a dedicated gfx card, it just happens to soldered to the board. it may share system ram, but it still has a processor for processing graphics. 

go to the packet manager and type in sis in and see if any of those packets work.

---

### Post by kDDs on 2007-09-16
ok i'll have a look... should hopefully be getting a new card soon, not an amzing one but and ok one lol

---

### Post by kDDs on 2007-09-16
ok i looked and couldnt find anything!

---

### Post by t3hi3x on 2007-09-19
post your xorg file

---

### Post by WakkaDojo on 2007-09-19
Well Linux doesn't have "OpenGL" directly, but all of the libraries are in the mesa package: [http://www.mesa3d.org/](http://www.mesa3d.org/)

If you have an i386 processor and have Feisty Fawn, try installing this build:
[https://launchpad.net/ubuntu/+source/mesa/6.5.2-3ubuntu7/+build/315525](https://launchpad.net/ubuntu/+source/mesa/6.5.2-3ubuntu7/+build/315525)

I think if you click on the "Resulting Binaries" tab on the left it will give you links to binary installs. Also, you can go to the home page (mesa3d.org) and build it yourself.

---

