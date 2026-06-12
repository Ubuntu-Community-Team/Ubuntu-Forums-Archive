---
title: "Freeze When Upgrading.."
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by NightShack on 2007-04-19
Ok so..I have 6.10 and I try to upgrage with "Update Manager" and click on "Upgrade" and then the window just freezes and says I dont have internet connection....Whats happening here??

Im using 6.10 right now

---

### Post by Big_J on 2007-04-19
Everyone is trying to upgrade. The servers are overloading...

---

### Post by DarkStarAeon on 2007-04-19
> **Big_J said:**
> Everyone is trying to upgrade. The servers are overloading...


Yeah, I wish I'd though of that before I hit the upgrade button, but it was before my first cup of coffee and I wasn't thinking. lol 
Sigh, I should have waited, this is taking forever.

---

### Post by NightShack on 2007-04-19
Argh... that sucks
Now i get this message:
Failed to fetch [http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz) 301 Moved Permanently

---

### Post by eyelessfade on 2007-04-19
Just cancel the update, and try again tomorrow. :)

---

### Post by Krist Blomme on 2007-04-21
I think I had the same problem , I followed the advise from an other forum tread
("Upgrade error message" filled by mmmpancake).

I did the following :
gksudo gedit /etc/apt/sources.list 

I commented the following :

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

after this the message is gone , 

HOWEVER , also the update button is gone in update manager , but I do not think I'm already upgraded , I didn't see any install being done .

Can someone tell me :
- how can I double check my UBUNTU version ( 6.10 <-> 7.04 )
- how can I continue the install again ?

---

### Post by DougieFresh4U on 2007-04-21
Under System>Administration>System Monitor, see what it says under System (screenshot). Then I would try in terminal **sudo apt-get update** **sudo apt-get -f install** and then **sudo dpkg --configure -a** Also is your sources list in order as all instances are feisty and not edgy or what ever version you were using?

---

### Post by Big_J on 2007-04-21
Or system-> about ubuntu

---

### Post by Krist Blomme on 2007-04-22
System>Administration>System Monitor did not give me any version info, 
System> about ubuntu gives me still 6.10

I have done te following :
in sources.list I have replaced edgy with feisty 
then i did 

sudo apt-get update
sudo apt-get autoremove
sudo apt-get -f install

this is the outcome of the install

krist@alimonta:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 967 not upgraded.
krist@alimonta:~$ 

nothing is getting upgraded , what can I do ?

---

### Post by Krist Blomme on 2007-04-23
upgrade manager finally  took over , the version is now upgraded , I'm having 7.04

---

### Post by garymc1 on 2007-04-29
still cant update, update manager just freezes when i click on the update button I am using Ubuntu 6.10 and want to upgrade to 7.04

---

### Post by DarkStarAeon on 2007-04-29
do you have a firewall setup? check the settings?

I realize that's obvious, just trying to help.

---

### Post by garymc1 on 2007-04-30
i am new to Linux i have a icon at the top for fire starter but even when i exit that it is just the same i have downloaded updates for stuff like wine and security update and other software updates using the update manager. in the update manager box when you can click on check, it checks OK because it downloads all the package info then when i click on upgrade it freezes Thanks Gary

---

