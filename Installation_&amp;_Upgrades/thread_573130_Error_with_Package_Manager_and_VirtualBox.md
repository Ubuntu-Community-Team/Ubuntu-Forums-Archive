---
title: "Error with Package Manager and VirtualBox"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by jodoj80 on 2007-10-11
I was trying to install the virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb and now I received this error. I want to know how I can resolve this, because I can't install other package on my computer.

---

### Post by BennBuntu on 2007-10-11
not quite sure why that's happening.
I'd recommend adding the virtualbox repository

open a terminal and type

sudo gedit /etc/apt/sources.list

paste in on a line by itself

deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free

then add the key.

 following instructions here [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

This way it stays up to date by itself

Virtualbox rocks too :-)

---

### Post by forestpixie on 2007-10-11
you might need to get rid of the errors first though

look in this thread for the same problem - [http://ubuntuforums.org/showthread.php?t=573031](http://ubuntuforums.org/showthread.php?t=573031)

---

### Post by jodoj80 on 2007-10-11
Hey thanks for the link to this post. It helps me with the problem. I just have to write in the terminal ```
sudo dpkg --remove --force-remove-reinstreq virtualbox
``` thanks for your help.

---

