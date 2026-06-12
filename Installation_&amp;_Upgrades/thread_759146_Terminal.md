---
title: "Terminal?"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by amsue on 2008-04-18
What is the "Terminal" and do I need it to download instaul everything? I can't seem to get adobie going? Also I am trying to instaul updates and they are going to be "cached locally for instaulation" ??? anyone wanna help the newb?? :confused:

---

### Post by Pumalite on 2008-04-18
Applications>Accessories>Terminal
This is the most powerful instrument in your computer.
Here you can do updates:
sudo apt-get update
sudo apt-get upgrade
You can call programs:
firefox
You can check your drives/partitions layout:
sudo fdisk -lu
You can edit a file:
gksudo gedit /etc/apt/sources.list
You can copy files:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
Here are some tutorials:
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

---

### Post by Pumalite on 2008-04-18
[http://www.icewalkers.com/Linux/Howto/Text-Terminal-HOWTO.html](http://www.icewalkers.com/Linux/Howto/Text-Terminal-HOWTO.html)

---

### Post by amsue on 2008-04-18
Thank you for all the links! I can't wait to learn all this stuff, right now its way way way way way beyond me...:KS

---

### Post by g2g591 on 2008-04-18
you can update and install stuff without the terminal using add/remove programs and synaptic, however, the terminal is a bit faster if you know the exact package name you want, (and even if you don't) . also, commandX--help usually gives you some good info on how to use commandX (commandX is a generic example , substitute apt-get and apt-cache as needed) . if more info is needed, run info commandX . after that, google is helpful

---

