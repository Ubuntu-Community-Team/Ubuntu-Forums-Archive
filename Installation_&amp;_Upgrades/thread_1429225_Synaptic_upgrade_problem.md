---
title: "Synaptic upgrade problem"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by dfpd62 on 2010-03-13
Hi Folks,

I want to upgrade from 9.04 to 9.10.
Synaptic returns the following error message,

 Failed to fetch [http://www.sourceslist.eu/repository/karmic/binary/Packages](http://www.sourceslist.eu/repository/karmic/binary/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Any help welcome.

Ta

Donald.

---

### Post by rcayea on 2010-03-13
Possibly broken packages. Try to repair packages in synaptic under the edit menu in the top left hand part of the screen.

---

### Post by dfpd62 on 2010-03-14
Tried that, and apt-get dist-upgrade, apt-get upgrade, apt-get update, dpkg --configure -a .
problem still the same, how do I update Repositories? is there a tool or do i have to do it manually? if so, where do I get the list?. 

Ta

Donald

---

### Post by rcayea on 2010-03-14
You could try this website:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)


Maybe first make note of the sources you do have and then delete your sources and then the website listed above will generate a new set for you, very easily.

---

### Post by dfpd62 on 2010-03-14
Thanks, tried that, apt-get downloaded the package list, but still won't do a "dist-upgrade"

 dd@mulberry:~$ sudo apt-get dist-upgrade
Reading package lists... Done           
Building dependency tree                
Reading state information... Done       
Calculating upgrade... Done             
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Is this command supposed to upgrade to Karmic?
if not. what should i use???

Donald

ps: I ran "apt-get update" before I ran dist-upgrade.

---

