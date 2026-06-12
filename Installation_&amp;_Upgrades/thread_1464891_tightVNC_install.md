---
title: "tightVNC install"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by skynet_2000 on 2010-04-28
I need some help here please I used the Synaptic Package Manager to install the tightVNC server and viewer, but I cannot find them anywhere Anybody have any idea on this thanks

---

### Post by Rod J on 2010-04-28
I have installed xtightvncviewer here on Jaunty. It appears in the internet category of the applications menu. If you can't find it there you should be able to start it in a terminal using 'xtightvncviewer'. I don't have the server part installed so I'm not sure what the server app name will be (have a guess). :)

---

### Post by skynet_2000 on 2010-04-28
> **Rod J said:**
> I have installed xtightvncviewer here on Jaunty. It appears in the internet category of the applications menu. If you can't find it there you should be able to start it in a terminal using 'xtightvncviewer'. I don't have the server part installed so I'm not sure what the server app name will be (have a guess). :)

ok I can see a small window on the left side but is blank I want to configure the viewer..

---

### Post by 2hot6ft2 on 2010-04-28
> **skynet_2000 said:**
> ok I can see a small window on the left side but is blank I want to configure the viewer..
put the IP Address of the machine you want to connect to in the window and hit enter.

---

### Post by 2hot6ft2 on 2010-04-28
> **Rod J said:**
> I'm not sure what the server app name will be (have a guess). :)
x11vnc
You can install it with
```
sudo apt-get install x11vnc
```
and start it in a terminal on the server with
```
x11vnc
```
And yes to the starting it in a terminal using 'xtightvncviewer'

---

