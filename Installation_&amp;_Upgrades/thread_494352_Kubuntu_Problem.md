---
title: "Kubuntu Problem"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by VEGAMO on 2007-07-06
ok so i've been using ubuntu Gnome for 2 days.

Now I upgraded to Kubuntu (where I have the chance to choose between KDE and Gnome)

however, since I did the upgrade i've been getting extremely slow launch time.

Like when I boot my computer, the kubuntu sign comes up, and the progress bar stops for like 3-4 minutes then it starts moving.

this is very annoying because I was happy on how fast Ubuntu loaded before, now it's slower than my windows.

is this normal?

---

### Post by dabl on 2007-07-06
I believe KDE is a bit more resource-hoggy than Gnome, but 4 minutes is a very long time -- I wonder if something else is going on.  There are some knowledgeable folks on Kubuntu Forums: [http://kubuntuforums.net](http://kubuntuforums.net)

Probably if you will boot Kubuntu, and in the konsole window run ```
top
``` it will show how the resources are being applied to the processes.  You can post the output of that on Kubuntu Forums (or here) and perhaps some kind soul will be able to perceive whether there is anything unusual going on.  It would be nice to know the CPU, RAM size:) and drive type that you're running, BTW.

---

### Post by bmorency on 2007-07-06
when you login to gnome does it still take that long to load or is it just kde?

---

### Post by VEGAMO on 2007-07-07
> **bmorency said:**
> when you login to gnome does it still take that long to load or is it just kde?

no im talking about before it gives you the choice to choose, IM talking about when it's booting up and it shows you the blue progress bar.

---

### Post by bmorency on 2007-07-07
maybe a process is making your system hang a bit. what you can try is to boot into recovery mode, as it is listing the processes it is loading you might see it stuck on a certain one. if it does get stuck you might be able to disable it and reboot.

---

