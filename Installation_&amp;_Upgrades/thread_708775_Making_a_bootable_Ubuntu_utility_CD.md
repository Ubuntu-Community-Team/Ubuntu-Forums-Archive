---
title: "Making a bootable Ubuntu utility CD"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by FightMankaFight on 2008-02-26
Hey guys, I'm new to these forums, I hope this is the right place to put this
:/
But I am currently a college student, and one of my first group projects is to create a bootable CD with helpful utilities for Linux [preferably Ubuntu] based systems.
We were encouraged to post in forums, and use any other means necessary to accomplish said task.

I am very new to Linux, and I am currently running Ubuntu in Virtual PC on a Windows partition in my MacBook Pro. I have tried using/installing Remastersys, but I am having problems with the terminal commands.

Any help would be much appreciated, as I and my group-mates have been "Google"-ing this for quite some time now.

---

### Post by Partyboi2 on 2008-02-26
Where exactly are you getting stuck? To install you can add ```
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/
``` to your sources.list
```
gksudo gedit /etc/apt/sources.list
``` then after you have saved open a terminal and update 
sudo apt-get update
then install remastersys
```
sudo apt-get install remastersys
``` It will create a desktop icon where you can start it.

---

