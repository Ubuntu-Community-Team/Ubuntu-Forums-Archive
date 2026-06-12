---
title: "Installation didnt install all the packets"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by scope on 2005-11-25
I've just installed ubuntu from a network installation and the first part went ok, I made the partitions, it downloaded some packets, it asked me the hour and  all those things and finally the system was restarted. 

When the installation was continued, it said some other packages were going to be downloaded and installed, but after several minutes i got and error and the installation said that the packets couldnt be installed and i should fix the problem reinstaling them. 

So now i only got the terminal, neither gnome nor anyotherdesktopmanager. How could i "continue" downloading the packages the installation was going to download before crashing?? thanks

---

### Post by Xian on 2005-11-26
I really don't have a definitive answer, but since there have been no other replies this is what I would do if it was my system:

Boot the Ubuntu installation. 
When it stops at the command prompt issue this:

$ sudo apt-get update
$ sudo apt-get -f install

That will check to see if there are any outstanding deps or broken packages. When that finishes go ahead and try to install gnome.

$ sudo apt-get install ubuntu-desktop 

If you get more errors consider doing the entire installation again.

---

### Post by scope on 2005-11-26
thanks for the reply, im doing the ubuntu-desktop install now, ill tell you what happens in some minutes =P

---

### Post by Doughsay on 2005-11-27
This is the exact same problem I am having.  I searched these forums before and didnt find this post so I posted my own thread.  Still no answers though.  This is a very annoying problem...I'm going to try the suggestions above right now.

---

### Post by Doughsay on 2005-11-27
This worked great!  Thanks for the help!

---

