---
title: "No GUI after updates"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by linuxnewbie999 on 2008-03-12
I installed ubuntu7.10 from the live CD successfully. After my first updates( update gnome ..etc) and the system request for restart. But after booting ubuntu generic there is no GUI...... Why is it so?? Why after update Gnome the GUI disappeared...  can only Crtl+Alt+F2  text mode ...

---

### Post by NorthernLights on 2008-03-12
Hi,

I had the same problem with Hardy yesterday night (french time). I saw there was the new Gnome 2.22.20 (or something like that) released on PlanetUbuntu and updated. After reboot, no letter in any GUI, even GDM, no window title bars... I messed around trying to fix it and gave up to go to bed, thinking there might be an update to fix that in the morning. And there was. I went to text mode like you said and updated manually :

```
sudo apt-get update ; sudo apt-get upgrade
```

A few Gnome related packages updated, I rebooted, and VOILA, working again. Try the same :).

---

### Post by Peter09 on 2008-03-12
try typing 

```
startx
```

 at the command prompt.

---

### Post by linuxnewbie999 on 2008-03-14
=.=ll  I haven;t try that yet. Because I installed Fedora8 instead of ubuntu for some reason(gcc no libraries) ....

---

### Post by gtdaqua on 2008-03-14
u may have lost display after an update probably because the kernel has been updated. Everytime the kernel is updated, video drivers have to be recompiled and installed.

If its NVIDIA, take a look here:

[Gutsy Latest NVIDIA on DELL - walkthrough]("http://ubuntuforums.org/showthread.php?t=596875")

Print it for easy reference during installation.

Losing display is not a big issue, once you know what it is, that is!

---

