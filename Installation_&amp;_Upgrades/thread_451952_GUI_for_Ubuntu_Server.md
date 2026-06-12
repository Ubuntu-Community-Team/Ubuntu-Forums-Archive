---
title: "GUI for Ubuntu Server"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by klgsx on 2007-05-22
.
Hello,

Been playing around with Ubuntu for a while not. So far no problems with the Ubuntu desktop in my laptop. Life is good...BUT... now i like to get my hands dirty with Ubuntu Server.

Got an old dell HP machine with 20GB Hard Drive and 2 GB of ram. I love to install Ubuntu Server, but so far i have notice that the Ubuntu Server does not have a GUI... Everything done tru command line

So here are is my question.

After downloading and successfully installing the Ubuntu Server can I Install some kind of GUI to run some basics admin actions such as add users, create share folders for users, configure network adapter, etc?

Any suggestions is more than welcome.

Thanks.

---

### Post by dbott67 on 2007-05-22
Sure: Gnome, KDE, XFCE... anything you want.

```
sudo apt-get install ubuntu-desktop
```
```
sudo apt-get install kubuntu-desktop
```
```
sudo apt-get install xubuntu-desktop
```

---

### Post by jerrylamos on 2007-05-22
The previous post is likely best choice given the large memory you have.
Ubuntu Gnome does most everything, not as fancy.
Kubuntu KDE has lots of eye candy and lots of menus and lots of choices if you like that.
Xubuntu XFCE is smaller and faster but lacks some function like browsing your local LAN.
Here's another choice from [http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

Getting a usable home desktop
Be careful to type these exact commands (pick the appropriate set of commands for the version you're installing). Spaces are important, as is case (upper or lower).

If you're using Feisty Fawn (7.04) or Edgy Eft (6.10):
sudo apt-get update

sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic

sudo dpkg-reconfigure -phigh xserver-xorg

sudo /etc/init.d/gdm start

---

