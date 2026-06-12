---
title: "Network-Manager missing after update (Lynx 10.04LTS)"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by gansvv on 2010-08-20
Hi, I did the normal sudo apt-get update and upgrade this morning and after a restart, the network-manager is gone!
nm-applet command does not work anymore.

Can I add the LAN ethernet interface using ifconfig and connect to the net to install the network-manager again? What is the best way to solve this? Thanks.

---

### Post by gansvv on 2010-08-20
Used the 10.04.1 alternate-install disk to install "network-manager-gnome". Works now. 
(network-manager was there, but network-manager-gnome wasn't installed.)

Would be good to know why it got removed in the first place though.

---

### Post by Mr.Comix on 2010-08-21
I do not have a alternate-install CD
can I build a Network Manager icon on my panel using some command
i just deleted it by accident
Thank you :)

---

### Post by jeff17237 on 2010-10-02
I've had the exact same problem..  I have no idea why this happens but would love to know and hope they are working on it.

---

### Post by jeff17237 on 2010-10-06
For anyone in the future having this problem, use whatever you are using now to get internet, download this package to a flash drive ([http://packages.ubuntu.com/lucid/net/network-manager-gnome](http://packages.ubuntu.com/lucid/net/network-manager-gnome)), install it back onto ubuntu and you should be good to go.

NOTE: the above package is for Lucid, so if you have another distribution, find your release at packages.ubuntu.com and look for network-manager-gnome

---

### Post by jusis on 2011-01-31
thank you jeff, I installed the package to usb and copy-pasted to home folder. but from there I cannot move on. 

when I click on the same package on another working computer, software center opens to reinstall the network manager (since on this computer it is already installed).
so this is supposed to be one of the possible ways it normally gets installed on the computer I suppose.
however, when I, on the partially-upgraded computer, right click on the package and select from the menu "open with ubuntu software center" , this doesn't follow, the software center doesn't open.

also I tried it with synaptic. when I select file>add downloaded packages, the file is greyed in the opening window, hence I cannot select it for adding.

and, with the terminal, I don't know the way to install the downloaded package.

could you please help me know more to solve this?

many thanks!! :)

---

