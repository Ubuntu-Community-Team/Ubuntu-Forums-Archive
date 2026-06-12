---
title: "No video after initial boot of Ubuntu 7.04"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by Puffball on 2007-04-26
I installed Ubuntu using the alternative ISO (the live cd never worked on my computer), and during the first boot up I saw the boot splash for a minute and then the screen goes blank; my monitor is then on for a few seconds until powering off. The video card I'm using is a Radeon 9250 and every other OS I've ever installed didn't have video issues. Afterwards, I tried installing 6.06 in hopes I could upgrade to Feisty, but then the video died again. Any ideas?

Thanks.

---

### Post by zvacet on 2007-04-27
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by Puffball on 2007-04-27
That talks about starting xorg from the command prompt, but I don't even get the command prompt either, let alone a video signal.

---

### Post by Acidictadpole on 2007-04-27
I'm kind of having the same problem. But i get as far as making a selection with the livecd (start or install ubuntu) and a little bit of loading before my screen does the same thing.


I have a radeon x800xl hopefully it's not an ATI deal ;/

---

### Post by jeff_hanna on 2007-05-03
> **Puffball said:**
> I installed Ubuntu using the alternative ISO (the live cd never worked on my computer), and during the first boot up I saw the boot splash for a minute and then the screen goes blank; my monitor is then on for a few seconds until powering off. The video card I'm using is a Radeon 9250 and every other OS I've ever installed didn't have video issues. Afterwards, I tried installing 6.06 in hopes I could upgrade to Feisty, but then the video died again. Any ideas?

Thanks.

I have the exact same problem. I tried installing from the regular CD, but after the text based menu screen Ubuntu would load and then my monitor would go black and eventually go in to sleep mode. I used the text-based installer on the alt CD and the installation worked without any probems. Now, though, when I boot Ubuntu I get the Ubuntu loading screen (logo and the thermometer bar) and then my monitor goes black, the drumbeat startup sound plays, and then my monitor goes in to sleep mode.

Intel Core 2 Duo (2.4GHz), 2 GBs ram, ATI X1900XT (PCI-E) 512MBs.

I know there are issues getting either the OSS or ATI enhanced driver installed. All of the documentation about that assumes you are starting from a working graphical Ubuntu desktop. I can't even get there. How can I fix this issue? Any help would be greatly appreciated.

---

### Post by Puffball on 2007-05-08
Whats also weird is a year ago, on the same exact hardware, Ubuntu 6.06 installed fine - the fglrx drivers worked and I even got XGL working. I'm using a Soyo KT400 chipset/Athlon XP 3000+/1.75 GB DDR - I guess whatever ati drivers used by default are causing the problem.

---

### Post by Topsiho on 2007-05-08
Did you try the recovery mode when booting the computer? That way you get into a text screen as root, and can do all things necessary to repair.

Seems to me that your xorg needs some twiddling, what exactly I do not know however. Sorry for that.

Topsiho

---

