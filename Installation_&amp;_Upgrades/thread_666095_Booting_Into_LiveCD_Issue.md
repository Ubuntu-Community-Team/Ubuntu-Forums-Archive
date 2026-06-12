---
title: "Booting Into LiveCD Issue"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by ArchCorsair on 2008-01-13
I'm having an issue booting into LiveCD

i use these parameters to start
```
noapic nolapic irqpoll noirqdebug
```

then when it gets to the point where it "freezes" i press alt+f4 and enter the following:
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo startx
```

then i get fatal error:
```
Fatal Server Error:
no screens found
```

any ideas?

PS: My monitor is a **Samsung SyncMaster 2232bw**

[B]My Machine:

_specs_
Q6600 Quadcore
Gigabyte P35-DS4
4GB RAM
8800 GTS G92 512mb[/B]

---

### Post by PmDematagoda on 2008-01-13
With your PC, I believe you will have to install Ubuntu using the Alternate CD.
The Alternate CD can be obtained from [here]("http://www.ubuntu.com/getubuntu/download"), check the check box near the end of the web page that will allow you to download the Alternate CD.

After Ubuntu is installed, you can then setup your graphics.

---

### Post by ArchCorsair on 2008-01-13
I am not trying to install ubuntu at this moment, I only need to access LiveCD  session

**Edit:** Alternative CD does not contain Live session

---

### Post by [MoG] Didier on 2008-01-16
ArchCorsair,

     You and I are having similar problems. I haven't gotten to the No screens found issue yet but the ubuntu livecd keeps booting straight to a black screen for me right after I tell it to start. You and I have practically the same setup too. 

Intel Q6600 2.4ghz Quad CPU
4gb Corsair XMS-2 RAM
MSI P6N Diamond Board
2x G92 8800gts with SLI connector on.

I'll be keeping an eye on this thread.

---

