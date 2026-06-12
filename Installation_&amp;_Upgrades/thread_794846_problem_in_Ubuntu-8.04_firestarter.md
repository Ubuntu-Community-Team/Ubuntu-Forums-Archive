---
title: "problem in Ubuntu-8.04 firestarter"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by cheesewizz on 2008-05-15
Hello

My main objective is to share internet using firestarter
into windows client and linux

Ubuntu-8.04 firestarter was installed on my PC, I have two (2) LAN CARD


on my eth0 i setup manually my ISP address
211.xx.xx.xx -IP
255.255.255.xx -SUB
211.xx.xx.xx -Gateway
211.xx.xx.xx -DNS1
211.xx.xx.xx -DNS2

then i test the connection, it works fine i can browse website
then i install the DHCP apt-get install dhcp3-server

after i install it im going to run the GUI firestarter it can be seen in System-Administration-Firestarter

once i open it theres an error appear that i need to enable the eth1 which is my localarea lan for sharing Internet

i go to system-administration-network
i type the password for root
then i choose the eth1 and i select static IP

on my eth1 i setup manually the IP address of
192.168.1.1 -IP
255.255.255.0-SUB
192.168.1.1-gateway
192.168.1.1-DNS



once i fix it...


My internet connection is gone, very strange...hmmm i dont whats happen but if i disable the eth1 the internet will works again...



please help any idea...


thanks







when i fix it

---

### Post by longcatspace on 2008-05-15
++++++ at the bottom of this post is an answer, but i wrote all this 1st, try 192.168.0.1 as your static IP address +++++++

thankyou, very detailed description of a problem i experience in a slightly different way,

i have 2 LAN cards and i wish to share an internet connection from this ubuntu 8.04 machine with the 2 other computers in our network (XP & OSX),

i know both connections work, one brings in the internet (eth1) on which i now write this... the other connects to the network in the house (using samba) & i've transfered a file back & forth with it (eth0),

i start firestarter and it says: 

"the device eth0 is not ready.

please check your network settings and make sure your internet connection is active"

eth0 isn't the connection bringing internet in, when i swapped the cables over (so eth0 was the internet connection) the message switched also, now saying that eth1 was not ready,

i hope this is indeed the same bug and someone has a fix for it, thanks cheesewhizz and whoever helps us...

x

PS DHCP3-server does not function right on my ubuntu machine 

and of course now i look a little deeper i find an answer,

set the LAN connection to static IP address as you do, but instead of 192.168.1.1 as your IP address try 192.168.0.1,

that worked for me, now firestarter runs...

but my DHCP3-server won't run... so i can't share my internet yet, but i'm a step closer to a solution,

sorry for the long & rambling post x

---

