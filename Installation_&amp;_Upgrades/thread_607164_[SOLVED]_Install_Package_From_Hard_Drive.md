---
title: "[SOLVED] Install Package From Hard Drive"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by snorkytheweasel on 2007-11-08
How do I install a package and its dependencies when those files are located on the local hard drive?

I've tried 
[LIST]
[*]Adept Installer
[*]Synaptic Package Installer
[/LIST]

GUI or command-line are both fine with me.

---

### Post by Pumalite on 2007-11-08
Give us the complete name of the file and where it is located.

---

### Post by snorkytheweasel on 2007-11-08
This worked:
[FONT="Courier New"][COLOR="black"][COLOR="Red"][B]
sudo dpkg --install webmin_1.380_all.deb[/B][/COLOR][/COLOR][/FONT]

First, I had to install the dependencies using the same process.

Let's call this one "Solved" :KS:KS:KS

---

### Post by Pumalite on 2007-11-08
Good for you!

---

### Post by ahaider on 2008-04-13
> **snorkytheweasel said:**
> This worked:
First, I had to install the dependencies using the same process.


How did u come to know of the dependencies ? Is there any command for that ?

---

