---
title: "ubuntu installation(x server)"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by Phoenix_nebula on 2008-07-03
I am installing ubuntu ultimate gamers edition.

After I got a message (when I booted from ubuntu cd and clicked on start or install ubuntu) "...try using noapic..." I tried again installing ubuntu through using "noapic" it got passed the message.

THen it gave me a awesomness picture with a loading bar at the bottom, after completion of the loading bar it gave a black screen with a 2mm line at the top left corner (flickering). It flickered some 2 min then it gave me message "failed to start x server(graphical interface)" 

After you say "ok" the screen goes black with flikering line at top and you must restart.

---

### Post by brazemcee on 2008-07-03
Try the following:

startx gnome
startx gdm

Or just
startx

It happens sometimes to me and it works for me.

You've probably got a problem with KDE/Gnome.
Try reinstalling them.

---

### Post by Phoenix_nebula on 2008-07-03
where do you input the command because I didn't finish installation because of error

---

### Post by PmDematagoda on 2008-07-03
What are the specifications of your PC?

---

### Post by Phoenix_nebula on 2008-07-04
I have the following:
OS = Xp (1 partition of HD)(other partition open)
Foxconn motherboard c51xem2aa
Samsung DVD writer
Nvidia 8600gt 256 mb gddr3
160 gb HD (2 partitions)
2 gb ram ddr2 800

hope you this can help

---

### Post by PmDematagoda on 2008-07-04
Is there an entry to start Ubuntu in Safe Graphics Mode? If so, try that. Also, what version of Ubuntu Ultimate Gamers edition do you have?

---

### Post by Phoenix_nebula on 2008-07-04
Its v 1.2 ultimate gamers edition and it has x server v 7.1.1
also in safe graphics mode you must type in "noapic" otherwise you dont get farther but I don't you how to type noapic in safe graphics mode.

---

