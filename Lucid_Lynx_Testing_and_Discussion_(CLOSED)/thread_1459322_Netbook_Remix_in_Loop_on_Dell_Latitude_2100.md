---
title: "Netbook Remix in Loop on Dell Latitude 2100"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jpmoo on 2010-04-21
Hello, all.
 
I'd been using the Kubuntu 10.04 netbook remix without any trouble on a Dell Latitude 2100. Desktop effects were enabled, and worked just fine.
 
I wanted to give the Ubuntu 10.04 remix a shot. I installed it and updated all of the packages. The netbook restarted just fine. I installed compiz, enabled effects, and restarted.
 
Now, the netbook is caught in some kind of loop. As soon as X starts (it's set to log me in automatically), the screen flashes white every second or so. My background image appears, along with the task bar along the top of the screen. I'm prompted for my password, which I'm able to enter. Wireless appears to connect. No menus appear on the desktop, though. It's blank.
 
I broke out to the command line and uninstalled compiz-core, and the 1 or 2 associated packages. No luck, though.
 
Is there a configuration file, somewhere, that I can edit to disable desktop effects?
 
I'm new to Gnome, and it's been a while (Jaunty) since I've been an Ubuntu/Kubuntu user. Please forgive my noobiness.
 
Thanks!

---

### Post by jpmoo on 2010-04-21
The July 15, 2007 6:21 AM message here got my desktop back:
 
[http://ubuntuforums.org/archive/index.php/t-418138.html](http://ubuntuforums.org/archive/index.php/t-418138.html)
 
Basically, rm'ing a lot of config folders.
 
Question, though: does is make sense that these effects would work fine in Kubtuntu Netbook 10.04, fully updated, but not Ubuntu Netbook 10.04?

---

### Post by jpmoo on 2010-04-22
Turns out I hadn't installed all of the required packages for compiz to work in Gnome. Solved, once I went into Synaptic and installed everything!

---

