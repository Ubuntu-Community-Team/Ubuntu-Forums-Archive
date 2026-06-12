---
title: "cannot upgrade or install"
date: 2017-03-23
forum: Installation &amp; Upgrades
---

### Post by kritikamish99 on 2017-03-23
Hello All
I am new to this community 
Please bear with me if i am making some silly mistakes
Recently i got Dell server poweredge t630
I have installed the ubuntu 16.04 LTS server version in my system after installation it is directly going into terminal no gui
now if i want to install or upgrade through terminal it need net connection 
I have already a LAN connected to my server 
Again i am not able to connect to internet

Please help me to find out the way i can connect to internet through console and upgrade my system
I have no idea which all driver are installed by default
Please help!!!!!!!

---

### Post by Bucky Ball on 2017-03-23
Welcome. Was there a particular reason for installing the server version? That has no GUI/desktop environment.

If you have no reason for going that route, [try the desktop version]("https://www.ubuntu.com/download/desktop"). You can boot the install media and 'Try Ubuntu' from that. See if you get internet via your cable on the 'live' session prior to installing.

Good luck.

PS: All the drivers you are going to need are generally in the Ubuntu kernel already, certainly for your ethernet cable connection. Any others can generally be installed post OS install. ;)

---

### Post by kritikamish99 on 2017-03-24
Hi Bucky Ball
Thanks for reply
Actually I have Dell T630 poweredge initially i tried to install the ubuntu 16.04 desktop version , but the GUI was dead slow so we decided switch to server version.
But with server version i am not able to connect to internet and not able to download required pakages.

---

### Post by Bucky Ball on 2017-03-24
As I mention, perhaps try Xubuntu or Lubuntu which come with light GUIs, less bloat than Ubuntu and may contain the software to get your network going 'automagically'. The server version is, well, a server version. A server is not really intended to have a GUI, along with a lot of other things, which is why there is no GUI.

You don't specifically want a server so it will include stuff you don't need. Better to [go for the minimal install ]("https://help.ubuntu.com/community/Installation/MinimalCD") than the server in your case and when you reboot after install, with the cable in, install a desktop from the terminal, xfce for instance, with:

```
sudo apt install xfce4
```

You could also try Xubuntu-core or Lubuntu-core. They are also lightweight with light GUIs. 

Good luck.

PS: As for the ethernet. Have you checked with another cable? I know it may seem obvious, but if you don't know for certain that the cable works, do it. :)

---

