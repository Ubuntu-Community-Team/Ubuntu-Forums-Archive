---
title: "Facing problme installing"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by $pinner on 2008-01-24
Hello, 

  I recently downloaded Ubuntu from Ubuntu Torrent. After completing downloading i then burned the same rar file to a CD. I burned the CD at 8x (which was the minimum). After burning i tried it on my computer but it was not working. Like i was able to Boot and see the Ubuntu option screen where i am given option to select ( like .. Start and Install Ubuntu etc etc etc) I selected first and then it start loading. It loaded well till the Loading screen ( Like Ubuntu was written above and below was a loading screen). After that loading i get a blank screen and then nothing comes. I kept waiting for 1 hour but nothing happened. I tried this 2-3 times from 4 different CD's but still i am facing the same problem. Like i am also getting this problem on my laptop. 

Can any one suggest me a solution to this problem. 

Regards,
Amrit

---

### Post by zvacet on 2008-01-24
When you boot select recovery mode from grub(place wich show you wich OS you can boot on) and type

```
dpkg-reconfigure xserver-xorg
```

When you come to drivers section select vesa and continue to the end.When you are finish type startx and that should give you basic graphic.After that go and search driver for your card.I think you will find it undet system>administration>restricted drivers mnager(or something similar because I don´t use english version).

---

### Post by $pinner on 2008-01-30
This solution is not helping me out. 

Let me explain this thing again. 

I presently have Window XP but i have disabled my HDD so that i can boot from the Ubuntu CD.  But when i select the Install Ubuntu (1 option) my screen turns blank and after that nothing come for a long time. What shall i do now and the same thing happens with my Laptop.

---

### Post by zvacet on 2008-01-30
Sorry for misunderstanding.When you boot CD  on the bottom you will see F1-F6 buttons.Press F1(it is help) and find something about graphic(safe graphic mode I think) and try with it.

---

### Post by $pinner on 2008-02-09
i tried. it.. i have tried booting from the safe graphical mode. I have tried help ... but nothing is helping me out.. 

What can be the possible problem..

---

### Post by Partyboi2 on 2008-02-09
When you downloaded the iso did you check the [md5sum?]("https://help.ubuntu.com/community/HowToMD5SUM") Also when you boot it at the main menu  choose "check the cd for defects" if you have not already done so.

---

