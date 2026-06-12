---
title: "OK i need help with my new ubuntu"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by --Blaster-- on 2007-09-23
I just installed ubuntu and i still have windows vista i was wondering how i can get a recyling bin in the desktop also how do i move around like into cubes and stuff. I also dont know what drive i am using it shows me the drives that vista uses. Can someone help me  1 more thing when i download stuff from the internet i cant install it.

---

### Post by Pumalite on 2007-09-23
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by ev5unleash1 on 2007-09-23
Ok, To get the cube effect you should have Ubuntu 7.04 Fiesty. click system on the top left corner click preferences and desktop effects. Enable them and then make sure the workspace is on cube check is checked off. Now every time you go to the next workspace is looks like it's on a cube. You can also hold control and alt on the keybored and then left click anywhere on the desktop hold everything and then move the mouse. You can have some fun with the cube effect.

---

### Post by Buffalo Soldier on 2007-09-23
> **--Blaster-- said:**
> I just installed ubuntu and i still have windows vista i was wondering how i can get a recyling bin in the desktop

Welcome to a brand new world of GNU/Linux and to your Ubuntu community. I'll try my best to avoid the terminal / command line interface (CLI), but some things are a lot easier done via CLI than GUI. So to show trash can on your desktop:[LIST=1]
[*]Open a Terminal (Applications -> Accessories -> Terminal)
[*]Type **gconf-editor**
[*]Browse to **/Apps/Nautilus/desktop** and click/check **trash_icon_visible**
[/LIST]

>  also how do i move around like into cubes and stuff. 

For that you will need to enable [Compiz Fusion]("https://help.ubuntu.com/community/CompositeManager/CompizFusion") (a composite manager). But I suggest you save this for last, until you familarized yourself in this new environment.

> I also dont know what drive i am using it shows me the drives that vista uses. 

Go to System -> Administration -> System Monitor -> (click tab) File Systems

Another cool thing you could try is the Disk Usage Analyzier. It's under Applications -> Accessories

> Can someone help me  1 more thing when i download stuff from the internet i cant install it.

Eventhough on the surface Ubuntu (GNU/Linux) might look like MS Windows (boxy windows, mouse, icons, etc etc) it's really a totally different beast with different ways of doing things, such as how it handles software installation.

I suggest you start with this excellent thread for beginners [READ FIRST prior to posting - IMPORTANT links ***PLUS INSTALL METHODS***]("http://ubuntuforums.org/showthread.php?t=232059"). It covers nearly everything you need to know. Including links to how installation works in Ubuntu:
[LIST]
[*] [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)
[*] [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[*] [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[*] [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
[*] [http://www.beginningubuntu.com/software_1.html](http://www.beginningubuntu.com/software_1.html)
[/LIST]

---

