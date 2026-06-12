---
title: "Spoiled installation"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by gasull on 2007-02-21
Hi.

It seems that I spoiled my Ubuntu Edgy.  I tried to install Folding@Home with checkinstall, it failed, and then I dpkg'd -i it.  dpkg showed a message saying that it couldn't delete /home/gasull (my user home) because it wasn't empty.  Then I tried to use sudo and it said the uid didn't exist.

I rebooted my laptop, and I got a blue and gray screen showing this message: "The GDM user 'gdm' does not exist.  Please correct GDM configuration and restart GDM".  Then I get a login screen, but my user doesn't exist anymore.

I thought about using [SystemRescueCd]("http://www.sysresccd.org/Main_Page") but I don't know exactly what to do.

Please help.

---

### Post by zvacet on 2007-02-21
I don´t know why,bit it seems you deleted your home/user folder.On login screen in sessions choose sefe gnome,and little terminal will pop up.Go to your home folder and
```
mkdir user
```

---

