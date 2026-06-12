---
title: "how do I update my video card?"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by zidane1341 on 2008-09-25
i found a update for my video card. it came in a .tar.gz file. i know i gotta unzip it, but i'm not sure what to do next

---

### Post by kspncr on 2008-09-25
Are you sure it is what you think it is? What video card do you have?

---

### Post by tuxxy on 2008-09-25
I agree its best to stick with supported software and .debs however if you want to have a try then the tar.gz file you have is likely to be source code you need to compile, before you start you may need to install build essential to compile, so enter this command first in a  terminal

```
sudo apt-get install build-essential
```

Now change dir to the location of the extracted tar.gz folder, for example if on your desktop type

```
cd Desktop
```

Now configure the software

```
./configure
```

If you receive no errors from ./configure then enter

```
make
```

Finally install the software 

```
sudo make install
```

---

### Post by zidane1341 on 2008-09-26
intel gma express or somecrap, it's integrated, but I got the drivers from [http://www.intellinuxgraphics.org/](http://www.intellinuxgraphics.org/)

also, the defualt driver screws up all of my games. most of the easiest to run games are choppy and not responsive and and a upper right hand corner keeps flashing solid black.

also, when i tryed to follow your directions, tuxxy, when i type in "CD DESKTOP", then it says: bash: cd: desktop: No such file or directory

---

### Post by zidane1341 on 2008-09-26
when i tryed to follow your directions, tuxxy, when i type in "CD DESKTOP", then it says: bash: cd: desktop: No such file or directory.

also, there is a new graphic glitch. when i run a program in maxscreen, sometimes it messes up my start menu-thingy. like whatever i'm doing, it replaces the menu. even when i minimized anything. and it doesnt go away, unless i drag a window or click over it. i don't know why I have these graphical glitches. here's my PC, in case anyone was wondering:[http://support.gateway.com/s/PC/R/5107/5107nv.shtml](http://support.gateway.com/s/PC/R/5107/5107nv.shtml)

---

