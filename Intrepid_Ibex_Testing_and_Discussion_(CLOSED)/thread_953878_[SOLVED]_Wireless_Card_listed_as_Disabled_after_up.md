---
title: "[SOLVED] Wireless Card listed as Disabled after update"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MTHarden on 2008-10-20
I did a fresh install on 8.10 on my computer. Wireless worked fine at first boot, but after applying 300+ updates through update manager, wireless no longer works. I'm attaching the log files that it seems others have submitted. I'm relatively new so if I've left out something please let me know.

Oh, and my wireless card is a PCI card, I think it is a linksys. in 8.04 I think I had RT61 as a driver, or somesuch.

---

### Post by psyke83 on 2008-10-20
> **MTHarden said:**
> I did a fresh install on 8.10 on my computer. Wireless worked fine at first boot, but after applying 300+ updates through update manager, wireless no longer works. I'm attaching the log files that it seems others have submitted. I'm relatively new so if I've left out something please let me know.

Oh, and my wireless card is a PCI card, I think it is a linksys. in 8.04 I think I had RT61 as a driver, or somesuch.

You possibly allowed a partial upgrade which has caused some vital packages not to be installed.

You need to update your repository lists (via ethernet if possible), then install the package "linux-firmware".

---

### Post by pbeck on 2008-10-20
This also occurred to me today during the update on my thinkpad x61. I didn't try to do the partial update, and when I have access to ethernet I'll try installing the firmware package.

---

### Post by pbeck on 2008-10-20
Installing linux-firmware did the trick for me. Back online!

---

### Post by MTHarden on 2008-10-20
I'll give it a go tomorrow if I can find a way to connect via my laptop and a crossover cable. But is there a way I can download the package elsewhere and transfer/install it via USB flash? That might be a silly question, but for networking issues it would be handy to know.

---

### Post by wwusnobrdr on 2008-10-21
Another thing you can check is see if the wireless card got disabled in the bios. That happened to me, worth a look.

---

### Post by zolookas on 2008-10-21
> **MTHarden said:**
> I'll give it a go tomorrow if I can find a way to connect via my laptop and a crossover cable. But is there a way I can download the package elsewhere and transfer/install it via USB flash? That might be a silly question, but for networking issues it would be handy to know.
You may try browsing mirrors and finding .deb packages. Try downloading .deb from here:_ [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/)_[URL="http://archive.ubuntu.com.ba/ubuntu/pool/main/l/linux-firmware/"]
[/URL]

---

### Post by MTHarden on 2008-10-22
Thanks guys! Installing the firmware fixed my problem. I did install from my USB key as well and was pleased that it worked. 

I think the problem was a partial update that I did, and even now when I go to update manager I see a lot of choices greyed out. Things like Linux-generic and ubuntu-desktop. That all seems important why might they be grey? And is it a problem? I had originally guessed it was for the reason listed as "Normal Changes of a Pre-release version of Ubuntu"

---

