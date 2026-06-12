---
title: "Updating Ubuntu 5.04, need repositories"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-11-29
I have older computers where new versions of ubuntu cannot be possible to run. I have decided to use ubuntu 5.04 on these computers. I dont want to use xubuntu cause openoffice is not included. I need to update its components, can I still use the repositories posted on [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Repositories) ?

---

### Post by aysiu on 2006-11-29
I'm sorry, but why can't newer versions of Ubuntu run on your older computers? What can 5.04 do that 6.10 can't?

If you're worried about not having enough hard drive space or RAM, consider doing a server install from the Edgy Alternate CD and then adding IceWM and a few other things: ```
sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm icewm menu firefox synaptic gksu
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by textguru on 2006-11-29
can Ubuntu 6.10 run a 128MB RAM and Celeron 433MHz PC?

---

### Post by unisol on 2006-11-29
no but xubuntu 6.10 should be able to

---

### Post by aysiu on 2006-11-29
> **textguru said:**
> can Ubuntu 6.10 run a 128MB RAM and Celeron 433MHz PC?
The default Ubuntu with Gnome cannot, but the advice I gave you in the second post was to do a server install from the Alternate CD and use IceWM instead.

5.04's Gnome is no less resource-intensive than 6.10's Gnome. Do not use Gnome or KDE.

If you use IceWM, Fluxbox, or XFCE, it won't matter (in terms of speed) if you use 6.10 or 5.04... except that 6.10 will have newer software.

---

### Post by textguru on 2006-11-29
I have tried installing Ubuntu 6.10 server and install the following code:
```
sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm icewm menu firefox synaptic gksu
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

will advice you once installation is done.

---

### Post by textguru on 2006-11-29
Installation is already done. I notice that after installation, I was prompt to logon using the gui window, after that, I was prompt to a terminal window. How can I enable the taskbar so I may select the program I need like openoffice, firefox, and terminal service including browsing to network servers (samba server)?

---

### Post by aysiu on 2006-11-30
> **textguru said:**
> Installation is already done. I notice that after installation, I was prompt to logon using the gui window, after that, I was prompt to a terminal window. How can I enable the taskbar so I may select the program I need like openoffice, firefox, and terminal service including browsing to network servers (samba server)?
[This thread](http://ubuntuforums.org/showthread.php?t=171203&highlight=icewm) should help you get set up.

You can also find some hidden treasures in [this one](http://ubuntuforums.org/showthread.php?t=263710&highlight=icewm).

---

### Post by textguru on 2006-11-30
I need to install OpenOffice, Terminal client(to access VNC and RDP), and Windows Network servers. How can I install these applications?

---

### Post by aysiu on 2006-11-30
Use *aptitude* to install those.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by textguru on 2006-12-01
what is the program name for openoffice? terminal client (to access vnc & RDP)? Access network servers?

I usually use apt-get but dont know the program name (sudo apt-get install openoffice2? and so on?

---

### Post by aysiu on 2006-12-01
Try ```
apt-cache search openoffice
```

---

